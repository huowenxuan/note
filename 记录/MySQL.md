# Mac
## 安装MySQL
1. 下载 [MySQL](https://dev.mysql.com/downloads/mysql/)，安装，新版mysql在安装时就可以设置密码，为8位数
2. 添加到环境变量
3. 查看在`/usr/local/mysql/bin`中是否有mysql
4. 如果有，就编辑`~/.bash_profile`，在最后添加`PATH=$PATH:/usr/local/mysql/bin`，输入`source ~/.bash_profile`生效

## 命令行
```
mysql -u root -p

create DATABASE db; // 每行都要加分号
```

## MySQL Workbench(MySQL GUI)
1. 下载[MySQL Workbench](https://dev.mysql.com/downloads/workbench/)

## 代码连接mysql报错` Client does not support authentication protocol requested by server; consider upgrading MySQL client`
```
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password'; // password为要设置的密码
```