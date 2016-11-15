#StatusBar

##属性
* animated 修改背景色、样式、隐藏时是否有动画
* hidden 是否隐藏
####android
* backgroundColor
* translucent 是否半透明
####iOS
* barStyle
  * default light-content
* networkActivityIndicatorVisible: bool 网络活动指示器是否显示
* showHideTransition 使用hidden时是淡入淡出还是滑入滑出
  * fade slide

##其他
StatusBar.getCurrentHeight 得到当前状态栏高度
