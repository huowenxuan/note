# 使用脚本安装
curl -fsSL get.docker.com -o get-docker.sh
sudo sh get-docker.sh --mirror Aliyun

建立 docker 组：
sudo groupadd docker
将当前用户加入 docker 组：
sudo usermod -aG docker pi