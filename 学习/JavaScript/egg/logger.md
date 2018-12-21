---
title: logger
---

# Logger
## 分类
- **appLogger** `app.logger` 和 contextLogger `ctx.logger`
    写入到${appInfo.name}-web.log，例如 example-app-web.log，应用/请求相关日志，供应用开发者使用的日志。我们在绝大数情况下都在使用它 
    
    在ctx中尽量使用ctx.logger，可以同时输出请求方式——method、router信息

- **errorLogger** `***logger.error`
    写入到common-error.log 实际一般不会直接使用它，任何 logger 的 .error() 调用输出的日志都会重定向到这里，重点通过查看此日志定位异常

- coreLogger `ctx.coreLogger`
    写入到egg-web.log 框架内核、插件日志

- agentLogger `agent.logger`
    写入到egg-agent.log agent 进程日志，框架和使用到 agent 进程执行任务的插件会打印一些日志到这里

## 级别（从高到低）
- error
- warn
- info
- debug

## 文件级别日志
默认只会输出INFO及以上的日志到文件中，可配置

```
// config/config.${env}.js
config.logger = {
    level: 'DEBUG', // 打印所有级别日志到文件中
    level: 'NONE', // 关闭所有
}

// 生产环境打印DEBUG级别的日志可能会导致性能问题，因此默认禁止。打开DEBUG级别的日志必须要打开allowDebugAtProd（不要设置）
// config/config.prod.js
exports.logger = {
  level: 'DEBUG',
  allowDebugAtProd: true,
};
```

## 终端级别日志
默认只会输出INFO及以上的日志到文件中，可配置

```
// config/config.${env}.js
config.logger = {
    consoleLevel: 'DEBUG', // 打印所有级别日志到文件中
    consoleLevel: 'NONE', // 关闭所有
}
```

## 日志切割
prod的日志是按天来切分的，格式为`***.log.2018-09-03`，当天的日志无日期，直接是`***.logs`

dev的日志全放在一个文件中，在重新运行后会清空原日志
                      