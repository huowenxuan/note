# 硬盘满导致Docker中的Egg服务停止
前提：硬盘满导致Docker容器停止，Egg服务停止，redis可能关闭后重启

## Redis 
重启容器，启动Egg服务时，Redis报错`MISCONF Redis is configured to save RDB snapshots, but is currently not able to persist on disk. Commands that may modify the data set are disabled. Please check Redis logs for details about the error`

原因：（硬盘满导致）Redis被强制关闭导致不能持久化
修改redis配置
```
redis-cli
x.x.x.x:6379> auth password
x.x.x.x:6379> config set stop-writes-on-bgsave-error no
```

docker start xxx; 容器启动成功

## MySQL
通过接口调用MySQL后报错，`1030, 'Got error 28 from storage engine'`，得知是硬盘满了

## 硬盘
通过调用 `df -h`、`du --max-depth=1 -h`、`du -sh *`、`du -sh /root/.pm2`得知是`/root/.pm2/logs太大，占用38G，删除掉

## pm2
删除后通过`df -h`发现硬盘没发生变化，但是`du -sh *`发现log确实被删除掉了，是因为pm2仍然在使用logs，所以空间没有被释放掉，使用`pm2 stop all`关闭所有应用，空间释放掉，mysql也成功访问

## 最后
在redis-cli中执行`config set stop-stop-writes-on-bgsave-error yes`