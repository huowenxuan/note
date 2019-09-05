1. 下载 `https://github.com/google/flutter-desktop-embedding`，放在和flutter目录同级的位置
2. cd到flutte，切换到master分支
3. 添加环境变量
    export ENABLE_FLUTTER_DESKTOP=true
4. 执行flutter devices，会下载一些东西，发现多出了macOS设备
5. 在自己的项目中运行，也会下载一些东西（最好拔掉iOS充电设备?）
    flutter run -d macOS
6. 如果失败，把flutter-desktop-embedding/example/macos下面的文件覆盖到自己项目中的macos/下
7. 修改flutter源代码
    packages/flutter/lib/src/foundation/_platform_io.dart
    ```
    platform.TargetPlatform result;
    if (Platform.isIOS) {
    ...
    // 加入以下两行
    } else if (Platform.isMacOS) {
      result = platform.TargetPlatform.iOS;
    }
    ```
8. build
    flutter build macos
    Xcode -> Archive -> Distribute App -> Copy App
    
## 错误
### run -d macOS 时报错 PhaseScriptExecution [CP]\ Embed\ Pods\ Frameworks

cd macos
pod install