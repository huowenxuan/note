## 页面传参

### url传参

```js
// Router.js中
<Route exact path="/detail/:id" component={Detail}/>
// Detail.js
this.props.match.params
// 跳转到 #/detail/3 得到 {id: 3}
```

### 隐式传参

```js
// 使用push
<button onClick={() => this.props.history.push({
		pathname: '/detail',
		state: { id: 3 }
})}>
// 获取
this.props.history.location.state
```

### 问号

```
let search = props.location.search // ?aaa=bbb
// 不需要判断字符串长度，直接去掉第一个字符问号；然后使用qs解码为对象
qs.decode(search.substr(1))

```

