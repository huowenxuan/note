

[TOC]

### 箭头函数和普通函数的区别

1. 箭头函数相当于匿名函数简化了函数定义
2. 箭头函数不能使用 new 命令，且没有prototype属性
   不能使用new实例化的原因：
   * 没有自己的this，无法调用call、apply
   * 没有prototype属性，而new命令在执行时需要将构造函数的prototype复制给新的对象`__proto__`
3. this指向不同
   * 普通函数this指向调用它的对象，可以通过bind，call，apply改变this的指向
   * 箭头函数this永远指向其上下文的this。通过call、apple调用时只传入了一个参数，对this无影响
4. 普通函数可通过arguments获取参数，箭头函数只能通过rest“...” 
5. 箭头函数不可以使用 yield 命令，因此箭头函数不能用作 Generator 函数。

### 对象和函数的关系

函数是对象（基本类型并不是对象，其他的所有引用类型都是对象（函数、数组、null））

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

TODO apply bind call

### new发生了什么

1. 创建空对象
2. 设置新对象的constructor属性为构造函数的名称，设置新对象的`__proto__`属性指向构造函数的prototype对象

3. 执行构造函数中年的代码，构造函数中的this指向新对象
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

function Person() {}
let p2 = _new(Person, "小花")
console.log(p2.name)  // 小花
console.log(p2 instanceof Person) // true
```

### js对象中自身声明的方法和属性与prototype声明的对象有什么差别

原型方法或属性作用于所有对象，同名以对象优先

### javascript的typeof返回哪些数据类型.

答案：string,boolean,number,undefined,function,object

### 例举3种强制类型转换和2种隐式类型转换?

答案：强制（parseInt,parseFloat,number） 隐式（==  ===）

**null，undefined的区别?**

　　null表示一个对象被定义了，但存放了空指针，转换为数值时为0。

　　undefined表示声明的变量未初始化，转换为数值时为NAN。

　　typeof(null) -- object;

　　typeof(undefined) -- undefined

### Promise

异步操作，避免回调地狱

三种状态，等待态（Pending）、执行态（Fulfilled）和拒绝态（Rejected）。一旦Promise被resolve或reject，不能再迁移至其他任何状态（即状态 immutable）

### 闭包

闭包就是能够读取其他函数内部变量的函数，即定义在函数内部的函数，且该函数作为返回值，在本质上就是将函数内部和函数外部连接起来的桥梁。最大用处

一个是前面提到的可以读取函数内部的变量，另一个就是让这些变量的值始终保持在内存中。

使用闭包的注意点

1）由于闭包会使得函数中的变量都被保存在内存中，内存消耗很大，所以不能滥用闭包，否则会造成网页的性能问题，在IE中可能导致内存泄露。解决方法是，在退出函数之前，将不使用的局部变量全部删除。

2）闭包会在父函数外部，改变父函数内部变量的值。所以，如果你把父函数当作对象（object）使用，把闭包当作它的公用方法（Public Method），把内部变量当作它的私有属性（private value），这时一定要小心，不要随便改变父函数内部变量的值。

闭包不会造成内存泄露，造成泄露的原因一般是被全局变量引用，没有及时释放

**由于闭包会携带包含它的函数的作用域，因此会比其他函数占用更多的内存。过度使用闭包可能会导致内存占用过多**

### 