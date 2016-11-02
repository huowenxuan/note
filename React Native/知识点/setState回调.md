# setState回调

```javascript
this.setState({
	text:'text'
	},
	()=>{console.log('setState完成')}
)
```
回调里setState完成会执行（render后执行回调）