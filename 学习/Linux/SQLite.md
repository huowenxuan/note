# SQLite
## 命令
Linux默认安装SQLite，sqlite3

```
sqlite3 -version

// 可以指定一个完整文件的路径名，打开或者创建数据库(文件不存在，则创建)，同时进入sqlite后台操作程序
sqlite3 ./test.db

// 查看数据库信息
.database
// 查看所有表
.table
// 查看所有表的创建语句
.schema
// 查看某个表的创建语句
.schema table_name
// 退出SQLite
.quit
// 执行sql语句
select ...
```

## mysql迁移到sqlite3
1. 使用MySQL Workbench，将表导出为json，使用代码bulkCreate数据
2. 使用其他工具导出为.db文件，直接通过sqlite3运行