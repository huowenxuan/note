[TOC]

## 第 1 章 初识Redis

> 五种类型的基本使用方法，加一个投票小案例

一般使用:作为分隔符，也可用./|，保持统一

## 第 2 章 使用Redis构建Web应用

### 登录和cookie缓存

使用hash(散列)保存用户信息

有序集合或列表保存用户访问记录，最多保存1000万个(假设)(或每个用户保存一个月内的10000个)，如果超出，每次删除最老的100个，如果没有达到最大值，休眠1秒再次计数

### 使用Redis实现购物车

每个购物车都是一个hash，保存商品id和数量之间的映射。如果商品数量大于0，添加到hash中，如果hash中已有则覆盖，如果不大于0就从hash中删除

### 数据行缓存

> 对数据的某些字段进行不定期更新缓存

例如促销活动，将需要频繁查询修改的n个字段放一起 toJSON 保存到redis中

（将整个活动每个字段缓存到redis hash中，但是对于标题等字段不需要更新，只需要不定期更新库存等字段即可）

使用两个有序集合来记录应该在何时更新缓存

1. 调度有序集合：key为字段名，值为时间戳，记录应该在何时缓存数据
2. 延时有序集合：key为字段名，值为缓存应该多久更新一次

程序先每50ms循环从集合1中查询是否有需要缓存的数据，如果有，开始缓存数据，并将集合1的时间设置为当前时间+集合2的延迟时间。

可修改2的时间，当为0时删除两个集合对应数据，不再进行更新

（可能会导致超卖）

### 网页分析

> 找出热门数据对它们进行缓存，而非缓存所有

通过每个用户访问记录的有序集合来计算热门数据太耗时间

需要一个记录所有商品浏览次数的有序集合viewed:userid，对浏览次数进行排序，浏览最多的商品放在索引0的位置（？），且具有序集合最少的分值(scope)

```python
redis.add("viewed:" + userid, data, timestamp)
redis.zremrangebyrank('viewed' + userid, 0, -26) // 删除用户25名之后的浏览
redis.zincrby('viewed:', data, -1) // 减1分?
```

需要定期对排行榜数据进行更新，删除排名中多余的商品，并将剩余商品的浏览次数减半

zinterstore将一个或多个有序集合求并集并计算，生成一个新的集合

```python
redis.zremrangebyrank("viewed:", 0, -20001) // 删除2000名之后的商品
redis.zinterstore("viewed:", {'viewed': .5}) // 将浏览次数降低为原来的一半，给新商品流行的机会
```

最终可将前10000个商品进行缓存

## 第 3 章 Redis命令

### 字符串

字符串可保存字节串，整数（长整数），浮点数（双精度）。

数字可自增和自减，空串自增自减当做0处理，无法被解释为数字会报错

### 列表

列表可包含多个字符串值，使用户可以将数据集中在一个地方

列表相比集合省内存，因为不需要分值

### 集合

主要是保存不相同的元素，厉害在于组合和关联多个集合

### 散列(Hash)

多个键值对储存在redis key里，存储着键和值之间的映射，提供了一些与字符串相同的特性

### 有序集合

存储着成员和分值之间的映射，提供了分值（双精度浮点数）处理命令，可根据分值大小有序地获取或扫描成员和分值。交集和并集可实现搜索系统

### 发布与订阅 pub/sub

订阅者listener订阅频道channel，发布者publisher发送二进制字符串消息binary string message，订阅者会接收到消息

一般不使用redis的该模式

1. 旧版本redis，如果客户端读取消息的速度不够快，积压的消息会使redis输出缓冲区的体积越来越大，导致redis速度变慢，甚至崩溃，或者被系统杀死，甚至导致操作系统不可用。新版redis不存在这种问题，会自动断开不符合client-output-buffer-limit pubsub配置选项要求的订阅客户端
2. 传输可靠性，如果客户端在执行订阅中短线，那么客户端将在丢失断线期间发送的所有消息

### 其他命令

排序sort，用于列表、集合、有序集合的排序，默认升序

```
// 排序。返回或者存储结果
SORT key [BY xxx] [LIMIT offset count] [GET xxx [GET xxx ...]] [ASC|DESC] [ALPHA] [STORE key2]
```

### Redis的基本事务

watch、multi、exec、unwatch

基本事务用到multi和exec，让一个客户端在不被其他客户端打断的情况下执行多个命令，和关系型数据库可进行回滚的事务不同。当redis收到一个multi时，将这个客户端之后发送的所有命令放到一个队列中，直到该客户端发送exec，然后redis就会在不被打断的情况下一个接一个的执行队列中的命令。当一个事务执行完之后，redis才会执行其他客户端的命令

主要作用是移除竞争条件，防止可能造成的内存泄露和数据不正确（多个线程自增同一个数据造成竞争而发生错误）。可以提高性能，减少通信次数

### 键的过期时间

只有少数几个命令可以原子地为键设置过期时间，并且对于列表、集合、散列和有序集合这样的容器来说，键过期只能为整个键设置过期时间，没办法为单个元素设置（可使用存储时间戳的有序集合来实现针对单个元素的过期操作）

## 第 4 章 数据安全与性能保障

### 持久化选项

持久化配置选项，两种可同时也可单独使用也可都不使用

```
// 快照持久化选项
save 60 1000 // 多久执行一次，频繁会浪费资源，次数太少会丢失大量数据
stop-write-on-bgsave-error no // 创建失败后是否仍然执行写命令
rdbcompression yes // 是否对快照进行压缩
dbfilename dump.rdb // 命名

// AOF持久化选项
appendonly no // 是否使用aof
// 多久将写入的内容同步到硬盘
// always 每个写命令都写入硬盘，严重降低redis速度（普通硬盘每秒只能处理大约200个命令，SSD每秒也只能几万个，并且不断写入少量数据可能引发“写入放大问题”，可能将SSD的寿命从几年降低为几个月） 
// everysec 每秒一次同步，推荐使用，和不使用任何持久化时的性能相差无几
// no 让操作系统来决定何时同步，系统崩溃可能导致丢失一些数据，如果用户硬盘处理写入的速度不够快，当缓冲区等待写入硬盘的数据填满时，redis写入操作会阻塞，不推荐使用
appendfsync everysec 
no-appendfsync-on-rewrite no // AOF压缩时能否执行同步操作
// 体积大于64m，并且文件体积比上次重写之后大了至少100%时，执行bgrewriteaof压缩
auto-aof-rewrite-percentage 100 
auto-aof-rewrite-min-size 64mb

// 共同选项，保存位置
dir ./
```

#### 快照 snapshotting

> 可将某一时刻的所有数据写入到硬盘里面

创建

* bgsave：redis调用fork创建一个子进程，负责将快照写入硬盘，父进程继续处理请求，最好留下30-45%的内存来执行
* save: 收到save之后在快照创建完毕之前不再响应任何命令，不常用，在没有足够内存执行bgsave才使用。不会像bgsave一样因创建子进程导致redis停顿，并且因为没有子进程抢资源，**创建快照速度要更快**
* 设置了save配置选项: 比如 save 60 1000，从redis最近一次创建快照算起，当“60秒内有1000次写入”这个条件被满足时，redis自动触发bgsave，如果设置了多个 save 配置，任一个配置条件满足都会触发
* 当一个redis服务器连接另一个redis服务器，并向对方发送sync命令来开始一次复制操作的时候，如果主服务器目前没有或刚刚没有执行bgsave，那么主就会执行bgsave

如果发生崩溃，快照只能恢复最近一次快照之前的数据，适用于丢失一部分数据也不会造成问题的应用程序

#### AOF持久化

> 将被执行的写命令写到AOF文件的末尾，记录数据发生的变化，从头到尾执行所有命令就可以恢复

缺点：AOF文件体积会越来越大，可能是快照的好几倍，可能会用完硬盘空间，在还原数据时候也会时间太长

bgrewriteaof命令：压缩aof文件，移除冗余命令，减小aof体积。fork一个子进程，负责重写，也会因创建子进程导致性能问题和内存占用问题，重写并删除旧的大文件时也可能导致系统挂起数秒

判断全部数据是否已保存在硬盘中：判断info命令的 aof_pending_bio_fsync 的值是否为0，为0表示已经将所有数据保存在硬盘中

### 复制

> 主服务器向多个从服务器发送更新，从服务器处理所有读请求

```
slaveof no one  // 该从服务器关闭复制功能，并从从服务器变回主服务器，数据不丢失，可以在主服务器失败的时候，将从属服务器用作新的主服务器，从而实现无间断运行
slaveof host post // 将当前服务器转变为指定服务器的从服务器
```

执行slaveof后的复制启动过程：

| 步骤 | 主服务器操作                                                 | 从服务器操作                                                 |
| ---- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 1    | 等待命令进入                                                 | 连接或重连接主服务器，发送sync命令                           |
| 2    | 自动执行bgsave，并缓冲区记录bgsave之后执行的所有写命令       | 根据配置来决定是继续用现有数据处理客户端的命令请求，还是向客户端返回错误 |
| 3    | bgsave执行完毕，向从服务器发送快照文件，发送期间继续使用缓冲区记录 | 丢弃所有旧数据，开始使用快照                                 |
| 4    | 快照发送完毕，开始向从服务器发送缓冲区的写命令               | 完成对快照的解释操作，开始接受命令请求                       |
| 5    | 缓冲区写命令发送完毕。每执行一次写命令，就向从服务器发送相同的写命令 | 接收并执行主服务器传来的每个写命令                           |

当多个从服务器连接同一个主服务器的时：如果步骤3尚未执行，所有从服务器都会接收相同的快照和缓冲区写命令；如果步骤3正在执行或执行完毕，主服务器会与新连接的从服务器重头开始执行

**从服务器同步会清空数据**；Redis不支持主主复制

主从链：当读请求的重要性明显高于写请求，且读请求的数量远高于一台redis服务器可以处理的范围时，就需要添加新的从服务器，主服务器可能无法快速地更新所有从服务器，就需要建立**从服务器的从服务器**来分担主服务器的复制工作

### 处理系统故障

```
// 检查aof文件的状态（无参数时）
// 增加--fix参数会对文件进行修复：扫描文件，寻找不正确或不完整的命令，当出现第一个出错命令时，会删除包括出错命令后的所有命令，大多数情况都是删除文件末尾的不完整写命令（因意外崩溃导致）
redis-check-aof 

// 检查快照文件的状态，快照无法修复
redis-chaeck-dump <dump.rdb> 
```

**更换故障主服务器**

假设A为主，B为从，A突然故障

1. 将C作为主：向B发送save，创建快照，发送给C，C启动redis，让B成为C的从
2. 或者将B作为主，C作为从
3. 最后更新客户端，修改连接的redis

### Redis事务

multi和exec在执行exec后才会有实际操作，所以没办法根据读取到的数据来做决定

通过使用watch、multi/exec、unwatch/discard等命令，可确保自己正在使用的数据没有发生变化来避免出错

```
// 使用watch对key监听后，直到exec这段时间里，如果有其他客户端抢先对key进行了写操作，执行exec时，事务将失败并返回错误。
watch key

// watch执行后、multi执行前对连接进行重置（取消监听）
unwatch

// multi执行后、exec执行前对连接进行重置，取消监听，清空已入队的任务
discard
```

为什么Redis没有实现加锁功能：典型的关系型数据库加锁的缺点是持有锁的客户端运行越慢，等待解锁的客户端被阻塞的时间就越长，redis为了减少客户端等待时间，不会在watch时加锁，只会在其他客户端修改后通知执行了watch的客户端，这种做法为乐观锁，只需要在事务执行失败时重试即可，关系数据库的锁为悲观锁

执行事务的好处之一就是客户端会通过使用流水线来提高事务执行时的性能（只在exec才发送命令）

### 非事务型流水线

> 在不使用事务的情况下通过流水线提升命令的执行性能（一次性发送多个命令来减少通信次数降低延迟）
>
> multi和exec会消耗资源，也可能导致其他重要的命令被延迟执行

在python中使用pipline()函数传入True或者无参数调用，将会使用事务来包裹命令，如果传入False，也会收集命令但是不使用事务，需要注意一个命令的结果不会影响另一个命令

### 关于性能方面的注意事项

```
// redis自带的性能测试程序，可了解redis在自己服务器上各种性能特征，一些命令在1秒内可执行的次数
// 无参数时将使用50个客户端进行性能测试，-c 客户端数量
redis-benchmark -c 1 -q
```

## 第 5 章 使用Redis构建支持程序

帮助和支持系统

### 使用Redis来记录日志

* 使用列表lpush记录日志的name、message、级别、时间，ltrim去掉早期日志，无法分辨哪些消息重要
* 使用有序集合，将出现的频率设置为分值，每一小时对老的消息集合根据时间重命名，再新增新的集合

```python
# 记录常见日志
def log_common(conn, name, message, severity=loggin.INFO, timeout=5):
  # 存储近期常见日志消息的key
  destination = 'common:' + name + ':' + severity
  # 程序每小时要轮换一次日志，所以使用一个键来记录当前所处的小时数
  start_key = destination + ':start'
  pipe = conn.pipeline()
  end = time.time() + timeout
  while time.time() < end:
    try: 
      # 监视，确保轮换能操作正确执行
      pipe.watch(start_key)
      now = datetime.utcnow().timetuple()
      # 当前所处小时数
      hour_start = datetime(*now[:4]).isoformat()
      existing = pipe.get(start_key)
      pipe.multi()
      # 如果这个常见日志列表记录的是上一个小时的日志
      if existing and existing < hour_start:
        # 将旧的常见日志归档
        pipe.rename(destination, destination + ':last')
        pipe.rename(start_key, destination + ':pstart')
        # 更新当前所处的小时数
        pipe.set(start_key, hour_start)
      # 对记录日志出现次数的计数器执行自增操作
      pipe.zincrby(destination, message)
      execute()
      # 可用来记录日志
      log_recent(pipe, name, message, severity, pipe)
      return 
    except redis.exceptions.WatchError:
      # 监视错误，重试
      continue
```



### 计数器

> 为了收集指标数据并进行监控分析（例如网站响应速度、点击量），构建一个能够持续创建并维护计数器的工具，这个工具创建的每个计数器都有名字，这些计时器以不同的时间精度（1s、5s、1min）存储最新的n个数据

如网站点击量计时器，使用一个hash（count:）保存每个时间片之内获得的点击量，每个key都是开始时间，值为点击量

清理旧的计数器，还需要一个有序集合（konw:），不能重复，可遍历，对计数器进行记录，集合的每个成员由计数器精度和名称组成（5:hits），所有成员分值为0，redis会自动使用成员名排序，按条件循环查询需要清理的计数器进行清理

```python
# 计数器精度，1s 5s 1min 5min 1h 5h 1d
PRECISION = [1, 5, 60, 300, 3600, 18000, 86400]

# 更新计数器
def update_counter(conn, name, count=1, now=None):
    now = now or time.time()
    pipe = conn.pipeline()  # 创建流水线
    # 为每个精度都创建一个计时器
    for prec in PRECISION:
        pnow = int(now / prec) * prec # 当前时间片的开始时间
        key = '%s:%s' % (prec, name)
        # 计时器的引用信息添加到有序集合，分值设为0
        pipe.zadd('know:', key, 0)
        # 更新计数器
        pipe.hincrby('count:' + key, pnow, count)
    pipe.execute()

# 获取计数器
def get_counter(conn, name, precision):
    key = '%s:%s' % (prec, name)
    # 取出计数器数据
    data = conn.hgetall('count:' + key)
    to_return = []
    # 转化格式
    for key, value in data.iteritems():
        to_return.append((int(key), int(value)))
    # 排序，把旧数据排在前面
    to_return.sort()
    return to_return
```

### 统计数据

保存统计结果数据：记录数据（某个页面一小时内的访问时间）的最小值，最大值，数量count，和，平方和sumsq，并通过这些信息计算平均值和标准差。保存在有序集合可进行并集计算，并通过min和max筛选相交的元素

```python
# 更新 value可以是页面响应时间、停留时间等，可在每次访问后计算出响应时间后调用
def update_stats(conn, page='UserPage', type='AccessTime', value, timeout=5):
  destination = 'stats:' + page + ':' + type
  # 开始处理当前一小时的数据和上一小时的数据，将不属于当前一小时的数据归档
  start_key = destination + ':start'
  pipe = conn.pipeline()
  end = time.time() + timeout
  while time.time() < end: 
    try: 
      pipe.watch(start_key)
      now = datetime.utcnow().timetuple()
      hour_start = datetime(*now[:4].isoformat())
      existing = pipe.get(start_key)
      pipe.multi()
      if (existing and existing < hour_start):
        pipe.rename(destination, destination + ':last')
        pipe.rename(start_key, destination + ':pstart')
        pipe.set(start_key, hour_start)

      tkey1 = str(uuid.uuid4())
      tkey2 = str(uuid.uuid4())
      # 值添加到临时键
      pipe.zadd(tkey1, 'min', value)
      pipe.zadd(tkey2, 'max', value)
      # 使用聚合函数对存储统计数据的key和两个key并集
      pipe.zunionstore(destination, [destination, tkey1], aggregate='min')
      pipe.zunionstore(destination, [destination, tkey2], aggregate='max')  
      # 删除临时键
      pipe.delete(tkey1, tkey2)
      # 对有序集合的3个统计数据更新
      pipe.zincrby(destination, 'count')
      pipe.zincrby(destination, 'sum', value)
      pipe.zincrby(destination, 'sumsq', value * value) 
      return pipe.execute()[-3: ]
    except redis.exceptions.WatchError:
      # 重试
      continue

# 获取
def get_stats(conn, page, type):
  key = xxx
  # 取出基本统计数据，放在dict中
  data = dict(conn.zrange(key, 0, -1, withscores=True))
  # 平均值
  data['average'] = data['sum'] / data['count']
  numerator = data['sumsql'] - data['sum'] ** 2 / data['count']
  # 标准差
  data['stddev'] = (numerator / (data['count'] -1 or 1)) ** .5
  return data

# 将页面平均访问时长加入到记录最长访问时间的有序集合中
pipe.zadd('slowest:AccessTime', page, average)
# 集合值保留最慢的100条
pipe.zremrangebyrank('slowest:AccessTime', 0, -101)
```

工具：Graphite可用于收集并绘制计数器以及统计结果

### 查找IP所属城市以及国家



PDF 120 页

书 100 页

