## sudo免密
登录到root用户

visudo  //或者vi /etc/sudoers
在root ALL=(ALL) ALL下一行添加 `your_user_name ALL=(ALL) NOPASSWD: ALL`

## su免密
切换到root权限；
创建group为wheel，命令为groupadd wheel；
将用户加入wheel group中，命令为usermod -G wheel your_user_name；
修改su的配置文件/etc/pam.d/su,增加下列项：

```
auth       required   pam_wheel.so group=wheel 
# Uncomment this if you want wheel members to be able to
# su without a password.
auth       sufficient pam_wheel.so trust use_uid
```
 
 使用su root不需要密码