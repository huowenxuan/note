[TOC]

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

```sh
gitlab-rails console production
# 全部用户
User.all
# 输出全部字符串，而非ActiveRecord :: Relation对象
User.all.to_a
# 输出json格式
User.all.as_json
```

## CI/CD

### 安装gitlab-runnder

```sh
curl -L https://packages.gitlab.com/install/repositories/runner/gitlab-runner/script.rpm.sh | sudo bash
yum -y install gitlab-runner
# root用户进入gitlab地址 /admin/runners，查看url和token，输入到下面命令中。后面的参数可回车跳过，executor可输入docker或shell，shell即可，docker需要选择镜像
gitlab-runner register
# 完成后刷新/admin/runners下面就会新增一行
```

### 编辑项目`.gitlab-ci.yml`

deploy部署。only test只在test分支执行。如果

```yml
stages:
  - deploy

deploy_job:
  stage: deploy
  script:
    - ssh root@xxx "cd /xxx && sh ./publish.sh"
  only:
    - test
```

#### script免密ssh

```sh
# GitLab服务器
# 切换gitlab-runner
su - gitlab-runner
cd ~/.ssh
# 查看是否有id_rsa.pub文件，如果没有，执行下面的命令
ssh-keygen -t rsa
# 查看公钥并且复制下来
cat id_rsa.pub
# 如果最后执行失败，切换到root用户再次执行上面的命令

# 登录到目标服务器
cd ~/.ssh
# 把上面的公钥粘贴到authorized_keys
vim authorized_keys

# 在gitlab服务器上ssh一次目标服务器，将服务器信息加入到known_hosts，即可正常部署。同时解决Host key verification failed.的错误
```

### 错误 `git fetch-pack: expected shallow list`

需要git 1.9+版本。升级git版本，centos中yum版本为1.8.3.1

```sh
# 查看yum git版本
yum info git
yum remove -y git
# https://stackoverflow.com/questions/21820715/how-to-install-latest-version-of-git-on-centos-7-x-6-x
# 安装源
yum install http://opensource.wandisco.com/centos/7/git/x86_64/wandisco-git-release-7-2.noarch.rpm # 失败就重试
yum install git # 升级到2.22.0。失败就重试
# 重新安装gitlab-runner，不需要先卸载，安装后不需要重新register
yum install gitlab-runner
```

## Gitlab迁移、升级

### 查看Gitlab版本
cat /opt/gitlab/embedded/service/gitlab-rails/VERSION
### 数据备份、导出到本机

```sh
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

导出后所有的group、project都默认为private，需要手动更新，成员需要添加为Maintainer或Developer，否则无法进行push
```

### 注册 

进入[新的GitLab](http://)注册，和[旧的GitLab](http://)使用完全一样的邮箱、用户名

### 新增SSH Key

1. 点击右上角头像 -> Settings -> 左侧SSH Keys
2. 将旧账号下的所有key都复制过来，title可重复

### 本地

1. 替换remote url。在项目根目录执行

   ```sh
   # Mac本地执行：
   sed -i '' "s/x.x.x.x/x.x.x.x/g" .git/config
   ```

2. 测试

   ```sh
   git push
   ```

### 服务器

1. 替换remote url：在项目根目录执行

   ### 

   ```sh
   # 某些服务器上sed需要去掉第一个参数，否则报错"sed：无法读取..."
   sed -i "s/x.x.x.x/x.x.x.x/g" .git/config
   ```

2. 然后直接使用git pull尝试，如果失败就继续执行下面的步骤

3. 查看服务器公钥

   ```
   cat ~/.ssh/id_rsa.pub
   # 如果文件不存在
   ssh-keygen
   # 之后再输入username和登录密码
   ```

4. 复制后添加到`gitlab `的`ssh keys`中

### 迁移后commit数为0的解决方法
设置->仓库->默认分支 修改为其他分支再修改回来即可

### **同版本**备份和恢复

```sh
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
