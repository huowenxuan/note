docker集群的前提是可以互相网络连接

```
# 初始化主节点
docker swarm init --advertise-addr xxx.xxx.xxx.xxx # 本机ip，会给出一个token
# 如果只有一台机器直接init
docker swarm init
# 连接主节点
docker swarm join --token xxxxxx xxx.xxx.xxxx.xxx:2377 # 根据上一步token与主节点连接

# docker-compose.yml 
version: '3'
services:
	web: 
		image: mynode
		deploy:
			replicas: 6               # 指定启动6个容器
			resources:
				limits:                 # 对系统资源做限定，每个容器能使用10%的cpu和50M内存
					cpus: "0.1"
					memory: 50M
			update_config:            # 更新策略
				parllelism: 2           # 每组更新2个
				delay: 10s              # 完成后延迟10s再更新下一组
			restart_policy:           # 更新策略
				condition: on-failure   # 条件，失败重启
		ports:
			- "3002:3002"
		networks:
			- webnet
networks:
	- webnet
	
# 集群模式不支持构建镜像，所以只能自己构建，根据Dockerfile
docker build . -t mynode

# 运行 myapp为集群名字
docker stack deploy -c docker-compose.yml myapp

# 查看运行的应用
docker stack services myapp
# 删除
docker stack rm myapp
```

