# ssh不输入密码登录
1. 在本地电脑执行命令：ssh-keygen，一路回车，将生成公钥在~/.ssh/id_rsa.pub
2. 在本地电脑执行命令：ssh-copy-id -i ~/.ssh/id_rsa.pub root@192.168.1.1

# ssh不输入username@ip进行登录
编辑`~/.ssh/config`，添加

```
Host super
    HostName 101.200.60.199
    User root
    
Host testsuper
    HostName 39.96.33.13
    User root
```

保存后即可