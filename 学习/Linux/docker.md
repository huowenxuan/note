# Docker
## 命令

```
sudo docker build -t sword .

# 新建并开启一个容器
# sudo docker run -d --net=host  --name sowrd sword
# 只能使用 这种方法将docker7002端口映射到宿主环境的7002
sudo docker run -d  --name sowrd  -p 7002:7002 sword

# 启动一个关闭的容器
docker container start cid
# 关闭一个容器
docker container stop cid

# 重启，使代码生效
docker restart cid

docker ps # 查看运行的容器，获得containerid
docker ps -a  # 查看挂掉的容器

# 追踪log 后面的参数为container id
docker logs -f 75164ca7e7cb

# 停止容器
sudo docker stop containerId

# 删除容器
sudo docker rm containerId

docker image ls
docker image rm imageid

# 查看端口占用
lsof -i:7002

# 进入容器
docker exec -it <name> /bin/bash

# 宿主机重启后自动启动容器
# 前提有两个：
# 宿主机system enable docker。就是说：宿主机开机时，会自动启动docker服务。
# 已经docker start了该container。
docker update --restart=always <name>
docker update --restart=no <name>
```

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
# RUN
# 当前镜像的顶层执行任何命令，并commit成新的（中间）镜像，提交的镜像会在后面继续用到
RUN npm run dev # shell格式，相当于执行/bin/sh -c "<command>"：
RUN ["npm", "run", "dev"] # exec格式，不会触发shell，所以$HOME这样的环境变量无法使用，但它可以在没有bash的镜像中执行，而且可以避免错误的解析命令字符串
RUN ["/bin/bash", "-c", "npm run dev"] # 与shell相同

# CMD
# 一个Dockerfile里只能有一个CMD，如果有多个，只有最后一个生效。CMD指令的主要功能是在build完成后，为了给docker run启动到容器时提供默认命令或参数，这些默认值可以包含可执行的命令，也可以只是参数（此时可执行命令就必须提前在ENTRYPOINT中指定）。
# 同样有以上两种格式
CMD ./node_modules/.bin/egg-scripts start --env=$env --port=7002

```

### 自定义参数
```
# Dockerfile
# FROM写在最前
FROM node:10.10.0

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
以本地的docker-compose.yml构建，指定yml文件使用-f
docker-compose  build
运行，代替docker run。-d 后台运行；如果docker-compose.yml指定了image，并且存在，就直接运行，否则会执行build
docker-compose up -d

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