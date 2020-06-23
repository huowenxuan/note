# 安装

```
# 切换源
sudo nano /etc/apt/sources.list
# 注释掉第一行，添加一行
deb http://mirrors.ustc.edu.cn/raspbian/raspbian/ stretch main contrib non-free rpi

sudo apt-get update
sudo apt-get install mysql-server
sudo apt-get install mysql-client
sudo apt-get install libmysqlclient-dev

配置文件在 /etc/mysql/conf.d/

# 查看是否安装成功
sudo netstat -tap | grep mysql
# 登陆
mysql -u root -p 
Enter password: 
```

