[TOC]

## centos

```sh
配置MongoDB的yum源
cd /etc/yum.repos.d 
vim mongodb-org-4.0.repo

使用阿里云的源

[mngodb-org]
name=MongoDB Repository
baseurl=http://mirrors.aliyun.com/mongodb/yum/redhat/7Server/mongodb-org/4.0/x86_64/
gpgcheck=0
enabled=1


# 安装
yum -y install mongodb-org
# 启动
systemctl start mongod.service
systemctl status mongod.service
# systemctl stop mongod.service
# 开机启动
sudo systemctl enable mongod.service

配置文件 /etc/mongod.conf
bindIp默认为127.0.0.1，修改为0.0.0.0可允许所有ip访问

日志
/var/log/mongodb/mongod.log
```

## mac 下安装

brew install mongodb

### 如果brew换中国源导致No available formula with the name "mongodb" 错误，安装社区版

brew tap mongodb/brew 

brew install mongodb-community

## 配置文件

etc /usr/local/etc/mongod.conf ?

## 启动

sudo mongod
## 第一次启动报错Data directory /data/db not found., terminating

sudo mkdir /data
sudo mkdir /data/db
sudo mkdir /data/logs

## 如果报错没有可读权限，进入/data，增加读与写的权限

## mac上报错 exception in initAndListen: IllegalOperation: Attempted to create a lock file on a read-only directory: /data/db, terminating

sudo mkdir -p /data/db
sudo  chmod 777 -R /data
sudo chown -R huowenxuan /data # 给用户赋予权限
再次启动

## 进入命令行

mongo

## 计算collection所占空间大小，以M为单位

db.xxxx.stats(1024 * 1024); // storageSize为所占空间大小

## 数据库导出与导入

mongoexport -h localhost --port 8888 --db aituwen --collection likes --out export.json --skip 10000000 --limit 100000 -q '{x: {$gt: 1}}' --sort '{x: 1}'

mongoimport -h localhost:27017 -d dbname --collection cname2 --file export.json

```

# 开启第二个实例，fork后台运行
mkdir -p /mnt/db/mongodb/data
mongod --port 27018 --dbpath /mnt/db/mongodb/data --smallfiles -oplogSize 128 --logpath /mnt/db/mongodb/mongo5.log --fork
```