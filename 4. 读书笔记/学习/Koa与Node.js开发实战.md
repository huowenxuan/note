[TOC]

**Koa与Node.js开发实战**

# 第1章 Node.js入门

> 基于Chrome v8引擎的JS运行时环境

JS运行时：一个能够执行JS语句的运行环境，（把底层的操作系统和体系结构的特点抽象出来，承担了解释与编译、堆管理、垃圾回收、内存分配、安全机制等功能）。提供了一系列以往由处理器和操作系统才能提供的功能，使得开发者能够彻底脱离底层指令，专注业务逻辑开发

Node.js使JS突破了浏览器的限制。Chrome v8引擎是一个高性能的JS解释引擎

事件驱动、非阻塞式I/O，轻量高效

# 第2章 遇见Koa

Express 4之前主要基于connect，封装了大量便利的功能：路由、视图处理、错误处理等，4之后不再依赖connect，中间件也作为单独模块安装。主要使用ES5语法，异步通过回调处理

Koa1使用ES6的Generator函数+yield语句+Promise，Koa2使用ES7的async/await+Promise处理

Koa不在内核中绑定任何中间件，仅提供了一个轻量的函数库，所有功能都需要引用第三方中间件实现，可以使框架更加优雅、轻量，也能让开发者根据项目定制中间件

```js
const koa = require('koa')
const app = new Koa();
app.use(async ctx => {
  await func()
  ctx.body = 'hello'
})
app.listen(3000)
```

## Context对象

一次对话的上下文，每个请求都创建一个Context，简写为ctx，在中间件中作为参数，包含Request和Response，常用属性context.app、context.cookies、context.state、context.throw，也可以自定义属性供全局使用

ctx.request 请求对象，包含method、url、query、path...

ctx.response 响应对象，可设置type、body、status、redirect(url)

ctx.state 通过中间件传递信息和前端视图，ctx.state.user = xxx，可被另一个中间件读取

ctx.throw(500)

## 中间件

通过app.use()加载中间件，中间件函数带有ctx和next参数

```js
const logger = async function(ctx, next) {
  console.log(ctx.method, ctx.host + ctx.url)
  await next()
}
app.use(logger)

// koa-compose可将多个中间件组合，便于重用或导出
const all = compose([middleware1, middleware2])
app.use(all)
```

中间件自下而上先进后出，依次执行，洋葱模型

### koa-bodyparser

koa没有封装获取post的body方法，需要解析ctx中原生node请求对象的req，`ctx.req.on('data', data=>postdata += data)`，使用该中间件可直接从`ctx.request.body`中获取

### koa-router

koa原生只能通过ctx.method判断请求方法，ctx.url判断路径，koa-router可直接匹配路由`router.get('/', ()=>{}).post(...).del(...).put(...)`

### koa-static和koa-views

前者加载静态资源，可为页面请求加载CSS、JS等静态资源，后者加载HTML

# 第3章 路由

# 第4章 HTTP

# 第5章 构建Koa Web应用

```
controller/
service/
public/
views/
app.js
router.js
```

# 第6章 数据库

## Sequelize for MySQL

## Mongoose for Mongodb

定义schema

类型：String、Number、Date、Buffer、Boolean、Mixed(混合类型，可存储多种类型)、ObjectId、Array、Decima 128(报精度数值)

约束：required是否必须、default默认值、select（查询时是否默认输出该字段）、get（定义getter，可通过它定义计算字段）、set（定义setter，写入时预处理）、alias（别名，配合set、get一起用，定义一个虚拟字段）、max min（Number类型可设置）、index（是否开启索引，可对该字段的查询进行优化）

 ```js
const categorySchema = new mongoose.Schema({
  name: String,
  createdAt: {
    type: Date,
    default: Date.now
  }
})
const Category = mongoose.model('Category', categorySchema)

const category = new Category({
  name: 'test'
})
// 保存对象到数据库
category.save(err=>{})
// 直接通过模型新增
Category.create({
  name: 'test2'
}, (err, category)=>{})
// 查询
Category.find({
  name: 'test'
}, (err, res)=>{})
// 支持Promise
Category.find({name: 'test'})
	.then
	.catch
Category.where('createdAt') // where指定字段查询
	.lt(new Date())           
	.select('name, createdAt')// 指定输出的字段
	.sort({createdAt: 1})    
	.limit(10)
	.exxec((err, res)=>{})    // 执行查询
// 删除
Category.remove({
  name: 'test'
}).then()
// 更新
Category.update({
  name: 'test'
}, {
  name: 'test2'
}).then()
 ```

## node_redis for Redis

yarn add redis

# 第7章 单元测试

Chai 断言库

Mocha 测试框架，配合断言代码来判断是否符合预期效果

SuperTest 测试Web请求

Nock 模拟服务器响应，覆盖node的http.request方法，伪造结果

Nyc 测试覆盖率

# 第7章 优化与部署

### log4js 日志

7个日志级别，支持日志文件切割

```
// 记录每个请求
ctx.logger.info(JSON.stringify({
	url,
	query,
	headers,
	ua: ctx.userAgent
	timespan: Date.now()
}))
```



## 错误处理

```
app.on("error", (err, ctx)=>{
 	if (ctx && !ctx.headerSent && ctx.status < 500) {
 		ctx.status = 500
 	} 
 	if (ctx && ctx.log && ctx.log.error) {
 		if (!ctx.state.logged) {
			ctx.log.error(err.stack)
		}
 	}
})
```

## 服务监控

通过process对象获取服务器资源信息

```
process.cpuUsage() // cpu时间
process.hrtime() // 更高精度的时间
process.memoryUsage() // 内存信息
```

yarn add pidusage 获取进程的CPU使用情况

```
pidusage(process.pid, (err, status)=>{})
```

ELK 日志分析系统 Elasticsearch（为日志做索引，查询）+ Logstash（处理日志的搜索分析过滤） + Kibana（Web界面）

Keymetrics 监控云服务 PM2提供

# 第9章 云相册功能介绍和准备工作

# 第10章 云相册服务开发

小程序登录（原生）

扫码登录（随机码+过期+HTTP轮询）

# 第11章 云相册小程序开发

# 第12章 云相册后台管理系统

# 第13章 云相册服务器部署

## mongo

配置文件在 /etc/mongod.conf

```
systemctl start mongod.service  // 启动
systemctl restart mongod.service  // 启动
systemctl enable mongod.service // 自启动
```

## Nginx

使用OpenResty，基于Nginx和Lua的Web平台，CentOS使用yum安装

```
nginx -t // 查看配置地址
// 开始修改配置文件
// 去掉错误日志配置的注释
mkdir /logs 

listen 80 default_server
listen [::]:80 default_server

// 重启
openersty -s reload
```

强制HTTPS跳转

```
server {
	listen 80;
	server_name: admin.xxx.cn;
	return 301 https://$server_name$request_uri;
}
server {
	listen 443 ssl http2;
	...
}
```

添加WWW跳转 xxx.com跳转到www.xxx.com

```
server {
	listen 80;
	...
	return 301 https://www.$server_name$request_uri;
}
```

