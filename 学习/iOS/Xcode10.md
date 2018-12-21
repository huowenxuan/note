---
title: Xcode10
---

在Xcode10上运行新旧项目

1. 报错`Build input file cannot be found: '/.../node_modules/react-native/Libraries/WebSocket/libfishhook.a'`
Xcode中Libraries->RCTWebSocket->TARGETS RCTWebSocket->BuildPhases->Link Binary With Libraries->删掉libfishhook.a再重新导入
2. 报错`That command depends on command in Target : script phase “[CP] Copy Pods Resources”`
Xcode中File->Workspace Settings->Build System改为Legacy Build System（由新的构建方式改为旧的）
3. 报错`library not found for -lstdc++.6.0.9`
libstdc++几年前就被废弃，在Xcode10中正式被删除，用libc++代替即可
1. 重新yarn install后报错`'config.h' file not found`。
    
    ```
    sudo xcode-select -s /Applications/Xcode-beta.app/Contents/Developer
    cd ./node_modules/react-native/third-party/glog-0.3.4 && ../../scripts/ios-configure-glog.sh && cd ../../../../
    ```
                      