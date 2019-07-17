# Python
## 安装opencv
使用 pip3 install opencv-python。import cv2后报错 ` libcblas.so.3: cannot open shared object file: No such file or directory`

按照网上的教程依次执行下面的命令，需要安装依赖就安装依赖

pip3 install opencv-contrib-python==3.3.0.9 -i https://www.piwheels.org/simple # 安裝3309版本
sudo apt-get update #安裝依賴庫
sudo apt-get install libhdf5-dev
sudo apt-get install libatlas-base-dev
sudo apt-get install libjasper-dev
sudo apt-get install libqt4-test
sudo apt-get install libqtgui4
sudo apt-get update

一直报错`ImportError: libhdf5_serial.so.100: cannot open shared object file: No such file`

然后重新安装 pip3 install opencv-python 成功