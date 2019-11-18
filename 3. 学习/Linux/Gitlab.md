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


## 更换root密码
gitlab-rails console production
等待进入控制台
user = User.where(id: 1).first
user.password="xxx"
user.password_confirmation="xxx"
user.save!

## gitlab-rails控制台

```
gitlab-rails console production
# 全部用户
User.all
# 输出全部字符串，而非ActiveRecord :: Relation对象
User.all.to_a
# 输出json格式
User.all.as_json
```

## Gitlab迁移、升级
### 查看Gitlab版本
cat /opt/gitlab/embedded/service/gitlab-rails/VERSION
### 数据备份、导出到本机

```
# gitlab代码保存在/var/opt/gitlab/git-data/repositories（gitlab-satellites目录为临时目录）
# 备份
cd /var/opt/gitlab
sudo -sH # git-data可能无权限，无法cd，默认缺省为获取root用户
cd git-data
# 压缩
tar -zcvf repositories.tar repositories/
mv repositories.tar .. # 移动到上级目录，否则无权限scp
# 查看文件大小
ls -lht
# 传输文件到新服务器
scp /var/opt/gitlab/repositories.tar x@x.x.x.x:/var/opt/repositories.tar

# 新服务器
# 解压
cd /var/opt/
tar -xzf repositories.tar
chown -R git:git repositories # 必须给git权限
sudo gitlab-ctl reconfigure # 安装成功后先更新配置，失败就重试
gitlab-rake gitlab:import:repos['/var/opt/repositories/'] # 导入备份，填入解压后的目录地址。有输出Processing...则成功，无输出则失败
```

### **同版本**备份和恢复

```
gitlab-rake gitlab:backup:create
cd /var/opt/gitlab/backups # 发现生成一个类似1574047630_gitlab_backup.tar的文件
# 查看文件大小
ls -lht
# 传输文件到新服务器
scp *.tar x@x.x.x.x:/var/opt/gitlab/backups
# 登录到新的服务器
chmod 777 1574047630_gitlab_backup.tar
# 停止相关数据连接服务
gitlab-ctl stop unicorn
gitlab-ctl stop sidekiq
# 恢复BACKUP为备份文件编号
gitlab-rake gitlab:backup:restore BACKUP=1574047630
```
