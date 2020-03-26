## 安装Docker
curl -fsSL get.docker.com -o get-docker.sh
sudo sh get-docker.sh --mirror Aliyun

建立 docker 组：
sudo groupadd docker
将当前用户加入 docker 组：
sudo usermod -aG docker pi

## 报错`exec user process caused “exec format error”`
Arm架构需要安装
docker pull armhf/debian

## 安装docker-compose
ARM架构使用pip
sudo pip3 install docker-compose

## x86机器为arm构建docker image

Mac
在https://github.com/multiarch/qemu-user-static/releases，找到qemu-arm-static

```
curl -L -o qemu-arm-static.tar.gz https://github.com/multiarch/qemu-user-static/releases/download/v4.0.0-5/qemu-arm-static.tar.gz
tar xzf qemu-arm-static.tar.gz 
sudo 

# 让docker内核可以理解 ARM ELF 文件
docker run --rm --privileged multiarch/qemu-user-static:register
```

docker run --rm -v /Users/huowenxuan/Desktop/qemu-arm-static:/usr/bin/qemu-arm-static arm32v7/python:3.6.5-slim-stretch qemu-arm-static /usr/local/bin/python3.6 -V

