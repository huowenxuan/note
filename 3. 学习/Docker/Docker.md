[TOC]

# Docker

curl -sSL https://get.daocloud.io/docker | sh

下载镜像加速——百度“docker加速器”

## CentOS安装

CentOS 7
```
yum install -y docker
yum install -y docker-compose
# 启动
systemctl start docker.service
# 开机启动
sudo systemctl enable docker
```

CentOS 6

```
yum install epel-release
yum install docker-io
# 如果报错 No package docker available，执行下面两句
cd /etc/yum.repos.d
sudo wget http://www.hop5.in/yum/el6/hop5.repo
# 再次运行
yum install -y docker-io
# 启动
docker -d
service docker start

# 如果报错 Error creating bridge: ip failed: ip link add docker0 type bridge (output: )
# 手动创建docker0网桥
sudo ip link set dev docker0 down
sudo brctl delbr docker0
sudo iptables -t nat -F POSTROUTING 
brctl addbr docker0
ip addr add 192.168.5.1/24 dev docker0
ip link set dev docker0 up
ip addr show docker0
echo 'DOCKER_OPTS="-b=docker0"' >> /etc/default/docker
docker -d & 

# 开机启动
chkconfig docker on
# 如果报错 docker: 未被识别的服务，使用nohup
nohup docker -d &
# nohup停止
# 查看进程id
ps
# 关闭
kill -9 pid

# 安装依赖 
yum install gcc g++ zlib zlib-devel openssl-devel
# 安装python2.7，安装后，可通过python2.7命令打开
wget https://www.python.org/ftp/python/2.7.8/Python-2.7.8.tgz
tar xf Python-2.7.8.tgz
cd Python-2.7.8
./configure --prefix=/usr/local
make && make install

# 安装easy_install、pip，安装好后可通过pip2.7安装
vi /etc/resolv.conf
新增 nameserver 8.8.8.8
# 安装setuptools
wget https://pypi.io/packages/source/s/setuptools/setuptools-33.1.1.zip
unzip setuptools-33.1.1.zip
cd setuptools-33.1.1
python2.7 setup.py install

# 安装pip https://pypi.python.org/pypi/pip找到下载地址
wget https://files.pythonhosted.org/packages/ce/ea/9b445176a65ae4ba22dce1d93e4b5fe182f953df71a145f557cffaffc1bf/pip-19.3.1.tar.gz
tar -zxvf pip-19.3.1.tar.gz 
cd pip-19.3.1
python2.7 setup.py install

# 安装docker-compose，最低要求python2.7
pip2.7 install docker-compose
# 最后报错 Internal server error: 404 trying to fetch remote history for xxx
放弃
```

## 命令

```
sudo docker build -t sword .

# 新建并开启一个容器
# sudo docker run -d --net=host  --name sowrd sword
# 只能使用 这种方法将docker7002端口映射到宿主环境的7002
sudo docker run -d  --name sowrd  -p 7002:7002 sword
# 添加-ti参数可直接进入容器shell
docker run -ti ubantu /bin/bash

# 启动一个关闭的容器
docker container start cid
# 关闭一个容器
docker container stop cid

# 重启，使代码生效
docker restart cid

docker ps # 查看运行的容器，获得containerid
docker ps -a  # 查看挂掉的容器

# 追踪log 后面的参数为container id
docker logs -f ec6d7d403ca0

# 停止容器
sudo docker stop containerId

# 删除容器
sudo docker rm containerId

docker image ls
docker image rm imageid

# 查看端口占用
lsof -i:7002

# 进入容器
docker exec -it <containerID> /bin/sh
docker exec -it <containerID> /bin/bash
# 交互式运行容器（运行并命令行进入）
# 其中centos可改为本地容器image，即使run失败的容器也可进入
docker run -i -t centos /bin/bash

# 宿主机重启后自动启动容器
# 前提有两个：
# 宿主机system enable docker。就是说：宿主机开机时，会自动启动docker服务。
# 已经docker start了该container。
docker update --restart=always <name>
docker update --restart=no <name>
```

## 容器内访问宿主机端口

1. 宿主机 ip addr show docker0 
2. inet后面为172.18.0.1/16，则在容器内可通过172.18.0.1访问到宿主机

## 使用Dockerfile定制镜像

```
构建镜像
# 在有Dockerfile的目录下构建，-t指定镜像名称<仓库名>:<标签>
docker build -t tag:v1 .
# -f或者--file指定dockerfile文件 
docker build -t tag:v1 . -f
```

直接用Git repo进行构建
docker build https://github.com/twang2218/gitlab-ce-zh.git#:11.1
这行命令指定了构建所需的 Git repo，并且指定默认的 master 分支，构建目录为 /11.1/，然后 Docker 就会自己去 git clone 这个项目、切换到指定分支、并进入到指定目录后开始构建。

用给定的 tar 压缩包构建
docker build http://server/context.tar.gz
如果所给出的 URL 不是个 Git repo，而是个 tar 压缩包，那么 Docker 引擎会下载这个包，并自动解压缩，以其作为上下文，开始构建。

## Dockerfile

```shell
# FROM写在最前，代表以何种镜像为基础
FROM node:10.10.0

# RUN 执行一些shell命令，比如安装依赖，通常写到一行，因为一个指令就是一个镜像层，安装的指令合在一层是最佳实践
RUN apt-get install -y vim

# 三种写法示例
RUN npm run dev # shell格式，相当于执行/bin/sh -c "<command>"：
RUN ["npm", "run", "dev"] # exec格式，不会触发shell，所以$HOME这样的环境变量无法使用，但它可以在没有bash的镜像中执行，而且可以避免错误的解析命令字符串
RUN ["/bin/bash", "-c", "npm run dev"] # 与shell相同

# CMD
# 一个Dockerfile里只能有一个CMD，如果有多个，只有最后一个生效
# docker run会执行CMD：是在build完成后，启动容器时的命令
CMD ./node_modules/.bin/egg-scripts start --env=$env --port=7002
# docker run如果加参数，参数会替换CMD的内容，ENTRYPOINT不会
ENTRYPOINT ["/bin/echo"]
docker run xxx hello
# 此时会输出hello，而不是替换掉命令

# VOLUME 将本机的目录挂在到镜像中
# COPY和ADD 把文件复制到容器中，一般使用COPY，远程文件使用ADD
# WORKDIR 切换目录，类似cd
```

### 自定义参数
```
# Dockerfile
ARG user1 # 参数必须先使用ARG声明
ARG user2
# 默认值
ARG user1=abc
# 使用
${user1} $user1
```
构建：
docker build --build-arg user=user1

```
# Dockerfile
# 使用ENV指定可用于RUN/CMD指令的变量。因为在RUN/CMD时已运行起来，此时访问的是环境变量，而不是Dockerfile变量，所以必须使用ENV。使用ENV定义的环境变量始终会覆盖同一名称的ARG指令定义的变量
ARG user1
ENV user1=$user1 # 把user1赋值给ENV的user1
${user1}
```

构建。此时RUN指令解析user1变量的值为abc.0而不是ARG设置并由用户传递过来的def
docker build --build-arg user1=def 

## 启动容器
启动容器有两种方式，一种是基于镜像新建一个容器并启动，另外一个是将在终止状态（stopped）的容器重新启动。

新建并启动
所需要的命令主要为 docker run

启动已终止容器
可以利用 docker container start 命令，直接将一个已经终止的容器启动运行

## docker-componse
```
# 以本地的docker-compose.yml构建，指定yml文件使用-f
docker-compose  build
# 运行，代替docker run。-d 后台运行；如果docker-compose.yml指定了image，并且存在，就直接运行，否则会执行build
docker-compose up -d
# 查看后台启动的服务日志
docker-compose logs
# 将所有通过up启动的容器停止并销毁，加入--volumes会清空储存卷
docker-compose down
# 查看启动的容器的信息
docker-compose ps
# 停止所有up的容器
docker-compose stop
# 启动被stop的容器
docker-compose start
# 重启
docker-compose restart
# 在某个容器中执行命令，进入命令行
docker-compose exec web sh
```

### 配置包含egg+mysql+adminer的docker-compose.yml

```
version: 1.0
services:
	web:
		build: .
		restart: always
		volumes:
			- .:/myapp
		ports: 
			- "7001:7001"
	
	db:
		image: mysql:5.6
		restart: always
		volumes:
			- "db-data:/var/lib/mysql"
		environment: 
			MYSQL_ROOT_PASSWORD: 88888
			MYSQL_DATABASE: app
	
	adminer:
		image: adminer
		restart: always
		ports: 
			-9000:8080

volumes:
	db-data:
```

volumes为了让数据持久化，下一次up时不会丢失数据，restart启动失败后一直重启，因为Web连不上数据库会异常退出，adminer可管理数据库，也可进行数据库的迁移



## 阿里云仓库 https://cr.console.aliyun.com/repository

创建docker仓库：在`容器镜像服务`创建镜像仓库，代码仓库选择本地

```shell
# 登录阿里云Docker Registry，根据仓库地域不同，域名也不同
sudo docker login --username=鹿小圈 registry.cn-beijing.aliyuncs.com

# 从Registry中拉取镜像
sudo docker pull registry.cn-beijing.aliyuncs.com/[命名空间]/[仓库名称]:[镜像版本号]

# 将镜像推送到Registry
# 使用"docker tag"命令重命名镜像，可覆盖上传
sudo docker tag [ImageId] registry.cn-beijing.aliyuncs.com/[命名空间]/[仓库名称]:[镜像版本号]
sudo docker push registry.cn-beijing.aliyuncs.com/[命名空间]/[仓库名称]:[镜像版本号]

# 删除本地，通过镜像名（<仓库名>:<标签>）
docker image rm registry.cn-beijing.aliyuncs.com/[命名空间]/[仓库名称]:[镜像版本号]
```

## Sword构建
本地
```
env=test docker-compose build
sudo docker tag testsuper:v1 registry.cn-beijing.aliyuncs.com/chudao/sword:v1
sudo docker push registry.cn-beijing.aliyuncs.com/chudao/sword:v1
docker rmi $(docker images -f "dangling=true" -q)
```

服务器
```
sudo docker pull registry.cn-beijing.aliyuncs.com/chudao/sword:v1
docker tag registry.cn-beijing.aliyuncs.com/chudao/sword:v1 testsuper:v1
env=test docker-compose up -d
```

## 注意
docker应用的host不能设置为127.0.0.1，设置为0.0.0.0，否则宿主机器无法访问

## 错误
### Cannot start service xxx: oci runtime error: container_linux.go:235:
yum update