
```javascript
// 得到屏幕宽高（包括状态栏），但是永远都是刚启动时的宽高，如果手机旋转，得到的数值是错误的，只能通过onLayout来获取
let {width, height} = Dimensions.get('window')
```
