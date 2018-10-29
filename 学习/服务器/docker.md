将代码pull到sword目录，在当前目录下执行一下操作：

```
sudo docker build -t sword .

# 上面的参考文章中说使用host来将端口自动映射到主机，为了使用localhost的 mysql，经测试，这种方法无法访问到服务
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
docker logs -f 5c4916fe88f6

# 停止容器
sudo docker stop containerId

# 删除容器
sudo docker rm containerId

docker image ls
docker image rm imageid

# 查看端口占用
lsof -i:7002
```