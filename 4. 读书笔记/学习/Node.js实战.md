[TOC]

# Node.js实战

## 实用

### 提示

egg支持babel是因为当前Node版本支持，想要开启import语法，运行时指定experimental-modules参数

### 测试代码覆盖率

```shell
npm run cov
# 打开HTML报告
open coverage/lcov-report/index.html
# 忽略某个文件，在文件顶部添加
/* istanbul */
```

### 工具代码

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

### 名言

* 对于个人来说，没有具体标准，最好的标准就是没有标准



## 第1章 Node.js的优势
* 一个Web应用是多门技术的综合体，而不只是一门语言或者一个技术
* 应用类型：I/O密集型、CPU密集型。常见的互联网产品瓶颈在I/O上，而非业务逻辑上，即返回给用户看的数据的读入与输出。CPU密集型是做频繁计算任务的应用，Node在这方面是短板（所以有nodejs不适合大型应用的说法）。
* 解决I/O密集型的瓶颈可以购买SSD磁盘来提升性能、使用内存型缓存来解决瓶颈，其次才是搭建或扩充数据库集群；解决CPU密集型的瓶颈只能增加CPU
* Go语言对于分布式的基础设施非常完善，特别是在Docker上（但这是操作系统级别的开发，构建Web应用更适合JS）
* Eggjs中的Egg-Cluster模块利用多进程解决了Node只能利用单核的问题

## 第2章 Egg.js框架核心原理与实现
### koa.js基础知识
非常小巧。实现了中间件模式，可对koa进行任意扩展。koa连路由、视图、数据库模型都没有，只带中间件与请求响应的一些方法，koa可以将各种服务以中间件的形式增加功能。中间件连接起来像一个洋葱圈。通过use使用中间件

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

### 全局方法

把常用的无依赖函数封装到全局是可行的，比如调试函数、帮助函数、无副作用的函数。但是把所有的依赖都加载到全局是不正确的做法，而且把大对象加入全局对象会发生内存泄露。

新建init.js，在其中添加全局方法，比如Controller

```js
const path = require('path')
const R = require('ramda')

// 检测一个对象的key是否是undefined
// 柯里化的好处是：当检查一个对象的key时，可以先传递这个对象，把返回的函数保存起来，再进行多次调用
const check = R.curry((obj, key)=>{
  if (typeof obj[key] === 'undefined') return false
  return true
})

const notInGlobal = key => !check(global)(key) 

function globalBaseInitial(baseDir) {
  const _use = dir => require(path.resolve(baseDir, dir))
  if (notInGlobal('check')) global.check = check
  
  if (notInGlobal('Controller'))
    // 封装的controller基类
    global.C = global.Controller = _use('app/controller/base')
  
  if (notInGlbal('use'))
    // use和_use将require('app/controller/home')变为use('app.controller.home')
    global.use = dir => {
      dir = dir.replace(/\./g, path.sep)
      return _use(dir)
    }
    
   if (notInGlobal('DEV'))
     global.DEV = process.env.NODE_ENV !== 'production'
}

module.exports = {
  globalBaseInitial
}
```

在app.js和agent.js中装载以上方法

```
const { globalBaseInitial } = require('./init')
globalBaseInitial(__dirname)
module.exports = app => {}
```

使用

```
// 新建app/schemas/signup/index.js
module.expotrs = {
	name: string
}
// app/controller/home
class Home extends C
...
	const r = use('app.schemas.signup')
```

### 自动路由

把相同的请求方法放在一个对象里，把URL作为key，控制器作为value

新建app/api.js

```
module.exports = ctl => ({
	post: {
		'/signup': ctl.user.signup,
		'/signin': ctl.user.signin
	}
})
```

新建app.utils.js

```js
npm i chalk -D // 控制台彩色输出

const { forEachObjIndexed } = require('ramda') // 遍历对象

/**
 *
 * prefix 前缀，类似 /api/v1
 */
function initRouterMap(prefix, maps, router) {
	forEachObjIndexed((map, mathod) => {
		forEachObjIndexed((controller, url) => {
     	router[method](prefix + url, controller)
      
	 		if (process.env.NODE_ENV && process.env.NODE_ENV !== 'production') {
				const chalk = require('chalk')
				console.log(
					`${chalk.blue('[' + method + ']')} -> ${chalk.red(prefix + url)}`
				)
			}
      
		}, map)
	}, maps)
}
```

router.js调用

```
initRouterMap('/api/v1', require('./api')(controller), router)
```

### CSRF

config.defualt.js

```
config.security = {
	csrf: {
		ignoreJSON: true, // 忽略json
		// enable: false, // 或者设置为不使用csrf
	}
}
```

### 封装app/extend/helper

```js
module.exports = {
	// 抛出跟验证错误相同的格式
	// throw可在helper中封装，controller和service都可以调用，ctx.helper.throw(400, 'code', '无效的参数')
	throw(code, field, message) {
		this.ctx.status = code
		throw [{field, message}]
	},
  // 快速生成start到end-1的数组
	range(start, end) {
    Array.from({lenth: end - start}, (_, k) => start + k)
  }
}
```

### 登录

```SH
npm i egg-passport egg-passport-local
npm i egg-jwt
```

passport封装了登录的公用组件，passport-local是本地登录的逻辑，用于验证用户名与密码，passport会从ctx上获取用户名与密码，传入我们在passport-loca的回调中供我们验证

配置 config.defualt.js

```js
const R = require('remda')
const chalk = require('chalk')
config.jwt = {
  secret: '123456',
  enable: true,
  // 注册和登录不需要jwt验证，忽略掉
  ignore(ctx) {
    const paths = ['/api/v1/signin', '/api/v1/signup']
    return R.contains(ctx.path, paths)
  }
}

exports.passportLocal = {
  usernameField: 'email',
  passwordField: 'password'
}
```

自动函数 app/util.js添加

```js
const { forEach } = require('ramda')
// 将passport生成的中间件挂载在控制器上
function mountPassportToController(keys, passport, controller) {
	if (!controller.passport) controller.passport = {}
	forEach(value => {
   // 获得中间件，第一个参数代表验证逻辑，比如local(egg-passport-local)、weibo(egg-passport-weibo)
   controller.passport[value] = passport.authenticate(value, {
     session: false,
     successRedirect: undefined, // 需要直接返回一个token，而不是成功后重定向
   })
  }, keys)
}

// 给passport添加如何验证的逻辑
function installPassport(passport, { verify }) {
  passport.verify(verify)
}
```

路由 app/router.js 添加代码

```js
const mount = require('./util').mountPassportToController
const install = require('./util').installPassport

install(app.passport, require('./passport'))
mount(['local'], app.passport, controller)
initRouterMap...
```

install中添加验证逻辑，直接导入passport，通过mount将local添加到路由上，和下面代码类似，但是抽象程度更高

```js
controller.passport = {}
controller.passport.local = app.passport.authenticate('local')
```

修改 app/api.js

```
'/signup': ctl.user.signUp,
'/signin': ctl.passport.local
```

添加passport逻辑 app/passport/index.js

使用debug模块代替dev来输出和调试，`npm i debug`

```js
const passportDebug = require('debug')('app.passport')

module.exports = {
  async verify(ctx, user) {
    // user.provider就是local、weibo等，这样就可以自动载入local.js、weibo.js
    passportDebug('use ' + user.provider)
    return require('./' + user.provider)(ctx, user)
  }
}
```

添加本地验证逻辑 app/passport/local.js

```js
const R = require('ramda')
module.exports = async (ctx, { username, password }) => {
  ...验证参数，验证用户...
  // 两种写法等价
  if (!user) ctx.throw(400, '用户名或密码错误')
  ctx.assert(user, 400, '用户名或密码错误')
  
  const token = await ctx.sign_token(user, ctx.request.body.remember_me)
  ctx.body = token
  return token
}
```

生成token app/extend/context.js

```js
async sign_token(user, remember_me) {
	return new Promise((resolve, reject) => {
		this.app.jwt.sign(
			user,
			this.app.config.jwt.secret,
			{
				expiresIn: remember_me ? '7d' : '1d'
			},
			(err, token) => {
				err && reject(err)
				resolve(token)
			}
		)
	})
}
```

### 邮件

egg-mail

### 调试

