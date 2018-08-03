# Mac
## 安装MySQL
1. 下载 [MySQL](https://dev.mysql.com/downloads/mysql/)，安装，新版mysql在安装时就可以设置密码，为8位数
2. 添加到环境变量
3. 查看在`/usr/local/mysql/bin`中是否有mysql
4. 如果有，就编辑`~/.bash_profile`，在最后添加`PATH=$PATH:/usr/local/mysql/bin`，输入`source ~/.bash_profile`生效

## MySQL Workbench(MySQL GUI)
1. 下载[MySQL Workbench](https://dev.mysql.com/downloads/workbench/)

## 代码连接mysql报错` Client does not support authentication protocol requested by server; consider upgrading MySQL client`
```
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password'; // password为要设置的密码
```

# CentOS

# 命令行
```
mysql -u root -p

create DATABASE db; // 每行都要加分号
// 修改root密码
set password for 'root'@'localhost'=password('要设置的密码');
// 修改远程登录的密码
GRANT ALL PRIVILEGES ON *.* TO 'root'@'%' IDENTIFIED BY '要设置的密码' WITH GRANT OPTION;
// 启动服务
service mysqld start
// 重启
service mysqld restart
// 连接远程mysql
mysql -u root -p -h 101.200.60.199 -P 3306
```

# 支持中文及表情

```
vim /ect/my.cnf
```

在对应位置添加

```
[client]
default-character-set=utf8mb4
   
   
[mysql]
default-character-set=utf8mb4
   
   
[mysqld]
character-set-server = utf8mb4
collation-server = utf8mb4_unicode_ci
init_connect = 'SET NAMES utf8mb4'
character-set-client-handshake = false
```

在建表时选择encoding(CHARACTER)为utf8mb4，collation默认即可。已存在的表也需要修改编码为utf8mb4