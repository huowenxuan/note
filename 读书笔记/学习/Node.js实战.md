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

#### 中间件koa-useragent
ctx.userAgent可返回ua信息

### egg.js基础知识
由koa扩展而来，增加了多进程支持，参考Ruby on Rails的设计哲学，以约定优先的配置（目录约定）

#### egg-core
egg能保持约定，得益于egg-core中的各种Loader，比如context_loader、file_loader

#### egg-cluster
多进程：使用cfork可多进程运行js
热重启：通过egg-development监听文件变化，变化时触发egg-cluster的reload事件进行重启

#### egg-socket.io
socket.io是Websocket协议在Node的实现，长连接