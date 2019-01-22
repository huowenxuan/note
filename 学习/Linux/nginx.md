
```
# 使用yum，安装在/etc/nginx, 配置文件在/etc/nginx/conf/nginx.conf或/etc/nginx/nginx.conf
yum install nginx

nginx # 启动
nginx -s reload #平滑重启

pkill -9 nginx

```

```
// 源码安装，安装在/usr/local/nginx
```
                     
## 错误
### [error] open() "/usr/local/var/run/nginx.pid" failed (2: No such file or directory)

```
pkill -9 nginx
nginx -s reload
```
