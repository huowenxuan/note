# 创建不可变数组、对象

```
let oldList = [1, 2]
// concat增，slice删，filter过滤，都是创建新的数组
// 不能使用push、pop、shift、unshift、splice，都是在原数组进行修改
let newList = oldlist.concat('3) 
// 或者
let newList = [...oldList, 3]

let oldObj = {a: 1}
let newObj = Object.assign({}, oldObj, {b: 2})
// 或者
let newObj = {...oldObj, b: 2}
```



                      