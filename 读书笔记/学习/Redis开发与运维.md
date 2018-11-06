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

### 单线程
单线程处理命令，所以不会立刻被执行，所有命令都会进入一个队列，逐个执行，不会有两条命令是同时执行的

为什么单线程还能这么快
1. 纯内存
2. 非阻塞I/O。使用epoll作为I、O多路复用技术的实现
3. 避免了线程切换和竞态产生的消耗

### 字符串
**命令**

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

**内部编码**
1. int：8个字节的长整型
2. embstr：小于等于39个字节的字符串
3. raw：大于39个字节的字符串
Redis会根据当前值的类型和长度决定使用哪种内部编码实现

**使用场景**
1. 缓存功能
    Redis作为缓存层，MySQL作为存储层。大部分请求都是从Redis中获取，加速读写、降低后端压力。先从redis获取信息，如果没有，就从mysql获取，然后存储到redis中，并设置过期时间

2. 计数
      可实现快速计数、查询缓存的功能，**同时数据可以异步地落地到其他数据源**。（redis可以很方便地自增）
      
3. 共享session
    分布式Web可将用户session保存到Redis中，而不是保存到各自的服务器，造成用户经常需要登录
    
4. 限速
    设置过期时间来限制某些接口不能被频繁访问，例如短信，例如限制一个IP不能在一秒钟之内访问超过n次（一秒钟之内自增数是否超过n）

### 哈希
> 在Redis中，哈希指值本身又是一个键值对，如value={{field1, value1}, ...{fieldN, valueN}}

**命令**

```shell
// 设置值，成功返回1，失败返回0
hset user:1 name tom 
hsetnx
// 批量设置
hmset user:2 name mike age 12 ...

// 获取
hget user:1 name
// 批量获取
hmget user:1 name age city ...

// 删除
hdel user:1 name

// 计算哈希中，field的个数
hlen user:1

// 判断field是否存在，存在返回1，不存在返回0
hexists user:1 name

// 获取所有field的key
hkeys user:1
// 获取所有field的value
hvals user:1
// 获取所有的key+value
hgetall user:1

// 自增
hincrby user:1 age
hincrbyfloat user:1 age

// 计算value的字符串长度
hstrlen user:1 name
```

**内部编码**
1. ziplist(压缩列表)：元素个数小于hash-max-ziplist-entries配置（默认512）、同时所有值都小于hash-max-ziplist-value配置（默认64字节）时，使用ziplist实现。ziplist使用更加紧凑的结构实现多个元素的连续从存储，节省内存
2. hashtable(哈希表)：当无法满足ziplist时使用，因为此时ziplist读写效率会下降，hashtable读写时间复杂度为O(1)

使用场景
记录map时，使用hgetAll来获取，hmset来设置

### 列表
> 可在列表两端push和pop，可指定范围内的元素列表、获取指定索引下表的元素等，比较灵活。一个列表最多可存储2<sup>32</sup>-1个元素。有序、可重复

**命令**

```shell
// 从右边插入
rpush key value [value...]
rpush listkey a b c
// 从左边插入
lpush key value ...
// 向某个元素前或后插入元素：找到等于pivot的元素，在其前/后插入新元素value
linsert key before|after pivot value


// 获取指定范围内的元素列表。从左到右为0到N-1，从坐到左是-1到-N。end中包含自身
lrange key start end
// 从左到右获取列表的所有元素
lrange listkey 0 -1

// 获取指定索引下标的元素
lindex key index
// 获取最后一个元素
lindex key -1

// 长度
llen key

// 从列表左侧/右侧弹出元素
lpop key
rpop key

// 删除指定元素。找到等于value的元素进行删除，count>0从左到右删除最多count个元素，count<0从右到左删除最多-count个元素，count=0删除所有
lrem key count value

// 按照索引范围修剪列表
ltrim key start end
// 只会保留第二个到第四个元素
ltrim listkey 1 3

// 修改
lset key index newValue 

// 阻塞操作
// 阻塞式弹出。timeout阻塞时间，单位秒。
blpop key ... timeout
brpop key ... timeout
// 1）列表为空：timeout=3客户端等3秒后返回，如果timeout=0，那么客户端一直阻塞下去。如果此期间添加了数据，客户端立即返回
// 2）列表不为空：客户端立即返回
brpopp listkey 3
```

**内部编码**

* ziplist（压缩列表）：当元素个数小于list-max-ziplist-entries（默认512个），同时每个值都小于list-max-ziplist-value（默认64字节）
* linkedlist（链表）：否则使用这种内部实现

**使用场景**
1. 消息队列：使用lpush+brpop命令组合实现阻塞队列，生产者客户端使用lrpush从列表左侧插入元素，多个消费者客户端使用brpop阻塞式“抢”列表尾部的元素
2. 文章列表：不仅有序，而且支持按索引范围获取元素

* lpush + lpop = Stack（栈）
* lpush + rpop = Queue（队列）
* lpush + ltrim = Capped Collection（有限集合）
* lpush + brpop = Message Queue（消息队列）


### 集合
用来保存多个字符串元素，但和列表类型不同的是，不允许重复，且无序，不能通过索引获取元素

**命令**

```
sadd myset a b c
srem myset a

// 计算元素个数
scard key
// 判断是否在集合中，返回0或1
sismember key a
// 随机从集合返回n个元素，不写默认1
srandmember key n
// 随机弹出元素
spop key
// 获取所有元素
smembers key

// 多个集合的交集
sinter key1 key2
// 并集
suinon key1 key2
// 差集
sdiff key1 key2
// 将交集、并集、差集的集合保存在一个key中
sinterstore destination key key1 key2
suinonstore destination key key1 key2
sdiffstore destination key key1 key2
```

**编码**
- intset（整数集合）
- hashtable（哈希表）

**使用场景**
标签。可使用sinter计算用户共同感兴趣的标签
抽奖。生成随机数

### 有序集合
保留了集合不能有重复的特性，但可排序，它给每个元素设置一个分数（score）最为排序的依据（元素不能排序，但是score可重复）

**命令**
集合内

```
// 添加。有四个参数：nx：member必须不存在才可以设置成功，用于添加；xx：member必须存在，才能设置成功，用于更新。ch：返回此次操作后，有序集合和分数发生变化的个数。incr：对score做增加，相当于zincrby。有序集合相比集合提供了排序字段，但是添加效率降低了
zadd key score member [sorce member...]

// 计算成员个数
zcard key
// 计算成员的排名
zrank key member // 分数从高到低
zrevrank key member // 分数从低到高

// 删除成员
zrem key member

// 增加成员的分数
zincrby key increment member
zincrby key 9 tom // 给tom增加了9分

// 返回指定排名范围的成员，加上withscores参数，会同时返回分数
zrange key start end [withscores]
zrevrange key start end [withscores]

// 返回指定分数范围的成员。limit offset count选项可限制输出的起始位置和个数。min和max支持开区间（小括号）和闭区间（中括号），-inf和+inf分别代表无限小和无限大
zrangebyscore key min max [withscores] [limit offset count]
zrevrangebyscore 
zrangebyscore key （200 +inf 

// 返回指定分数范围成员个数
zcount key min max

// 删除指定排名内的生序元素
zremrangebyrank key start end
// 删除指定分数范围的成员
zremrangebyscore key min max
```

集合间的操作

```
// 交集，destination：计算结果保存到这个键，numkeys：需要做交集计算的键的个数，key...：需要做交集计算的键，weights 每个键的权重，每个member都以自己的分数乘以这个权重，默认为1
zinterstore destination numkeys key [key...] [weights weight [weight...]]
// 并集
zunionstore
```

**编码方式**
- ziplist
- skiplist
- hashtable

**使用场景**
排行榜系统（点赞排行榜等）

### 键管理
#### 单个键管理

```
// 键重命名，如果已具有newkey，之前的数据会被覆盖。重命名期间会指定del命令删除旧的键，如果值比较大，可能会阻塞Redis
rename key newkey
// 只有当newkey不存在时才可以重命名
renamenx key newkey

// 随机返回一个键
randomkey
```

**键过期**

**对于字符串类型的键，执行set命令会去掉过期时间**，在redis源码中，set 命令最后执行了删除过期时间

Redis不支持二级数据结构内部元素的过期

```
// expire key seconds // seconds秒后过期。如果键不存在返回0，如果过期时间为负数，键会立即删除
expireat key timestamp // 秒级时间戳之后过期
pexpire key milliseconds // 毫秒后过期
ttl key // 大于0的整数为剩余过期时间；-1键没有设置过期时间，-2键不存在（已过期）
pttl key // 剩余过期时间，精度更高，可达到毫秒级别
persist key // 将键的过期时间清除
```

**迁移键**
把数据从一个Redis迁移到另一个Redis，建议使用merge

```
// 把指定的键从源数据库移动到目标数据库中。redis内部可以有多个数据库，彼此在数据上互相隔离。多数据库功能不建议在生成环境使用
move key db 

// dump+restore
// 在源Redis执行dump
dump key
// 目标Redis执行restore。ttl表示过期时间
restore key ttl value

/*
 * merge：实际上就是将dump、restore、del组合，简化了流程，具有原子性，支持多个键的迁移
 * key|"" 如果只迁移一个键，写要迁移的键，如果要迁移多个，设为""，要迁移的键通过keys指定
 * timeout 迁移的超时时间（毫秒）
 * [copy] 如果添加此选项，迁移后不删除源键
 * [replace] 如果添加此选项，不管目标是否存在该键都会正常迁移进行数据覆盖
 * keys 迁移多个键 例: keys key1 key2 key3
 */ 
merge host port key|"" destination-db timeout [copy] [replace] keys
merge 127.0.0.1 6380 hello 0 1000
```

**遍历键**

```
// keys通配符匹配，如果包含了大量的键，可能造成阻塞，不要在生产环境使用
keys *

/* 
 * 渐进式遍历，避免了keys的阻塞。但是在scan的过程中有键的变化，那么新增的键可能会没有遍历到，或遍历出重复的键等情况
 * cursor 必须参数，游标，每次遍历从0开始，scan完都会返回当前的游标值，直到游标为0，遍历完成
 * pattern 匹配
 * count 每次要遍历的键个数，默认10
 */
scan cursor [match pattern] [count number]

```

#### 数据库管理
默认redis有16个数据从，index为0-15。每个数据库之间没有任何关联。但是Redis已经逐渐弱化这个功能，原因：

1. Redis是单线程的。如果使用多个数据库，这些数据库仍然是使用一个CPU，彼此之间还是会受到影响
2. 多数据库的使用方式，让调试和运维不同业务的数据库变得困难，假如有一个慢查询，依然会想象到其他数据库
3. 部分Redis客户端根本不支持这种方式。即使支持，在开发时来回切换数字形式的数据库，容易混乱

建议如果要使用多个数据库，可以在一台机器上部署多个redis实例，用端口区分，合理利用CPU资源

```
select dbIndex // 切换数据库 
flushdb/flushall // 清除当前数据库/清除所有数据库
```

# 命名
Redis没有命令空间，也没有对键名又强制要求。设计合理的键名，有利于防止键冲突和项目的可维护性，比较推荐的方式是使用`业务名:对象名:id:[属性]`作为键名（也可以不是分号），例如`vs:user:111:name`（vs为业务名，如果只有一个业务，可省略）。如果键名比较长，例如`user:{uid}:friends:messages:{mid}`，可以减少键的长度，减少由于键过长的内存浪费：`u:{uid}:fr:m:{mid}`.   


## 第3章 小功能大用处

### 慢查询分析
在命令执行前后计算每条命令的执行时间，当超过预设阈值，就将这条命令的相关信息（如发生时间、耗时、命令的详细信息）记录下来

只记录执行时间，不记录排队等待时间和网络传输时间

- slowlog-log-slower-then 为预设阈值，单位是微秒（毫秒的千分之一），默认10 000，设置为0会记录所有命令，设置为小于0不会记录任何信息。建议设置为1000

- slowlog-max-length 慢查询日志最多存储多少条。建议设置为1000以上

- redis修改配置有两种方法，一种是修改配置文件，一种是使 config set xxx value 命令动态修改，修改后使用 config rewrite 持久化到本地配置文件

```
slowlog get n  // 获取慢查询日志，n为条数
slowlog len // 慢查询日志列表的长度
slowlog reset // 重置日志
```

### Redis Shell

#### redis-cli

```
// -r  将命令执行多次。执行3次ping：
redis-cli -r 3 ping

// -i 每隔几秒执行一次命令，必须和-r一起使用，单位是秒，可以设置为0.001。每隔1s执行一次ping，共执行5次：
redis-cli -r 5 -i 1 ping

// -x从标准输入读取数据作为redis-cli的最后一个参数。将world作为set hello的值
echo “hello” | redis-cli -x set hello

// -c（cluster）是连接Reids Cluster节点时需要使用的，防止moved和ask异常

// -a （auth）如果redis配置了密码，用-a就不需要手动输入auth命令

// —scan —pattern 用于扫描指定模式的键，相当于scan命令

// —slave 把当前客户端模拟成当前Redis节点的从节点，可以用来获取当前Redis节点的更新操作

// —rdb会请求Redis实例并发送RDB持久化文件，保存在本地，可使用它做持久化文件的定期备份

// —pipe 将命令封装成Redis通信协议定义的数据格式，批量发送给Redis执行

// —bigkeys 使用scan命令对Redis的键进行采样，从中找到内存占用比较大的键值

// —eval 执行指定lua脚本

// —latency 检测网络延迟

// —stat 实时获取重要统计信息（info命令的统计信息更全，但不是实时）

// —raw和—no-raw：no-raw返回结果必须是原始格式，raw返回格式化后的结果
```

#### redis-service

```
redis-server —test-momory 1024 用来检测当前操作系统是否能稳定地分配指定大小的内存给Reids
```

#### redis-benchmark
可为Reids做基准性能测试

```
// -c（client）代表客户端的并发数量（默认50）
// -n 代表客户端的请求总量（默认100 000）

// 100个客户端同时请求Redis，一共执行20000次：
redis-benchmark -c 100 -n 20000

// -q 仅限时requests per second信息
// -r（random）向Redis插入更多随机的键
// -P 每个请求pipeline的数据量（默认为1）
// -k 是否使用keepalive，1为使用，0为不使用，默认1
// -t 对指定命令进行基准测试

redis-benchmark -t get，set -q

// —csv 将结果按照csv格式输出
```

### Pipeline
Pipeline（流水线）机制能将一组Redis命令进行组装，一次性传输给Redis，再将这组命令的执行结果按顺序返回给客户端。Pipeline执行速度一般比逐条执行快

原生批量命令和Pipeline的对比

* 原生批量命令是原子的，Pipeline是非原子的
* 原生批量命令是一个命令对应多个key，Pipeline支持多个命令
* 原生批量命令是Redis服务端支持实现的，Pipeline需要服务端和客户端的共同实现

Pipeline组装的命令个数不能没有节制，如果数据量过大，会增加客户端的等待时间，也会造成一定的网络堵塞，可以将一次大量的Pipeline拆分成多次较小的Pipeline来完成

### 事务与Lua

#### 事务
表示一组动作，要么全部执行，要么全部不执行。Redis提供了简单的事物功能，将一组命令放到multi（事务开始）和exec（事务结束）之间。multi之后的命令并没有真正执行，而是暂时保存在Redis中，数据没变，只有当exec执行后，操作才真正完成。如果要停止事务的执行，使用discard代替exec

Redis不支持回滚

watch命令确保事务中的key没有被其他客户端修改过，才执行事务，否则不执行 

#### Lua

Lua数据类型：booleans布尔、numbers数值、strings字符串、tables表格

```lua
— 定义局部hello字符串。local代表局部变量，没有local代表全局变量
local strings hello = “world”
print(hello)

— 数组。使用tables来实现数组，数组下标从1开始
local tables myArray = {“redis”, “jedis”, true, 88}

— for
local int sum = 0
for i = 0, 100
do
    sum = sum + i
end

— 遍历myArray，需要知道tables的长度，只需要在变量前加一个#号即可
for i = 1, #myArray
do 
    print(myArray[i])
end

— ipairs 可遍历出所有的索引下标和值
for index, value ipairs(myArray)
do 
    print(index)
    print(value)
end

— while
local int sum = 0
local int i = 0
while i <= 100
do 
    sum = sum + i
    i = i + 1
end

— if else
if hello == “world”
then 
    print(“yes”)
else 
    — do nothing
end

— 哈希也可以使用tables来创建
local tables user = {age = 10, num = “tom”}
print(user[“age”])

— 函数定义
function func(num) 
    ...
end
func(1)
```

#### Redis与Lua
Redis将Lua脚本语言可以帮助开发者定制自己的Reis命令

在Redis执行Lua

```
// eval
// eval 脚本内容 key个数 key列表 参数列表
eval ‘return “hello” ...KEYS[1] ...ARGV[1]’ 1 redis world “hello redisword”
// 此时KEYS[1]=“redis”，ARGV[1]=“world”，最终返回“hello redisworld”

// 如果lua脚本较长，使用redis-cli —eval直接执行文件（把脚本作为字符串发送给服务端）

// evalsha执行Lua脚本。首先将脚本加载到redis服务器，得到sha1。evalsha使用sha1作为参数可以直接执行对应lua脚本，避免每次发送脚本的开销
// 加载脚本：将脚本内容加载到redis内存中，得到sha1
redis-cli script load “$(cat **.lua)”
evalsha sha1值 key个数 key列表 参数列表

// 是否存在
script exists sha1
// 清除已加载的所有脚本
script flush
// 杀掉这个正在执行的脚本
script kill
```

Lua的Redis API

```
redis.call实现对redis的访问，遇到错误会直接返回错误，redis.pcall遇到错误会忽略错误继续执行。调用redis的set和get：
redis.call(“set”, “hello”, “world”)
redis.call(“get”, “hello”)
```

### Bitmaps
可以实现对位的操作。本身并不是数据结构，实际上是字符串，但是可以对字符串的位进行操作。可以想象成是一个以位为单位的数组，每个单元只能是0或1

### HyperLogLog
实际类型为字符串，是一种基数算法，可以利用极小的内存完成独立总数的统计，但是存在误差（大概0.18%）

场景：如果只为了计算独立总数，不需要获取单条数据，而且可以容忍一定的误差率

### 发布订阅
Redis提供了基于”发布/订阅”模式的消息机制，消息发布者和订阅者不能直接通信，发布者客户端向指定的频道channel发布消息，订阅该频道的每个客户端都可以接收到该消息

```
// 发布消息。向频道channel:sports发布一条消息hello
publish channel:sports “Hello”

// 订阅消息，订阅者可订阅一个或多个频道。
subscribe channel 

// 取消订阅
unsubscribe channel1 channel2

// 按照模式订阅和取消订阅，支持glob风格的订阅命令和取消订阅命令
// 订阅以it开头的所有频道
psubscribe it*
punsubscribe it*

// 查询订阅
// 查看活跃的频道：当前频道至少有一个订阅着
pubsub channels 
pubsub channels channel:*r*

// 查看频道订阅数
pubsub numsub channel

// 查看模式订阅数
pubsub numpat
```

使用场景：聊天室、公告牌、服务之间

### GEO
地理信息定位功能，支持存储地理位置信息，底层实现是zset

```
// 增加地理位置信息
geoadd key longitude latitude member
geoadd cities:locations 116.28 39.55 beijing

// 获取
geopos key member
geopos cities:locations beijing

// 获取两个地理位置的距离。unit：m km mi英里 ft 尺
geodist key member1 member2 【unit】
geodist cities:locations beijing tianjin km

// 获取指定位置范围内的 地理信息位置集合
georadius key longitude latitude 
georadiusbymember key member 
参数：rediusm|km|ft|mi 【withcoord】【withdist】【withhash】【COUNT count】【asc|desc】【store key】【storedist key】

georadius和georadiusbymember都是以一个地理位置为中心算出指定半径内的其他地理信息位置，前者的中心位置给出了具体的经纬度，后者只需给出成员即可

withcoord：返回结果中包含经纬度
withdist：包含离中心点位置的距离
withhash：结果包含geohash
COUNT count：指定返回结果的数量
asc|desc：按中心节点的距离升序、降序
store key：将返回结果的地理位置信息保存到指定键
storedist key：将返回结果离中心点的距离保存到指定键

georadiusbymember cities-locations beijing 150 km

// 获取geohash：将二纬经纬度转换为一维字符串
geohash cities-locations beijing

// 删除地理位置信息
zrem key member
```

## 第4章 客户端
Java和Python版Redis客户端基本用法，略过

## 第5章 持久化
### RDB
把当前进程数据生成快照保存到磁盘，触发RDB持久化过程分为手动触发和自动触发

手动触发分别对应save和bgsave命令
- save：阻塞当前Redis服务器，直到RDB完成，线上环境不建议使用，已废弃
- bgsave：Redis进程fork操作创建子进程，持久化由子进程负责，完成后自动结束，阻塞只发生在fork阶段，时间很短

自动触发：
1. 使用“save”相关配置，如“save m n”，表示m秒内数据集存在n次修改时，自动触发bgsave
2. 如果从节点执行全量复制，主节点自动执行bgsave生成RDB文件并发送给从节点
3. 执行debug reload重新加载Redis时，自动触发save
4. 默认情况下执行shutdown命令，如果没有开启AOF，则自动执行bgsave

RDB文件的处理
- 保存：保存在dir配置指定的目录下，文件名通过dbfilename指定。通过执行config set dir {newDir} 和 config set dbfilename {newFileName}运行期动态执行，下次运行时RDB会保存到新目录
- 压缩：默认LZF算法对生成的RDB文件压缩，默认开启，压缩后文件远小于内存大小。通过config set rdbcompresssion yes|no 动态修改
- 校验：如果加载损坏的RDB文件时拒绝启动，可使用redis-check-dump工具检测RDB文件

优点：
- 紧凑压缩的二进制文件，代表Redis在某个时间点上的数据快照，适用于备份，全量复制等场景，比如每6小时备份，并把RDB文件拷贝到远程机器或文件系统
- Redis加载RDB恢复数据远快于AOF

缺点：
- 没办法做到实时化/秒级持久化，因为bgsave每次都要执行fork，属于重量级操作，频繁操作成本太高

### AOF（append only file）
以独立日志的方式记录每次写命令，重启时再重新执行AOF文件中的命令达到恢复数据的目的。主要作用是解决了数据持久化的实时性，是Redis持久化的主流方式

开启AOF需要设置配置：appendonly yes，默认不开启。AOF文件名通过appendfilename配置设置，默认文件名是appendonly.aof，保存路径和RDB一致，通过dir配置 

AOF工作流程
1. 命令写入append：所有的写入命令追加到aof_buff（缓冲区）中。写入的内容直接是文本协议格式
2. 文件同步（sync）：缓冲区根据对应的策略向硬盘做同步操作
3. 重写（rewrite）：压缩。超时的数据不再写入；只保留最终数据写入命令；多条写命令合并为一个，以64元素为界拆分为多条
4. 重启加载（load）：Redis重启，可加载AOF文件进行数据恢复。手动触发：bgrewriteaof命令；自动触发：auto-aof-rewrite-min-size（AOF重写时文件最小体积，默认64M），auto-aof-rewrite-percentage（当前AOF文件空间aof_current_size和上一次重写后AOF文件空间aof_base_size的比值）。触发AOF后，父进程会fork创建子进程，开销等同于bgsave，fork完成后，继续影响其他命令，所有修改命令写入AOF缓冲区...

**AOF开启并且存在AOF文件时，优先加载AOF，否则加载RDB**

### 优化
RDB和AOF都会执行fork，fork是重量级操作。改善fork的耗时：
1. 使用物理机或高效支持fork的虚拟化技术，避免使用Xen
2. 控制Redis实例最大可用内存，fork耗时和内存量成正比，建议每个Redis实力内存控制在10GB内
3. 合理配置Linux内存分配策略，避免内存不足导致fork失败
4. 降低fork操作的频率，如放宽AOF自动触发时机

## 第6章 复制
## 第7章 Redis的噩梦：阻塞
## 第8章 哨兵
## 第10章 集群

## 第11章 缓存设计
缓存的收益
- 加速读写
- 降低后端负载

缓存的负载
- 数据不一致
- 代码维护成本
- 因为成本

使用场景
- 开销大的复杂计算：对mysql来说复杂的操作或计算（例如大量联表操作、分组计算）
- 加速请求响应

### 缓存更新策略
缓存中的数据都需要有生命周期，需要在指定时间后删除或更新

** LRU/LFU/FIFO 算法剔除 **
剔除算法用于缓存超过预设的最大值的时候，如何对现有数据进行剔除。Redis使用maxmemory-policy这个配置作为内存最大值后对于数据的剔除策略

一致性差：要清理哪些数据由具体算法实现，开发人员只能决定使用哪种算法，所以数据的一致性是最差的

维护成本低：算法不需要自己实现，只需要知道每种算法的含义，选择适合自己的算法

** 超时剔除 **
通过给缓存数据设置过期时间，让其在过期时间后自动删除，Redis的expire命令。可以容忍这短时间内可能发生的数据不一致的情况

一致性差、维护成本不算高，只需设置expire

** 主动更新 **
对于一致性要求高的场景，需要在真实数据更新后，立即更新缓存数据。

一致性高，维护成本高，需要开发者自己完成更新，并保证更新操作的正确性

** 最佳实践 **
- 低一致性业务建议配置最大内存和淘汰策略的方式使用
- 高一致性业务可结合使用超时剔除和主动更新

### 缓存粒度控制
对于一个user来说，缓存全部属性还是只缓存部分属性呢？要综合以下角度进行取舍
- 通用性：缓存全部数据比部分数据更通用，但很长时间只需要几个重要的属性
- 空间占用：缓存全部数据要比部分数据更占空间，造成以下问题：
    - 内存浪费
    - 消耗的网络流量较大
    - 序列化和反序列化的CPU开销更大
- 代码维护：全部数据方便代码维护，部分数据一旦加了新的字段需要修改业务代码，还要刷新缓存数据

### 穿透优化
缓存穿透事指查询一个根本不存在的数据，缓存层和存储层都不会命中，通常出于容错的考虑，如果从存储层查不到数据则不写入缓存层。**导致不存在的数据每次请求都要到存储层去查询，失去了缓存保护后端存储的意义**

可在程序中分别调用总调用数、缓存层命中数、存储层命中数，如果发现大量存储层空命中，可能就出现了缓存穿透的问题

造成缓存穿透的基本原因：
1. 代码或数据出问题
2. 恶意攻击、爬虫造成大量空命中

解决穿透优化：
1. 存储空对象。当存储层不命中后，仍然保存空对象到缓存层中，之后再访问这个数据都会从缓存中获取，保护后端数据源。适用于数据命中不高、数据频繁变化实时性高。代码维护简单。但是会造成两个问题：
    1. 缓存层保存的过多的键，需要更多的内存空间，可以设置较短的过期时间
    2. 缓存层和存储层的数据会有一段时间窗口的不一致，可利用消息系统或其他方式清楚缓存的空对象
2. 布隆过滤器。在访问缓存层和应用层之前，将存在的key用布隆过滤器提前保存起来，做第一层拦截。用于数据命中不高、数据相对稳定、实时性低的应用场景，代码维护复杂，但是缓存空间占用少

### 无底洞优化
### 雪崩优化
### 热点key重建优化
当一个key是一个热点key，并发量非常大，或重建缓存不能在短时间完成，在缓存失效的瞬间，有大量线程来重建缓存，造成后端负载加大，可能让应用崩溃

1. 互斥锁：只允许一个线程重建缓存，其他线程等待该线程执行完成，重新从缓存获取数据。比较简单，但如果构建缓存时间较长，可能存在死锁和线程池阻塞，单能较好地降低后端存储负载，一致性较好

    ```Java
    String get(String key) {
        String value = redis.get(key);
        if (value == null) {
            // 只允许一个线程重构缓存，使用nx并设置过期时间ex
            String mutexKey = "mutes:key" + key;
            if (redis.set(mutexKey, "1", "ex 180", "nx")) {
                // 从数据源获取数据
                value = db.get(key)
                // 回写redis。并设置过期时间
                redis.setex(key, timeout, value);
                redis.delete(mutexKey);
            }
        } else {
            // 其他线程休息60ms后重试
            Thread.sleep(50)
            get(key)
        }
    } 
    ```

2. 永远不过期。缓存层面上不设置过期时间。从功能层面上为每个value设置一个逻辑过期时间，当发现超时后，用单独的线程去构建缓存。不足是在重构缓存期间会出现数据不一致的情况，取决于应用是否容忍这种不一致，代码复杂度会增大

## 第12章 开发运维中的“陷阱”
## 第13章 Redis监控运维云平台CacheCloud
## 第14章 Redis配置统计字典