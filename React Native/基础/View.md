##属性
* removeClippedSubviews: 用于性能优化，当有子组件不在屏幕显示范围内时，设置为true可以释放它们以优化性能，想使它生效，必须设置组件和子组件的overflow为hidden
* pointerEvents: 触摸事件响应方式
  * none 不响应触摸，本组件和子组件的触摸都交给父组件来响应
  * box-none 本组件的子组件可以响应触摸，本组件不响应触摸，交给父组件响应
  * box-only 本组件以及子组件的触摸都交给本组件来响应
  * auto 默认，触摸谁谁管

##函数
* onLayout: 当组件大小或位置发生变化调用onLayout回调，可以用来监测设备放置状态
  ```javascript
  onLayout={(event)=>{
    let {x, y, width, height} = event.nativeEvent.layout
    }}
    ```
