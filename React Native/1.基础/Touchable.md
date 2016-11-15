##Components
* TouchableNativeFeedback：android only，提供Android原生视图的视觉效果

* TouchableNativeWithoutFeedback：触摸没有任何视觉效果

* TouchableOpacity：触摸时组件变成半透明
  * activeOpacity：触摸时的透明度0-1，默认0.2

* TouchableHighlight：触摸时变暗，有时有bug：按下后旁边空白地方可能也会变暗，解决办法是在旁边加一个view
  * activeOpacity：默认0.8
  * underlayColor: 下层颜色

##Function
* onPress 手指离开后触发
* onPressIn 手指接触后delayPressIn毫秒后出发
* onPressOut
* onLongPress 长按
* delayLongPress 按了多少ms后，onLongPress被激活，默认0
* delayPressIn 按了多少ms后，onPressIn被激活，默认0
* delayPressOut
* pressRetentionOffset 当手指离开组件多远后，就变成了不被触摸的状态，再进来，再变成触摸状态
  * top left right bottom
