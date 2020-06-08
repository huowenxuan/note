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

TODO

《深入浅出React和Redux》p56

《深入React技术栈》p64

