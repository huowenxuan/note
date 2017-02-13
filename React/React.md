# children

```javascript
// 遍历children
React.Children.map(this.props.children, (item, index)=> { // 或者forEach
})
//
React.Children.Only()
```

# key
如果组件中包含通过循环插入的子元素，为了保证重新渲染UI的时候能正确显示这些子元素，每个元素都要通过一个特殊的key属性指定一个唯一值，是为了内部diff的效率

