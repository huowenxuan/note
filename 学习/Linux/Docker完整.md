# Docker
## 容器
## 虚拟机
传统虚拟机技术是虚拟出一套硬件后，在其上运行一个完整操作系统，在该系统上再运行所需应用进程；而容器内的应用进程直接运行于宿主的内核，容器内没有自己的内核，而且也没有进行硬件虚拟。因此容器要比传统虚拟机更为轻便。
## Docker
Docker 在容器的基础上，进行了进一步的封装，从文件系统、网络互联到进程隔离等等，极大的简化了容器的创建和维护。使得 Docker 技术比虚拟机技术更为轻便、快捷

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

## 启动容器
启动容器有两种方式，一种是基于镜像新建一个容器并启动，另外一个是将在终止状态（stopped）的容器重新启动。

新建并启动
所需要的命令主要为 docker run

启动已终止容器
可以利用 docker container start 命令，直接将一个已经终止的容器启动运行

## docker-componse
以本地的docker-compose.yml构建，指定yml文件使用-f
docker-compose  build
运行 -d 后台运行
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
docker-compose -f docker-compose-test.yml build
sudo docker tag testsuper:v1 registry.cn-beijing.aliyuncs.com/chudao/sword:07.22.01-sword
sudo docker push registry.cn-beijing.aliyuncs.com/chudao/sword:07.22.01-sword
docker rmi $(docker images -f "dangling=true" -q)
```

服务器
```
sudo docker pull registry.cn-beijing.aliyuncs.com/chudao/sword:07.22.01-sword
docker tag registry.cn-beijing.aliyuncs.com/chudao/sword:07.22.01-sword testsuper:v1
docker-compose -f docker-compose-test.yml up -d
```