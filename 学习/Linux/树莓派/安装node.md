# 安装Node
不可以用apt-get，先删除通过apt-get安装的版本

```
sudo apt-get remove node
sudo apt-get remove npm
```

去官网下载https://nodejs.org/en/download/current/
获取 Linux Binaries (ARM)	ARMv7 的下载地址

```
wget https://nodejs.org/dist/v12.5.0/node-v12.5.0-linux-armv7l.tar.xz
tar -xJf node-v12.5.0-linux-armv7l.tar.xz  -C /opt
# 解压到opt
sudo tar -xJf node-v12.5.0-linux-armv7l.tar.xz  -C /opt
# 链接到bin
sudo ln -s /opt/node-v12.5.0-linux-armv7l/bin/node /usr/local/bin/node
sudo ln -s /opt/node-v12.5.0-linux-armv7l/bin/npm /usr/local/bin/npm

# 安装yarn
npm install -g yarn
sudo ln -s /opt/node-v12.5.0-linux-armv7l/lib/node_modules/yarn/bin/yarn.js /usr/local/bin/yarn
```