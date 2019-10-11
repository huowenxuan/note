[TOC]

# 深入浅出Node.js
朴灵

## 第8章 构建Web应用

- *Basic认证：*请求报文头中的Authorization字段的内容为username + “:” + password，进行base64编码，如果未认证成功，返回401未授权的状态码。近乎是明文的，不推荐使用

- *CSRF：*跨站请求伪造

- *中间件：*简化和隔离从HTTP请求和业务逻辑之间的细节。类似过滤器，在进入具体的业务处理之前，先让过滤器处理。中间件的上下文就是请求对象和相应对象：req和res。当一个中间件执行完成后，调用next执行下一个中间件

- *中间件和性能：*添加中间件后，我们的业务逻辑是最后才执行的，应该让业务逻辑提早执行，尽早相应给用户，中间件的应用需要一些考究。
    1. 编写高效的中间件
        1. 使用高效的方法。可通过jsperf.com测试基准性能
        2. 缓存需要重复计算的结果
        3. 避免不必要的计算
    2. 合理利用路由，避免不必要的中间件执行

## 第9章 玩转进程

- *node多进程：*child_process模块，child_process.fork()函数供我们实现进程的复制。通过fork复制的进程都是一个独立的进程，有独立全新的V8实例，至少需要30毫秒的启动时间和10M的内存，fork进程是昂贵的。但是node通过事件驱动的方式在单线程上解决了大并发的问题，启动多个实例只是为了充分利用CPU资源，而不是为了解决并发问题

    ```js
    let fork = require('node_process').fork
    let cpus = require('os').cpus()
    for (let i = 0; i < cpus.length; i++) {
      fork('./worker.js')
    }
    ```

- *进程间通信IPC原理：*node中实现IPC原理是管道（pipe）技术，由libuv提供，在windows下由命名管道（named pipe）实现，*nix使用unix domain socket实现。表现在应用层上只有简单的message事件和send()方法

- *Cluster模块：**是child_process和net模块的组合应用。在node v0.8以前，进程必须通过child_process实现，有很多细节需要处理。Cluster用以解决多核CPU的利用率问题，提供了完善的API
    
    ```js
let cluster = require('cluster')
let numCPUs = require('os').cpus().length
// 官方示例创建子进程集群
if (cluster.isMaster) { // 判断是主线程还是工作线程
  for (let i = 0; i < numCPUs; i++) {
    cluster.fork()
  }
  cluster.on('exit', (worker, code, signal)=>{
    console.log('worker' + worker.process.pid + ' died')
  })
} else {}
// 推荐使用这个API创建子进程而不是使用fork，逻辑分明，代码可读性和可维护性好
cluster.setupMaster()
```
    
## 第10章 测试
    
- *单元测试：*包含断言、测试框架、测试用例、测试覆盖率、mock、持续集成等

- *断言assert：*检查程序在运行时是否满足期望，不满足会终止运行，出现错误信息。

    ```js
    // node自带的断言库。市面上的断言库大多都是基于assert模块进行封装和扩展的（例如should.js）
    let assert = require('assert')
    assert.equal(x, 100)
    ```
        
    * ok(): 判断结果是否为真
    * equal(): 判断实际值与期望值是否相等
    * notEqual()
    * deepEqual(): 实际值与期望值是否深度相等（对象或数组的元素是否相等）
    * notDeepEqual()
    * strictEqual()：实际值与期望值是否严格相等（===）
    * notStrictEqual()
    * throws(): 判断代码块是否抛出异常
    * doesNotThrows()
    * ifError(): 判断实际值是否为一个假值（null、undefined、0、''、false）
        
- *测试框架：*断言一旦检查失败，会抛出异常停止整个应用，对于做大规模断言检查并不友好，通常应该记录抛出的异常并继续执行，最后生成测试报告，这就是测试框架。本身不参与测试，主要用于管理测试用例和生成测试报告，提升测试用例的开发速度、可维护性
    - *测试风格：*将测试用例的不同组织方式成为测试风格，主要有TDD（测试驱动开发）和BDD（行为驱动开发）
        - 关注点不同：TDD关注所有功能是否被正确实现，每个功能都具备对应的测试用例，BDD关注整体行为是否符合预期，适合自顶向下的设计方式
        - 表达方式不同：TDD表述方式偏向于功能说明书的风格，BDD更接近于自然语言的方式
        - *mocha：*mocha为优秀的单元测试框架。TDD和BDD都支持。BDD主要采用describe和it进行组织，describe描述多层级的结构，具体到测试用例时，用it。TDD主要采用suite和test，suite实现多层级描述，测试用例用test
    
- *测试覆盖率：*blanket模块

- *mock：*模拟异常，伪造某个方法来抛出错误触发异常。同时为了保证该测试用例不影响其余应用，需要在执行完后还原它，mocha的before()和after()钩子函数就派上了用场。mock的过程使用muk模块：在before/beforeEach中`muk(fs, 'readFileSync', ()=>(throw new Error('mock readfilesync error')))`模拟fs.readFileSync方法抛出错误，在after/afterEach中`muk.restore()`恢复。
    需要注意的是：对于异步方法的模拟，需要小心将异步模拟为同步
    
    ```js
    // 错误
    fs.readFile = (_, _, callback)=>{
        callback(new Error('mock readFile error'))
    }
    // 正确
    fs.readFile = (_, _, callback)=>{
        // 使得回调方法能异步执行
        process.nextTick(()=>{
            callback(new Error('mock readFile error'))
        })
    }
    ```

- *私有方法的测试：*只有挂载在exports或module.exports的变量才能被外部引入。可以使用rewire模块实现对私有方法的访问，rewire原理是在它引入文件时，对原始文件进行了修改，增加了__set__()和__get__()方法，利用闭包，在eval()执行时实现了对模块内部局部变量的访问，再将局部变量导出给测试用例
    
    ```js
    // lib.js
    let limit = n => n
    // test
    it('limit should return success', ()=>{
        let lib = rewire('./lib')
        let limit = lib.__get__('limit')
        limit(10).should.be.equal(10)
    })
    ```
    
- *性能测试：*负载测试、压力测试、基准测试

- *基准测试：*以相同的时间执行方法，根据执行的时间判断性能。benchmark模块

- *压力测试：*对网络接口进行压力测试以判断网络接口的性能。常用的工具为ab、siege、http_load

- *QPS/RPS（Requests per second 每秒查询率）：*例如页面每天访问量PV为100万，主要访问量集中在10小时以内，那么QPS=PV/10h=1,000,000/10/60/60≈27.7，即服务器需要每秒处理27.7个请求才能胜任业务量
                      