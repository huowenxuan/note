
```
# 使用yum或apt，安装在/etc/nginx, 配置文件在/etc/nginx/conf/nginx.conf或/etc/nginx/nginx.conf
yum install nginx
apt-get install nginx

nginx # 启动
nginx -s reload # 平滑重启

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

或者
```
nginx -c /etc/nginx/nginx.conf
nginx -s reload
```

## 例子
###  nginx.conf
```
user  root;
worker_processes  1;
error_log  /var/log/nginx/error.log warn;
pid        /run/nginx.pid;
events {
    worker_connections  1024;
}
http {
    include       /etc/nginx/mime.types;
    default_type  application/octet-stream;

    log_format  main  '$remote_addr - $remote_user [$time_local] "$request" '
                      '$status $body_bytes_sent "$http_referer" '
                      '"$http_user_agent" "$http_x_forwarded_for"';
    access_log  /var/log/nginx/access.log  main;
    sendfile        on;
    #tcp_nopush     on;
    keepalive_timeout  65;

    # 启用gzip
    gzip  on;
    gzip_min_length 1k;
    gzip_buffers 4 16k;
    gzip_comp_level 1;
    gzip_types text/plain application/x-javascript text/css application/xml text/javascript application/javascript;

    # 配置缓存
    #proxy_cache_path /usr/local/nginx/cache levels=1:2 keys_zone=cache_one:500m inactive=1d max_size=5g;
    #proxy_temp_path /usr/local/nginx/cache/temp;

    # body最大50M
    client_max_body_size 50M;
    client_body_buffer_size 128k;
    
    include /etc/nginx/conf.d/*.conf;
}
```

### conf.d/www.conf
整合http、https，把localhost:7002转发到/api/，把/build/index.html转发到/react/（结尾都有/）

```py
# HTTP server
#
server {
    listen 80;
    listen 443 ssl;
    ssl_certificate ./cert/hwx.pem;
    ssl_certificate_key ./cert/hwx.key;
    ssl_session_cache shared:SSL:1m;
    ssl_session_timeout  10m;
    ssl_ciphers HIGH:!aNULL:!MD5;

    server_name  www.huowenxuan.top localhost;

    location /api/  { 
        proxy_pass http://localhost:7002/; # 注意结尾的/
    }
    
    root /root/xx-react/build;
    location /react/ { 
        try_files $uri $uri/ /index.html;
        add_header Cache-Control no-cache;
        add_header Cache-Control private;
        expires -1;
    }

    location ~* \.(?:html)$ {
        add_header Cache-Control no-cache; 
        add_header Cache-Control private; 
        expires -1;
    }

    location ~* \.(?:jpg|jpeg|gif|png|ico|cur|gz|svg|svgz|mp4|ogg|ogv|webm|htc)$ {
        expires 1M;
        access_log off;
        add_header Cache-Control "public";
    }

    location ~* \.(?:css|js)$ {
        expires 1y;
        access_log off;
        add_header Cache-Control "public";
    }
}
```