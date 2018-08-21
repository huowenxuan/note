# ssh不输入密码登录
1. 在本地电脑执行命令：ssh-keygen，一路回车，将生成公钥在~/.ssh/id_rsa.pub
2. 在本地电脑执行命令：ssh-copy-id -i ~/.ssh/id_rsa.pub root@192.168.1.1