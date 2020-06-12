### 基础

* 响应式编程：更新data，用户界面做出响应

* 虚拟DOM：保存在内存中的树形结构，每次自上而下渲染React组件时，都会对比这次和上次的虚拟dom，最后修改真正的dom树时只修改有差别的部分

* 首字母小写为dom元素，大写为组件元素

* props 默认情况下，props改变，会渲染所有子节点

* componentWillMount: 即使修改状态也不会引发重绘，所以直接使用componentDidMount即可

* componentWillReceiveProps(nextProps): 不管props有没有改变，只要父元素render被调用，就会触发子元素的该方法；修改state不会对该方法产生影响（否则会造成死循环）

* shouldComponentUpdate(nextProps, nextState) 

* 无状态组件：不存在state，内部状态无需变化，不需要this、bind来调用方法、没有生命周期（无法使用shouldComponentUpdate来优化），并不比有状态组件性能好、容易复用

  对于无法使用shouldComponentUpdate的问题，可使用Recompose的pure方法 `const OptimizedComponent = pure(ExpensiveComponent)`

* findDOMNode得到实际dom

* ref如果放在原生dom中，得到的就是dom节点，可调用原生的方法（例如播放、聚焦等），如果放到React组件中，得到的就是React组件的实例

* findDOMNode和ref都不可用在无状态组件，无状态组件只是方法调用，没有新建实例，而对于React组件，refs指向组件类的实例，所以可以调用它的方法

### 事件

* 如果想访问原生对象使用nativeEvent
* 必须用驼峰来写事件属性名 onClick。HTML的属性值必须是JS字符串`onclick="handleClick()"`，JSX中可以是任意类型，指针：`onClick={this.handleClick}`
* React事件是合成事件，不是原生DOM事件。在dom事件中可以通过返回false来阻止事件默认行为，但在React事件中，必须通过preventDefault来阻止默认行为
* 事件委派：React不会把事件处理函数直接绑定到真实节点，而是绑定到最外层document，使用统一的事件监听器来保存所有组件的事件监听和处理函数；当事件发生，监听器找到真正的处理函数来调用。简化了事件处理和回收机制，效率也有很大提升
* 使用原生事件：`this.refs.button.addEventListener('click', e => {...})`。监听组件之外的点击需要使用原生事件
* dom原生事件在组件卸载需要手动移除，否则可能内存泄露，合成事件不需要，React处理好了

### 表单

属性e.target: value（input、textarea、select）、checked（radio、checkbox）、selected（select下的option，一般用不到，在select上使用value属性）

事件：onChange

```
// 受控组件，通过state更新值
<input value={this.state.value} onChange={(e) => this.setState({value: e.target.value}})/>

// 非受控组件
<input ref="name" defaultValue={...}/>
// 通过ref取值
handleSubmit(e) {
	e.oreventDefault()
	const {value} = this.refs.name
}
```

受控组件可以在onChange中实时对输入进行检测、格式化。每次更新都会调用onChange，对性能有一定影响，但仍然不提倡使用非受控组件

简化多个表单元素的事件和值：

```
this.state = {
	name: '',
	age: 10
}

handleChange(name, e) {
	const {value} = e.target
	this.setState({
		[name]: value
	})
}

render() {
	const {name, age} = this.state
	return (
		<div>
			<input value={name} onChange={this.handleChange.bind(this, 'name')}/>
			<input value={age} onChange={this.handleChange.bind(this, 'age')}/>
		</div>
	)
}
```

### 样式处理

* React使用className避免命名冲突
* 行内样式使用对象，去掉'-'，改为驼峰
* 宽高等可直接设为数字，react自动添加px，lineHeight等可以直接将数字作为值的属性，不自动添加px

* classnames 可动态设置className

css两种模块化方案：

* inline style：完全使用JS来写样式，模块化能力强，但是无法使用css本身的特性，如级联、媒体查询等，伪类处理复杂，且需要框架实现，如Radium、jsxstyle、react-style

* CSS Modules：依旧使用CSS，但使用JS的模块化能力来管理样式。webpack css-loader内置

  《深入React技术栈》p66-p74

### 组件性能优化

1. 纯函数。通过拆分让方法和组件更专注，体积更小，更独立，具有复用性可可测试性

   1. 给定相同的输入，返回相同的输出
   2. 过程没有副作用。不能改变外部状态，让参数复制，Immutable、_.cloneDeep，不改变外部
   3. 没有额外的状态依赖。方法内的状态在在方法生命周期内存货，不能使用共享变量

2. PureRender（PureComponent）

   纯组件在shouldComponentUpdate对新的props和state做了一层的浅比较，来进行性能优化，深比较是很昂贵的

   优化：

   1. `<C style={{color: 'block'}}/>`这样的组件每次渲染时都是新对象。提前赋值成常量，默认值同理

      ```js
      const defaultValue = {}
      <C style={this.props.style || defaultValue/>
      ```

   2. 事件绑定。在constructor中提前bind，避免每次渲染都bind

   3. 对于子组件，不论什么时候都会重复渲染，把shouldComponentUpdate的判断放在父组件上可避免

3. Immutable

   保证旧数据不变，且避免深拷贝把所有节点都复制一遍带来的性能损耗，只修改发生变化的节点，其他节点进行共享
   
   节省内存，时间旅行。缺点是侵入性较强。容易和原生对象混淆，可约定变量名规则，例如以$$开头
   
   Immutable.is(map1, map2) 值比较，参数为Immutable.Map，直接判断hashCode，避免深度遍历，性能好
   
   ```js
   // Immutable + shouldComponentUpdate
   import React, { Component } from 'react';
   import { is } from 'immutable';
   class App extends Component {
   	shouldComponentUpdate(nextProps, nextState) {
   		const thisProps = this.props || {}; 
   		const thisState = this.state || {};
    		if (Object.keys(thisProps).length !== Object.keys(nextProps).length ||
    			Object.keys(thisState).length !== Object.keys(nextState).length) {
    			return true;
    		}
    		for (const key in nextProps) {
    			if (nextProps.hasOwnProperty(key) &&
    					!is(thisProps[key], nextProps[key])) {
    				return true;
    			}
    		}
   	 	for (const key in nextState) {
   			if (nextState.hasOwnProperty(key) &&
    					!is(thisState[key], nextState[key])) {
    				return true;
    			}
    		}
   		return false;
    	}
   }
   
   // Immutable + setState
   // React建议this.state是不可变的，所以修改前需要深拷贝，使用Immutable可解决
   handleAdd() {
     this.setState(({data}) => ({
       data: data.update('times', v => v + 1)
     }))
     // 此时times不会改变
     this.state.data.get('times')
   }
   ```
   
4. key

   子组件是数组或迭代器，必须有key，用来做虚拟dom的diff，标识当前项的唯一，设置为独一无二，不用遍历值或随机值，除非列表内容也不唯一

5. react-addons-perf 性能检测工具

   会把各组件渲染的各个阶段的时间统计出来，打印出一张表格

   ```
   Perf.start() stop()
   ```

### 动画

界面的变化可分为DOM节点/组件的增减和属性变化。React的TransitionGroup可便捷地识别出增删的组件

#### CSS动画

有更好的性能和开发效率，设计简洁，适用于简单的动画，局限性：

1. 只支持cubic-bezier（三次贝塞尔，支持ease、linear）的缓动，对缓动函数有要求则要使用JS动画
2. 只能针对特有的CSS属性，有些属性是不支持的，例如SVG中path的d属性
3. 把translate、rotate、skew等归结为transform属性，因此只能共用一个缓动函数。left、top实现的动画性能不如translateX和translateY

```
使用CSS实现的微互动：在不同状态加不同的样式和动画，比较繁琐
el {
	opacity: 1;
	&:hover {
		opacity: 0.8;
		transition: opacity .4s ease;
	}
}
```

#### CSS animation

弥补了CSS transition在控制上的不足，可以使用多关键帧动画，可设置动画的反转、暂停、次数/永久等

#### JS包装的CSS动画

使用JS包装共同的逻辑，简化动画的开发

react-smooth库来写动画，支持CSS以及各种缓动类型的JS动画，提供定制化缓动函数的插件入口

```
<Animate from={1} to={0.8} attributeName="opacity">
	// ...
</Animate>
```

#### JS动画

包含缓动函数部分和渲染部分。渲染部分直接在缓动函数中执行setState来更新动画进度，触发页面重绘

#### SVG线条动画

vivus.js利用SVG path的stroke-dasharray虚线属性和getTotalLength方法

```
简单的线条动画
el {
	stroke-dasharray: 0, 1px;
	&.active {
		stroke-dashoffset: totalLength, 0;
		transition: stroke-dasharray .4s ease;
	}
}
```

缺陷：使用JS实现，但是CSS动画是支持stroke-dasharray的；不支持虚线动画

#### React Transition

当React Transition识别到子组件的增删时候，则调用相应的生命周期函数，我们可在生命周期函数中实现动画逻辑。如果每个子组件的动效都相同，可共用一个生命周期函数，React Transition提供了childFactory，自定义封装子组件的工厂方法，为子组件加上相应的生命周期函数

React Transition生命周期：componentWillAppear、componentDidAppear、componentWillEnter、componentDidEnter、componentWillLeave、componentDidLeave。在componentWillReceiveProps触发componentWillxxx即可，didxxx在willxxx中提供一个回调函数来执行?

**React CSS Transition**

React Transition对CSS动画做了封装，CSS3就可以让状态延迟更新，让代码专注于业务，还能提高动画性能

React CSS Transition为了每个生命周期加了不同的className，可根据className的变化来实现动画

```jsx
// 例如
// sass
.example-enter {
	transform: scaleY(0);
	&.example-enter-active {
		transform: scaleY(1);
		transition: transform .4s ease;
	}
}
<ReactCSSTransitionGroup
	transitionName="example"
	transitionEnterTimeout={400}
>
	{items}
</ReactCSSTransitionGroup>


// react-smooth实现更简洁
const enter = {
	from: 'scaleY(0)',
	to: 'scaleY(1)',
	attributeName: 'transform',
	duration: 400
}

// 列表动画
<AnimateGroup enter={enter}>
	{items}
</AnimateGroup>
```

给名次发生变化的子组件设置key值，可设置为 `名次-id`

#### 缓动函数

返回当前帧动画进度的函数

缓动体验 linear < ease < spring（遵循物理规律，更自然）

```
react-smooth实现弹簧动画
<Animate from={{left: 0}} to={{left: 10}} ease="spring">...

react-motion实现
<Motion style={{x: spring(this.state.open ? 400: 0)}}>...
```

### 自动化测试

这里针对React渲染的UI层

Mocha测试执行器，Chai断言。测试框架Jest、Enzyme

#### Jest

Facebook开源，DOM操作基于JSDOM（模拟DOM），语法和断言基于Jasmine

引入react-addons-test-utils用来模拟浏览器时间和对DOM进行校验

#### Enzyme

Airbnb开源。提供类似jQuery操作DOM的语法，更灵活

#### 自动化测试

CI，GitHub或Gitlab使用Travis CI或Circle CI



《深入浅出React和Redux》p56

《深入React技术栈》p135

