# Node.js实战

## 第1章 Node.js的优势
* 一个Web应用是多门技术的综合体，而不只是一门语言或者一个技术
* 应用类型：I/O密集型、CPU密集型。常见的互联网产品瓶颈在I/O上，而非业务逻辑上，即返回给用户看的数据的读入与输出。CPU密集型是做频繁计算任务的应用，Node在这方面是短板。
* 解决I/O密集型的瓶颈可以购买SSD磁盘来提升性能、使用内存型缓存来解决瓶颈，其次才是搭建或扩充数据库集群；解决CPU密集型的瓶颈只能增加CPU
* Go语言对于分布式的基础设施非常完善，特别是在Docker上（但这是操作系统级别的开发，构建Web应用更适合JS）
* Eggjs中的Egg-Cluster模块利用多进程解决了Node只能利用单核的问题

## 第2章 Egg.js框架核心原理与实现
### koa.js基础知识
实现了中间件模式，可以对koa进行任意扩展，只带中间件与请求响应的一些方法，甚至连路由、视图、数据库模型都没有，koa可以将各种服务以中间件的形式增加功能。中间件连接起来像一个洋葱圈

### egg.js基础知识
由koa扩展而来，增加了多进程支持，参考Ruby on Rails的设计哲学，以约定优先的配置（目录约定）

#### 中间件koa-useragent
ctx.userAgent可返回ua信息

#### 插件egg-core
egg能保持约定，得益于egg-core中的各种Loader，比如context_loader、file_loader

#### 插件egg-cluster
多进程：使用cfork可多进程运行js
热重启：通过egg-development监听文件变化，变化时触发egg-cluster的reload事件进行重启

#### 插件egg-socket.io
socket.io是Websocket协议在Node的实现，长连接

默认配置：

```js
config.io = {
    init: {}, // 初始化选项
    namespace: { // 命名空间，可理解为路由的url
        '/': {
            connectMiddleware: ['auth'], // 连接时的中间件：经过 / 时要通过auth中间件
            packetMiddleware: ['filter'] // 通信时（发包）的中间件：发消息时通过filter中间件
        },
         '/chat': {
            connectMiddleware: ['auth'], 
            packetMiddleware: [] 
        }
    },
    redis: { // 如果服务器是集群的，可能需要redis来实现同步数据
        host: '',
        port: 6379
    }
}

// auth中间件：当发生连接时就进入auth中间件
module.exports = ()=> {
    return async (ctx, next) => {
        const say = await ctx.service.user.say()
        // 向客户端发送消息，客户端会被socket.on('res')事件接收
        ctx.socket.emit('res', 'auth!' + say) 
        await next()
        console.log('disconnect!')
    }
}

// filter中间件
module.exports = () => {
    return async (ctx, next) => {
        console.log(ctx.packet) // 输出['chat', 'hello']
        const say = ...
        ctx.socket.emit('res', 'packet!' + say) // 向客户端发送
        await next()
        console.log('packet response!')
    }
}

// 路由
module.exports = app => {
    // of说明在 / 路径下
    // app.io.of('/')
    app.io.route('chat', app.io.controller.chat.index)
    // app.io.of('/chat')
    app.io.of('/chat').route('chat', app.io.controller.chat.index)
}

// app.io.controller.chat.js
class ChatController extends Controller {
     async index() {
        const message = this.ctx.args[0]  // 获取到hello
        console.log('chat: ', message + ': ' + process.pid) // pid 进程号
        const say = ...
        this.ctx.socket.emit('res', say)
        // 执行完回到filter中间件的next()后，输出packet response!
    }
}

```

```js
客户端代码
client.js
// 通过socket.io-client与7001建立WebSocket连接
const socket = require('socket.io-client')('http://127.0.0.1:7001')

// 建立连接后会触发connect
socket.on('connect', ()=>{
    // 第一个参数chat表示路由的route('chat')，当执行emit时，会触发后端app/io/controller/chat.js中的index方法，有中间件则先进入中间件
    socket.emit('chat', 'hello')
})
socket.on('res', msg=>{
    console.log('res from server: ', msg)
})
```

### 制作插件

```shell
# 初始化插件模板
egg-init --type=plugin egg-xxx
cd egg-xxx
yarn
```

## 第3章 构建后端API服务
### 使用Sequelize构建ORM

执行 `sequelize model:generate —name User`，会分别在model和migration创建一个文件

```
// 配置 package.json scripts
“m:new”: “sequelize migration:create”,// TODO migration:create和model:generate的区别
“m:up”: “sequelize db:migrate”,
“m:down”: “sequelize db:migrate:undo”
```

```
// 配置.sequelizerc
module.exports = {
    config: path.resolve(‘config’, ‘config.json’),
   ‘models-path’: path.resolve(‘app’, ‘model’),
   ‘seeders-path’: path.resolve(‘app’, ‘seeder’),
   ‘migrations-path’: path.resolve(‘app’, ‘migration’),
}
```

app/migration/ 存放数据库迁移文件
app/seeder/ 存放如何生成假数据的文件
app/model/ 表中字段如何映射到JS对象的逻辑

`sequelize db:migrate -debug`：当语法错误时，debug选项可获得详细错误
`sequelize db:migrate`：同步到数据库

#### 创建假数据

`sequelize seed:generate —name create_user`: 会在seeder目录下新建一个js文件，和迁移文件结构相同

```
const utils = require(‘utility’) // 是Egg依赖的
“up”: ()=>{
    return queryInterface.bulkInsert(‘Users’,[{
        email: ‘xxx@xx.xx’,
        password: utils.md5(‘00000’),
        username: ‘xxx’,
        avatar: ‘xxx’,
        ...
    }])
}
“down”: ()=>{
    queryInterface.bulkDelete(‘Users’)
}
```

### 注册服务
app/model/xx.js中 beforeCreate等生命周期方法支持异步

```
ModelA.beforeCreate((instance,options)=>{
    instance.code = await generatorCode();
})
```

#### User模型

## 实用

## Egg
### 使用Sequelize构建ORM

执行 `sequelize model:generate —name User`，会分别在model和migration创建一个文件

```
// 配置 package.json scripts
“m:new”: “sequelize migration:create”,// TODO migration:create和model:generate的区别
“m:up”: “sequelize db:migrate”,
“m:down”: “sequelize db:migrate:undo”
```

```
// 配置.sequelizerc
module.exports = {
    config: path.resolve(‘config’, ‘config.json’),
   ‘models-path’: path.resolve(‘app’, ‘model’),
   ‘seeders-path’: path.resolve(‘app’, ‘seeder’),
   ‘migrations-path’: path.resolve(‘app’, ‘migration’),
}
```

app/migration/ 存放数据库迁移文件
app/seeder/ 存放如何生成假数据的文件
app/model/ 表中字段如何映射到JS对象的逻辑

`sequelize db:migrate -debug`：当语法错误时，debug选项可获得详细错误
`sequelize db:migrate`：同步到数据库

#### 创建假数据

`sequelize seed:generate —name create_user`: 会在seeder目录下新建一个js文件，和迁移文件结构相同

```
const utils = require(‘utility’) // 是Egg依赖的
“up”: ()=>{
    return queryInterface.bulkInsert(‘Users’,[{
        email: ‘xxx@xx.xx’,
        password: utils.md5(‘00000’),
        username: ‘xxx’,
        avatar: ‘xxx’,
        ...
    }])
}
“down”: ()=>{
    queryInterface.bulkDelete(‘Users’)
}
```

### 注册服务
app/model/xx.js中 beforeCreate等生命周期方法支持异步

```
ModelA.beforeCreate((instance,options)=>{
    instance.code = await generatorCode();
})
```


## 工具代码

```
getIp(ctx) {
    if (ctx.app.config.proxy && ctx.request.ips) {
        return ctx.request.ips
    }
    return ctx.request.ip || '
}

const {forEachObjIndexed} = require(‘ramda’); forEachObjIndexed(a,b=>{})  // 可遍历对象

process.env.NODE_ENV // 判断环境 
```
