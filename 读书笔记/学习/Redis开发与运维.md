[TOC]

## 第1章 初识Redis
Redis是基于键值对的NoSQL数据库。还可以将内存的数据利快照和日志的形式保存到硬盘，在关机后内存的数据不会丢失

### 特性
1. 速度快
    * 所有数据放在内存中，读写性能惊人
    * C语言实现
    * 单线程，预防多线程可能产生的竞争问题
    * 源代码优雅。Redis是少有的集性能和优雅于一身的开源代码

2. 基于键值对的数据结构服务器
    值可以是string、hash、list、set、zset（有序集合），在字符串的基础上演变出了Bitmaps（位图）、HyperLogLog，后来又加入了GEO（地理位置信息）

3. 丰富的功能
    * 键过期，实现缓存
    * 发布订阅，实现消息系统
    * 事务
    * 流水线，客户端能将一批命令一次性传到Redis，较少网络开销
    * Lua脚本，利用lua创造出新的Redis命令

4. 简单稳定
    * 简单：源码少、单线程、不依赖操作系统中的类库，自己实现了相关功能
    * 稳定
    
5. 客户端语言多
    提供了简单的TCP通信协议，几乎涵盖了主流的编程语言
    
6. 持久化
    为了防止断电后内存中的数据丢失，提供了两种持久化方式：RDB、AOF，可以将内存的数据保存到硬盘中

7.  主从复制
    提供了复制功能，实现了多个数据相同的Redis副本

8. 高可用和分布式
    高可用实现Redis Sentinel，保证Redis的节点的故障发现和故障自动转移
    分布式实现Redis Clustr，提供了读写、容量的扩展
    
### 使用场景
1. 缓存
     加快数据访问速度、降低后段数据源的压力
     
2. 排行榜系统
    Redis提供了列表和有序集合数据结构，可以很方便地构建各种排行榜系统
    
3. 计数器应用
    例如播放数、浏览数，如果并发量很大对于关系型数据库的性能是一种功能挑战。Redis天然支持计数功能而且性能非常好
    
4. 社交网络
    赞/踩、粉丝、共同好友/喜好、推送、下拉刷新是社交网站的必备功能，通常访问量较大，而且关系型数据库不适合保存这种类型的数据，Redis提供的数据结构可以比较容易地实现
    
5. 消息队列系统
    消息队列系统是大型网站必备的基础组件，具有业务解耦、非实时业务削峰的功能特性。Redis提供了发布订阅和阻塞队列的功能
    
### 不适合做什么
数据分为热数据和冷数据，热数据是需要频繁更新的数据。将冷数据放在Redis是对内存的浪费，但是对于一些热数据，可以放在Redis中加速读写，减轻后端存储的负载。（例如视频网站，视频基本信息是经常更新的数据，属于热数据；用户的观看记录不一定是经常需要访问的数据，属于冷数据）

### 配置
安装好后，在目录下多了几个可执行文件，为Redis Shell

|  可执行文件  |  作用  |
| --- | --- |
|  redis-server  |  启动redis  |
|  redis-cli  |  redis命令行客户端  |
|  redis-benchmark  |  redis基准测试工具  |
|  redis-check-aof  |  redis aof持久化文件检测和修复工具  |
|  redis-check-dump  |  redis rdb 持久化文件检测和修复工具  |
|  redis-sentinel  |  启动redis sentinel  |

#### redis-server 启动Redis

```shell
redis-server // 使用默认配置来启动，不可在生产环境中使用
redis-server —port 6380 // 后面加上配置项，未设置的配置使用默认配置
redis-server /opt/redis/redis.conf // 配置文件启动，生产环境应该使用这种方式
```

#### redis-cli 命令行客户端

```
// 交互式。如果没有-h参数，默认为127.0.0.1，-p默认6370redis-cli -h {host} -p {port} 
127.0.0.1:6379> get hello

// 命令方式
redis-cli -h {host} -p {port} get hello 

// 停止redis服务：断开与客户端的连接、持久化文件生成。如果使用kill -9强制杀死redis服务，不会做持久化操作、缓冲区等资源不能被优雅关闭
redis-cli shutdown 
// 是否生成持久化文件
redis-cli shutdown save|nosave
```

## 第2章 API的理解和使用

### 命令

```shell
// 查看所有键
keys * 

// set
set hello world // 设置键hello为world
// ex 秒级过期时间
// px毫秒级过期时间
// nx 键必须不存在，才可以设置成功，用于添加
// xx 键必须存在，才可以设置成功，用于更新
set hello world ex 1 px 2 nx|xx 
setex key seconds value
setnx key value

// 批量设置
mset k1 v1 k2 v2 k3 v3
mget k1 k2 k3

// set
get key

// 键总数
dbsize 

// 向一个列表插入
rpush mylist a b c d 

// 检查键是否存在
exists hello 

// 删除键，返回值为成功删除键的值，如果键不存在，返回0
del hello 

// 设置过期时间，过期后自动删除，单位为秒
expire hello 10 

// 查看过期时间。返回整数：大于0为剩余的过期时间；-1为没设置过过期时间，-2为键不存在
ttl hello 

// 查看数据类型。不存在返回null
type hello 
// 查看内部编码：每种数据结构都有两种以上内部编码。可以改进内部编码，而对外的数据结构和命令都没影响
object encoding hello 

// 对counter作自增操作。值不是整数，返回错误；值是整数，返回自增后的结果；键不存在，按照值为0自增，返回1
incr counter 
decr key // 自减
incrby key number// 自增指定数字
decrby // 自减指定数字
incrbyfloat // 自增指定浮点数

// 追加值（可为字符串）
append key v

// 字符串长度
strlen key 

// 设置并返回原值
getset key v

// 设置指定位置的字符
setrange key offset value

// 获取部分字符
getrange key start end
```

### 内部编码

#### 字符串

1. int：8个字节的长整型
2. embstr：小于等于39个字节的字符串
3. raw：大于39个字节的字符串

Redis会根据当前值的类型和长度决定使用哪种内部编码实现

### 使用场景

#### 字符串

### 单线程
单线程处理命令，所以不会立刻被执行，所有命令都会进入一个队列，逐个执行，不会有两条命令是同时执行的

为什么单线程还能这么快
1. 纯内存
2. 非阻塞I/O。使用epoll作为I、O多路复用技术的实现
3. 避免了线程切换和竞态产生的消耗

2.2.3