[TOC]

### 变量

```js
for (var i = 0; i < 5; i++) {
    setTimeout(function(){
        console.log(i)
	})
}
console.log(i)
// 5 5 5 5 5 5 （var声明了一个全局作用域的变量，在setTimeout回调执行后，i早已变成了5）

for (let i = 0; i < 5; i++) {
    setTimeout(function(){
        console.log(i)
	})
}
console.log(i)
// 5 0 1 2 3 4 （let声明了一个块级作用域变量，在setTimeout当前环境中，i不再变化）
```

### == 和 ===

`==`先把两端变量转换成相同类型，再比较，`===`直接比较类型是否相同，再比较值

```
false == '0' // true 如果一个是字符串，一个是数值，把字符串转换成数值之后再进行比较
false === '0' // false
```

