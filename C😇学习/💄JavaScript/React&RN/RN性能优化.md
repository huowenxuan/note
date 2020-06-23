# 使用setNativeProps方法
setNativeProps 方法可以理解为web的直接修改dom。使用该方法修改 View 、 Text 等 RN自带的组件 ，则不会触发组件的 componentWillReceiveProps 、 shouldComponentUpdate、 componentWillUpdate 等组件生命周期中的方法。
建议频繁更新的操作，如slider、tabs切换等拖曳操作时，使用 setNativeProps 来更新属性，会获得意想不到的性能体验。

```
me.refs.tabView.setNativeProps({
	style : {
		height : 0,
		opacity : 0
	}
});

```

# shouldComponentUpdate

```
shouldComponentUpdate(nextProps, nextState) {
	return false
}
```

# 不要使用阴影效果
React Native 里面的 shadow 相关的样式，是非常耗性能的css属性。这在web上，以前android 2.0年代，也是一样耗性能的css属性之一。如果需要使用阴影效果，建议使用图片来代替反而性能更好一些。

# 设置key值
如果组件中包含通过循环插入的子元素，为了保证重新渲染UI的时候能正确显示这些子元素，每个元素都要通过一个特殊的key属性指定一个唯一值，保证React的diff效率




                      