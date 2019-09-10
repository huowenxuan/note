[TOC]

```
# mac 下安装
brew install mongodb

# 启动
sudo mongod
# 第一次启动报错Data directory /data/db not found., terminating
sudo mkdir /data
sudo mkdir /data/db
sudo mkdir/data/logs
# 如果报错没有可读权限，进入/data，增加读与写的权限

# 进入命令行
mongo

```







                      