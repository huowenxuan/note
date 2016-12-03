#ScrollView
##style
* contentContainerStyle 内部容器样式（子组件显示方式）
* horizontal: bool 子组件是否水平排列
* keyboardDismissMode: 某个子组件调出键盘后，拉ScrollView键盘是否消失
  * none
  * interactive ios-only 键盘消失的动画与手势进展交互对应，如果向上拉，不会消失
  * on-drag ios-only 手势开始时消失
* keyboardShouldPersistTaps: bool false时，点击输入框外，键盘收回，默认false
* onContentSizeChange: function 当ScrollView容器的宽高改变触发
* onScroll
* removeClippedSubviews 默认true，当为true时，不在屏幕内的view暂不处理计算来提高滑动效果，需要配合自己和子组件设置overflow: hidden来设置。不成熟，如果遇到问题，可以设置为false
* showsHorizontalScrollIndicator 水平方向滚动条
* showsVerticalScrollIndicator 垂直方向滚动条
####ios-only
* scrollEventThrottle ios-only 控制onScroll回调频率
* alwaysBounceHorizontal
* alwaysBounceVertical
* **bounces**
* automaticallyAdjustContentInsets 被放置在导航栏、分页栏、工具栏后，是否自动调整它的内容，默认true
* bouncesZoom
* contentInset {top, left, bottom, right} 从哪里开始显示
* contentOffset {x, y} 手动设置偏移值
* onScrollAnimationEnd 滑动动画结束回调
* **pagingEnabled** 分页
* **scrollEnabled** 能否滚动
* **scrollEventThrottle** 控制滑动事件触发频率（每秒触发多少次），数值越高，准确度越高
* onRefreshStart 当有这个属性时，会显示一个UIRefreshControl
####android-only
* onScrollBeginDrag 手指开始拖动
* onScrollEndDrag 手指结束拖动
* onMomentumEvents
* onMomentumScrollBegin 滚动趋势开始调用
* onMomentumScrollEnd 滚动趋势结束调用

##函数
```javascript
scrollTo({
  x,
  y,
  animated
})
```

#RefreshControl
* onRefresh 刷新时调用
* refreshing 是否显示
####ios-only
* tintColor
* title
####android-only
* colors 颜色数组，刷新时一直变色
* enabled
* progressBackgroundColor
* size
####使用
```html
<ScrollView
  refreshControl={
    <RefreshControl
      refreshing={true}
      onRefresh={()=>{}}
    />
  }
/>
```
