# createRef
ref有三种创建方式

1. 字符串（官方不推荐）

    ```
    <View ref={'view'}/>
    this.refs.view
    ```

2. 回调函数

    ```
    view = null
    <View ref={ref=>this.view = ref}/>
    this.view
    ```

3. createRef，react 16.3新增，唯一可以直接调用HOC的ref创建方式
   
    ```
    view = React.createRef()
    <View ref={view}/>
   this.view.current
   ```

# setState

```
this.setState((preState, props)=>({
    counter: preState.quantity + 1;
})
// 可替代↓↓↓，避免异步情况下多次重复操作导致值被覆盖，拿到的数据不是最新的
this.setState({counter: this.state.quantity + 1})
```

# 错误处理
```
// 可以捕获子组件的错误
componentDidCatch(error, info)
```






​                      