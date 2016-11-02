# 得到text的高度

```javascript
<Text onLayout={(event)=>this._textOnLayout(event)} />

_textOnLayout(event){
	console.log(event.nativeEvent.layout.height,'onLayout');
}
```