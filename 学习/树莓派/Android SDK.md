cd /home/pi/dev
wget http://dl.google.com/android/android-sdk_r24.4.1-linux.tgz
tar xzf android-sdk_r24.4.1-linux.tgz
rm -rf android-sdk_r24.4.1-linux.tgz

nano /etc/profile
最后添加：
export ANDROID_HOME=/home/pi/dev/android-sdk-linux
export PATH=${PATH}:${ANDROID_HOME}/tools:${ANDROID_HOME}/platform-tools

source /etc/profile

sudo mkdir /home/pi/dev/android-sdk-linux/tools/lib/arm

android update sdk --no-ui # 安装工具，这一步不需要执行完，在android-sdk-linux/下创建了一个platform-tools目录即可，只需要用到里面的adb，但是此时创建的adb是不可识别的二进制文件，因为是下载的位数（或Linux系统）不同（难点就在于此，找不到合适的SDK系统和版本）。解决方法>>>

sudo apt-get install android-tools-adb # 使用apt安装adb，会在/usr/bin中生成一个adb的可执行文件，将这个文件复制到platform-tools/下即可（系统会从ANDROID_HOME中去查找adb，所以直接安装adb是不能通过android SDK来使用的，会造成一系列问题：Adb not found in $ANDROID_HOME path. adb not working...）

cp /usr/bin/adb /home/pi/dev/android-sdk-linux/platform-tools/adb