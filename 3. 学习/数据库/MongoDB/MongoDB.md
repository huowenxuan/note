[TOC]

# mac 下安装
brew install mongodb

# 配置文件
cat /etc/mongod.conf

# 启动
sudo mongod
# 第一次启动报错Data directory /data/db not found., terminating
sudo mkdir /data
sudo mkdir /data/db
sudo mkdir /data/logs
# 如果报错没有可读权限，进入/data，增加读与写的权限

# mac上报错 exception in initAndListen: IllegalOperation: Attempted to create a lock file on a read-only directory: /data/db, terminating
sudo mkdir -p /data/db
sudo  chmod 777 -R /data
sudo chown -R huowenxuan /data # 给用户赋予权限
再次启动

# 进入命令行
mongo

# 计算collection所占空间大小，以M为单位
db.xxxx.stats(1024 * 1024); // storageSize为所占空间大小

# 数据库导出与导入
mongoexport --port 27017 --db dbname --collection cname --out export.json
mongoimport -h localhost:27017 -d dbname --collection cname2 --file export.json
```

# 开启第二个实例，fork后台运行
mkdir -p /mnt/db/mongodb/data
mongod --port 27018 --dbpath /mnt/db/mongodb/data --smallfiles -oplogSize 128 --logpath /mnt/db/mongodb/mongo5.log --fork