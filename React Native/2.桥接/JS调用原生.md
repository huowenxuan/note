##JS调用Native

```objective-c
// iOS
// DemoManager.h
#import "RCTBridgeModule.h"
@interface DemoManager : NSObject <RCTBridgeModule>
@end

// DemoManager.m
#import "DemoManager.h"
@implementation DemoManager
// 声明该模块导出到js端调用
RCT_EXPORT_MODULE()
// 声明该方法导出到js端调用
// RCTPromiseResolveBlock和RCTPromiseRejectBlock一起返回一个JS的Promise对象
RCT_EXPORT_METHOD(sendMessageToNative: (NSString *)msg
                  resolver: (RCTPromiseResolveBlock)resolve
                  rejecter: (RCTPromiseRejectBlock)reject) {
  NSLog(@"调用sendMessage方法");
  if (true) {
    resolve(@[@"success"]);
  } else {
    reject(0, @"errorMsg", nil);
  }
}
// 导出常量，每一个key都是一个常量名。可导出的类型见"可桥接的类型.md"
- (NSDictionary *)constantsToExport {
  return @{@"constantName": @"name"}
}
// 可选，声明一个独立的队列来在这里工作，用于耗时的操作
- (dispatch_queue_t)methodQueue {
  return dispatch_queue_create("com.demo", DISPATCH_QUEUE_SERIAL);
}
@end
```

```java
// Android
// DemoPackage.java
import com.facebook.react.ReactPackage;
import com.facebook.react.bridge.JavaScriptModule;
import com.facebook.react.bridge.NativeModule;
import com.facebook.react.bridge.ReactApplicationContext;

import java.util.ArrayList;
import java.util.Collections;
import java.util.List;

public class DemoPackage implements ReactPackage {

    @Override
    // 创建功能类模块
    public List<NativeModule> createNativeModules(ReactApplicationContext reactContext) {
        List<NativeModule> modules = new ArrayList<>();
        modules.add(new DemoManager(reactContext));
        return modules;
    }

    @Override
    public List<Class<? extends JavaScriptModule>> createJSModules() {
        return Collections.emptyList();
    }

    @Override
    // 创建viewManagers
    public List<ViewManager> createViewManagers(ReactApplicationContext reactContext) {
        return Collections.emptyList();
    }

}

// DemoManager.java
import com.facebook.react.bridge.Callback;
import com.facebook.react.bridge.ReactApplicationContext;
import com.facebook.react.bridge.ReactContextBaseJavaModule;
import com.facebook.react.bridge.ReactMethod;

public class DemoManager extends ReactContextBaseJavaModule {
    private static DemoManager instance = null;

    @Override
    public String getName() {
        return "DemoManager";
    }

    public DemoManager(ReactApplicationContext reactContext) {
        super(reactContext);
    }

    @ReactMethod
    // Callback返回JS的Promise对象
    public void sendMessage(String msg, Callback callback) {
      Log.e(msg, 'sendMessage');
      if (true) {
        callback.invoke("success");
      } else {
        callback.reject(0, "errorMeg", null);
      }
    }

    @Override
    // 导出常量
    public Map<String, Object>getConstants() {
      final Map<String, Object> constants = new HashMap();
      constants.put("constantName", "name");
      return constants;
    }
}

// 在MainApplication的getPackages中添加
new DemoPackage()
```

```javascript
// JS
import {
  NativeModules
} from 'react-native'
var DemoManager = NativeModules.DemoManager
DemoManager.sendMessage('调用sendMessage方法')
  .then((msg)=> {})
  .catch((errorMsg)=> {})
DemoManager.constantName // 获取到常量
```
