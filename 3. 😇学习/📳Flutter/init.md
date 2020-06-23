## 执行无反应，需要设置镜像

或者报错  SSL: no alternative certificate subject name matches target host name 'storage.flutter-io.cn'

每次打开终端都要切换一下镜像

```
export PUB_HOSTED_URL=https://pub.flutter-io.cn
export FLUTTER_STORAGE_BASE_URL=https://storage.flutter-io.cn
```

## 命令

```
flutter doctor
flutter upgrade
flutter pub get
```

## 环境变量

```
open ~/.bash_profile
// 添加
export PATH="/Users/huowenxuan/dev/flutter/bin:$PATH"
export PUB_HOSTED_URL=https://pub.flutter-io.cn
export FLUTTER_STORAGE_BASE_URL=https://storage.flutter-io.cn
// 生效
source ~/.bash_profile
```
## 让当前执行的命令停止

killall -9 dart