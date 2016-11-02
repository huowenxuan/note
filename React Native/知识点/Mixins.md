# Mixins
在ES5下，我们经常使用mixin来为我们的类添加一些新的方法，譬如PureRenderMixin

```javascript
var PureRenderMixin = require('react-addons-pure-render-mixin');React.createClass({  mixins: [PureRenderMixin],
render: function() {    return <div className={this.props.className}>foo</div>;  }});
```
然而现在官方已经不再打算在ES6里继续推行Mixin，他们说：Mixins Are Dead. Long Live Composition。
尽管如果要继续使用mixin，还是有一些第三方的方案可以用，譬如这个方案
不过官方推荐，对于库编写者而言，应当尽快放弃Mixin的编写方式，上文中提到Sebastian Markbage的一段代码推荐了一种新的编码方式：

```javascript
//Enhance.jsimport { Component } from "React";
export var Enhance = ComposedComponent => class extends Component {    constructor() {        this.state = { data: null };    }    componentDidMount() {        this.setState({ data: 'Hello' });    }    render() {        return <ComposedComponent {...this.props} data={this.state.data} />;    }};
//HigherOrderComponent.jsimport { Enhance } from "./Enhance";
class MyComponent {    render() {        if (!this.data) return <div>Waiting...</div>;        return <div>{this.data}</div>;    }}
export default Enhance(MyComponent); // Enhanced component
```
用一个“增强函数”，来某个类增加一些方法，并且返回一个新类，这无疑能实现mixin所实现的大部分需求。
