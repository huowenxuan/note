# 自动绑定this
property initializers会自动为class中定义的方法绑定this，默认是不支持的，需要添加transform-class-properties插件

```
class Components extends React.Components {
	handleClick = () => {
	}

	render() {
		return (
			<button onClick={this.handleClick}/>
		)
	}
}
```

# 静态变量

```
class A {
    a = 1;
    
    log() {
        this.a // 1
    }
}
```

# ?.

```
a = undefined
a.b // 错误
a?.b // 不报错，等于undefined
```

