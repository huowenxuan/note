# ssh不输入密码登录
1. 在本地电脑执行命令：ssh-keygen，一路回车，将生成公钥在~/.ssh/id_rsa.pub
2. 在本地电脑执行命令：ssh-copy-id -i ~/.ssh/id_rsa.pub root@192.168.1.1 默认端口号22，如需设置为其他端口号，添加参数 -p xxx

# ssh不输入username@ip进行登录
编辑`~/.ssh/config`，添加

```
Host super
    HostName 101.200.60.199
    User root
    
Host testsuper
    HostName 39.96.33.13
    User root
    Port 22
```

保存后即可

# 指定端口号
ssh -p xxx xx@xxx.xxx.xxx.xxx      

# 本地端口转发
## 后台静默转发
-----------本地端口号:要转发的远程ip(mongo):要转发的远程端口号(mongo) ssh
ssh -CfNg -L 8888:10.26.32.60:27017 root@123.56.29.196
## 前台转发，可通过exit取消
ssh -L 8888:10.24.198.136:27017 root@123.56.29.196