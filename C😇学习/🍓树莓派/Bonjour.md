# Bonjour
用于自动发现网络上的设备，可实现局域网上的自动域名解析，同一局域网下可以使用主机名.local的形式，找到对应的ip地址

树莓派的默认主机名是respberrypi
ssh pi@respberrypi.local

如果局域网有多个相同的名字，会命名为           
respberrypi
respberrypi-2
respberrypi-3

改名：在respi-config中，选择 7 Advanced Options -> A2 Hostname。更改后重启

在mac下，可用下面的命令查询IP
dns-sd -q respberrypi.local