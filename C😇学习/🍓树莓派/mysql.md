## 安装

```
sudo apt-get install mysql-server
# 如果提示让安装mariadb则执行
sudo apt-get install mariadb-server
# 如果失败则更新软件包
sudo apt-get update

# 再次安装，如果还提示出现错误，修改源
# 源位置
sudo nano /etc/apt/sources.list
# 注释掉第一行，添加一行
deb http://mirrors.ustc.edu.cn/raspbian/raspbian/ stretch main contrib non-free rpi
# 修改后执行 sudo apt-get update ，如果还失败，就把源还回去，再次update，就安装mariadb就成功了，不明白为什么（中间执行了一次 sudo apt-get install aptitude）
```



## 配置

安装 mariadb 成功后

```
# 空密码登录
sudo mysql
mysql>use mysql;
# 设置远程访问
mysql>update user set host='%' where user='root' and host='localhost';
# 为root授权远程登录，并设置密码（远程登录和本地登录都设置为该密码password）
mysql>grant all privileges  on *.* to root@'%' identified by "password";
mysql>flush privileges;
# 允许所有ip访问。配置文件位于 /etc/mysql/mariadb.conf.d/50-server.cnf
# 将其中的 bind-address 修改为 0.0.0.0
# 重启mysql
sudo service mysql restart
# 登陆
sudo mysql -u root -p
```



## TODO

内存优化