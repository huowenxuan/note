使用symbol作属性或者方法可变为隐藏属性，不会被访问或覆盖

无法被for...in循环到

## 判断对象是否为空（判断Symbol）

正常对象都可以用`_.isEmpty()`、`JSON.stringify()`、`Object.keys()`、`Object.getOwnPropertyNames()`来判断，`Object.getOwnPropertySymbols()`只会返回以Symbol类型的key，只有通过`Reflect.ownKeys()`才能判断可能同时有正常类型和Symbol类型的对象

|                                | null  | {}                | `{a: 1}`          | `{[Symbol('a')]: 1}` | `{[Symbol('a')]: 1, a: 1}` |
| ------------------------------ | ----- | ----------------- | ----------------- | -------------------- | -------------------------- |
| _.isEmpty()                    | true  | true              | false             | true                 | false                      |
| JSON.stringify()               | null  | {}                | {"a":1}           | {}                   | {"a":1}                    |
| toString()                     | Error | "[object Object]" | "[object Object]" | "[object Object]"    | "[object Object]"          |
| Object.keys()                  | Error | []                | [ 'a' ]           | []                   | [ 'a' ]                    |
| Object.getOwnPropertyNames()   | Error | []                | [ 'a' ]           | []                   | [ 'a' ]                    |
| Object.getOwnPropertySymbols() | Error | []                | []                | [ Symbol(a) ]        | [ Symbol(a) ]              |
| Reflect.ownKeys()              | Error | []                | [ 'a' ]           | [ Symbol(a) ]        | [ 'a', Symbol(a) ]         |