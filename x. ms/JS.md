

[TOC]



### 闭包

可以访问另一个函数作用域中的变量的函数，由函数和创建该函数的环境组成。可以读取函数内部的变量，并且让变量始终保持在内存中

使用场景：作为参数被传递、作为返回值被返回、隐藏数据，不让外部改变

影响：变量会常驻内存，得不到释放内部，闭包不要乱用

```js
function fn() {
	const data = {} // 闭包中年的数据，外界无法访问
}
```

```js
// 闭包中自由变量的查找：是在函数定义的地方，向上级作用域查找，不是在执行的地方
// 闭包作为返回值
function create() {
  let a = 100
  return function() {
    console.log(a)
  }
}
let fn = create()
let a = 200
fn() // 100

// 闭包作为参数
function print(fn) {
  let a = 200
  fn()
}
let a = 100
function fn() {
  console.log(a)
}
print(fn) // 100
```

```js
// 题，点击后输出什么？
let i, a
for (i = 0; i < 10; i++) {
  a = document.createElement('a')
  a.innerHTML = i + '<br>'
  a.addEventListener('click', function (e) {
		e.preventDefault()
		console.log(i) // 每次都输出10，因为点击后才执行，i是全局变量，早已变为10
	})
  document.body.appendChild(a)
}
// 点击后输出什么?
let a
for (let i = 0; i < 10; i++) {
  a = document.createElement('a')
  a.innerHTML = i + '<br>'
  a.addEventListener('click', function (e) {
		e.preventDefault()
		console.log(i) // 依次为0-9，因为此时i是块级变量，优先从块级作用域查找
	})
  document.body.appendChild(a)
}
```



### this不同场景内的取值

关键点：this指向定义的地方，this的值是执行时才能确定的，不是定义时确定的

* 当做普通函数被调用：window/global
* 使用call，apply，bind：传入的对象
* 作为对象的方法调用：对象本身
* class中的方法：实例本身
* 箭头函数：上级作用域的this

```js
const obj = {
  wait() {
    setTimeout(function () {
      console.log(this) // window，因为调用者是setTimeout
    }, 1000);
  }
}

const obj = {
  wait() {
    setTimeout(() => {
      console.log(this) // 当前对象，因为是箭头函数
    }, 1000);
  }
}
```

### 手写bind

```js
// 标准
Function.prototype.bind2 = function () {
  // 参数解析为数组
  const args = Array.prototype.slice.call(arguments)
  // 获取bind第一个参数（要绑定的对象）
  const t = args.shift()
  // 获取执行的对象
  const self = this
  return function () {
    return self.apply(t, args)
  }
}

// 简易
Function.prototype.bind2 = function () {
  const [t, ...args] = [...arguments]
  const self = this
  return function () {
    return self.apply(t, args)
  }
}

// 检验
function fn1(a, b, c) {
  console.log('this:', this)
  console.log(a, b, c)
}
const fn2 = fn1.bind2({x: 100}, 10, 20, 30)
console.log(fn2())
```

手写call

```js
Function.prototype.call = function(ctx) {
  ctx = ctx || window
  ctx.func = this // 为了能以对象调用的形式绑定this
  const args = [...arguments].slice(1) || [] // 获取参数
  const res = ctx.func(...args)
  delete ctx.func
  return res
}
```

手写apply

```js
Function.prototype.apply = function(ctx) {
  ctx = ctx || window
  ctx.func = this // 为了能以对象调用的形式绑定this
  const res = argumensts[1] ? ctx.func(...arguments[1]) : ctx.func()
  delete ctx.func
  return res
}
```

### 异步

* 同步方法调用一旦开始，调用者必须等到方法调用返回后，才能继续后续的行为
* 异步方法调用一旦开始，方法调用就会立即返回，调用者就可以继续后续的操作。而异步方法通常会在另外一个线程中，整个过程，不会阻碍调用者的工作

JS是单线程语言，所以需要异步执行一些操作。同步会阻塞代码执行，异步不会

当主线程空闲后，开始执行异步任务的回调函数

### 事件循环机制

解决JS单线程一次只能同时执行一个任务。

同步任务直接在主线程中执行。异步任务进入事件队列中。主线程内的任务执行完毕为空，会去事件队列读取任务，堆入主线程执行，不断循环就是事件循环

异步任务分为两类：微任务和宏任务

（宏任务队列）包括setTimeout, setInterval, setImmediate,  I/O等

（微任务队列）包括 如Promise.then、process.nextTick

执行栈执行完毕时会立刻先处理所有微任务队列中的事件，然后再去宏任务队列中取出一个事件。同一次事件循环中，微任务永远在宏任务之前执行

```js
setTimeout(() => {
  console.log(1)
}, 0)
new Promise((resolve, reject) => {
  console.log(2)
  for (let i = 0; i < 10000; i++) {
    i === 9999 && resolve()
  }
  console.log(3)
}).then(() => {
  console.log(4)
})
console.log(5)

// 2 3 5 4 1
// new promise是同步，所以先输出2，3，然后顺序执行到5，promise.then和process.nextTick都是先执行，所以4，最后setTimeout，1
```

### process.nextTick() setTimeout() setImmediate()

process.nextTick()任务在所有异步任务之前，主线程的末尾执行

setTimeout() 和 setImmediate() 执行顺序不定

### 箭头函数和普通函数的区别

1. 箭头函数相当于匿名函数，简化了函数定义
2. 箭头函数不能使用 new 命令，且没有prototype属性
   不能使用new实例化的原因：
   * 没有自己的this，无法调用call、apply
   * 没有prototype属性，而new命令在执行时需要将构造函数的prototype复制给新的对象`__proto__`
3. this指向不同
   * 普通函数this指向调用它的对象，可以通过bind，call，apply改变this的指向
   * 箭头函数this永远指向其上下文的this。通过call、apple调用时只传入了一个参数，对this无影响
4. 普通函数可通过arguments获取参数，箭头函数只能通过rest“...” 
5. 箭头函数不可以使用 yield 命令，因此箭头函数不能用作 Generator 函数。

### class和function的关系

```js
class Point {
  constructor(x) {
    this.x = x;
  }
  toString() {
    return this.x;
  }
}

// 与下列方式等价
function Point(x) {
  this.x = x;
}
Point.prototype.toString = function () {
    return this.x;
}
```

### constructor

对象的constructor指向它的构造函数。所有函数（对象）最终的构造函数都指向**Function**。

### apply bind call

a、b、c。b调用才执行，a、c立即执行，a的第二个参数是array

1. 都是改变this指向，第一个参数都是this的指向对象
2. bind返回一个新的函数，调用时才会执行
3. apply和call都是立即执行，apply第二个参数是数组，代表一个个参数，call是把参数依次作为第二个第三个参数

### new发生了什么

1. 创建空对象
2. 设置新对象的constructor属性为构造函数的名称，设置新对象的`__proto__`属性指向构造函数的prototype对象

3. 执行构造函数中的代码，构造函数中的this指向新对象
4. 返回新对象（如果构造器函数有返回值且为对象，则以该对象作为返回值。若没有`return`或`return`了基本类型，则将上述的新对象作为返回值）

```js
var obj = {}
obj.__proto__ = Class.prototype
Class.call(obj)
```

### 模拟new的过程

```js
function _new(){
  // 1、创建一个新对象
  let target = {};
  let [constructor, ...args] = [...arguments];  // 第一个参数是构造函数（下面的Person）
  // 2、原型链连接
  target.__proto__ = constructor.prototype;
  // 3、将构造函数的属性和方法添加到这个新的空对象上。
  let result = constructor.apply(target, args);
  
  if(result && (typeof result == "object" || typeof result == "function")){
    // 如果构造函数返回的结果是一个对象，就返回这个对象
    return result
  }
  // 如果构造函数返回的不是一个对象或为空，就返回创建的新对象。
  return target
}

// 验证
function Person() {}
let p2 = _new(Person, "小花")
console.log(p2.name)  // 小花
console.log(p2 instanceof Person) // true
```

### js对象中自身声明的方法和属性与prototype声明的对象有什么差别

原型方法或属性作用于所有对象，同名以对象优先

### javascript的typeof返回哪些数据类型.

string, boolean, number, undefined, function, object

### 例举3种强制类型转换和2种隐式类型转换?

强制（parseInt, parseFloat, number） 隐式（==  ===）

**null，undefined的区别?**

　　null表示一个对象被定义了，但存放了空指针，转换为数值时为0。

　　undefined表示声明的变量未初始化，转换为数值时为NAN。

　　typeof(null) -- object;

　　typeof(undefined) -- undefined

### Promise

异步操作，避免回调地狱

三种状态，等待态（Pending）、执行态（Fulfilled）和拒绝态（Rejected）。一旦Promise被resolve或reject，不能再迁移至其他任何状态（即状态 immutable）

### Promise写一个axios

```javascript
new Promise((resolve, reject) => {
    const xhr = new XMLHttpRequest()
    xhr.open(method, url)
    xhr.onreadystatechange = () => {
       if (xhr.readyState === 4 && xhr.status === 200) {
            resolve(xhr.response)
        } else {
            reject(xhr.statusText)
        }
    }
    xhr.send(data)
})
```

### 手写实现数组扁平化

```js
function bp(arr){
	return arr.reduce((a,cur)=>{
		return Array.isArray(cur) ? [...a, ...bp(cur)] : [...a, cur]
	},[])
}
```

### 实现继承的方法

JS实现继承一般是复制父对象，通过call、apply等，只是形式上的模仿，本质上不是继承

```js
function Animal(){}

// 1. 原型链继承
function Cat(){}
Cat.prototype = new Animal()
Cat.prototype.xxx = xxx

// 2. 构造继承，使用 call 复制父类的实例属性给子类
function Cat() {
	Animal.call(this)
}

// 3. 实例继承
function Cat() {
	let obj = new Animal()
	obj.xxx = xxx
	return obj
}

// 4. 拷贝继承
function Cat(name){
  var animal = new Animal();
  for(var p in animal){
    Cat.prototype[p] = animal[p];
  }
  Cat.prototype.name = name || 'Tom';
}

// 5. 组合继承（原型链 + 构造）
function Cat(name){
  Animal.call(this);
  this.name = name || 'Tom';
}
Cat.prototype = new Animal();
Cat.prototype.constructor = Cat;
```

### node如何利用多个cpu

cluster模块 fork进程

### node防止程序异常退出

try/catch 捕获异常

或者监听`uncaughtException` 未捕获异常

```
process.on('uncaughtException', function (err) {
    console.log('Caught exception: ' + err);
});
```

