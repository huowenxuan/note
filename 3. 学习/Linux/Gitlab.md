# Gitlab
## 安装
https://about.gitlab.com/install/#centos-7

## 配置
配置文件在 /etc/gitlab/gitlab.rb
修改external_url为`http://ip`

## 命令
sudo gitlab-ctl reconfigure # 更新配置
sudo gitlab-ctl start # 启动
sudo gitlab-ctl stop # 停止
gitlab-ctl tail # 实时日志

## 访问页面错误：Whoops, GitLab is taking too much time to respond.
第一种：默认的8080被占用，修改配置
unicorn['port'] = 8888
gitlab_workhorse['auth_backend'] = "http://localhost:8888" 

或杀掉
lsof -i:8080
或
netstat -tunlp |grep 8080

第二种：内存不足，要求2G内存，所以2G的服务器

## 卸载
sudo gitlab-ctl stop # 停止
sudo rpm -e gitlab-ce # 卸载
ps -ef|grep gitlab # 查看进程
kill -9 4473 # 杀掉第一个守护进程
find / -name *gitlab*|xargs rm -rf # 删掉所有文件
find / -name gitlab |xargs rm -rf 

## Gitlab迁移、升级
### 数据备份、导出到本机
```
# gitlab代码保存在/var/opt/gitlab/git-data/repositories（gitlab-satellites目录为临时目录）
cd /var/opt/gitlab
sudo -sH # git-data可能无权限，无法cd，默认缺省为获取root用户
cd git-data
# 压缩
tar -zcvf repositories.tar repositories/
mv repositories.tar .. # 移动到上级目录，否则无权限scp
# 查看文件大小
ls -lht
# 传输文件到另一台服务器
scp /var/opt/gitlab/repositories.tar xxx@xxx.xxx.xxx.xxx:/var/opt/gitlab/repositories.tar
# 另一台服务器
# 解压
tar -xzf repositories.tar
```