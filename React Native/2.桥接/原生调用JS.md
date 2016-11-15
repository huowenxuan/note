##Native调用JS
Native调用JS通过发送通知来实现
```objective-c
// iOS
// DemoModuleEvent.h
#import "RCTBridgeModule.h"
#import "RCTEventEmitter.h"

@interface DemoModuleEvent : RCTEventEmitter <RCTBridgeModule>
-(void)sendEvent:(NSDictionary *)msgDic;
@end

// DemoModuleEvent.m
#import "DemoModuleEvent.h"
#import "RCTBridge.h"

@interface DemoModuleEvent()
@property(copy,nonatomic) RCTResponseSenderBlock senderBlock;
@end

@implementation DemoModuleEvent
RCT_EXPORT_MODULE();
// 单例
+ (id)allocWithZone:(NSZone *)zone {
  static DemoModuleEvent *sharedInstance = nil;
  static dispatch_once_t onceToken;
  dispatch_once(&onceToken, ^{
    sharedInstance = [super allocWithZone:zone];
  });
  return sharedInstance;
}

RCT_EXPORT_METHOD(callbackMessage: (NSString *)type) {
  self.senderBlock = callback;
}

- (NSArray<NSString *> *)supportedEvents {
  return @[@"nativeNotification"];
}

// 外部调用该方法来给JS端发送通知
-(void)sendEvent:(NSDictionary *)msgDic {
  [self sendEventWithName:@"nativeNotification" body:msgDic];
}

@end
```

```java
// TODO Android
```

```javascript
// javascript
import {
  NativeEventEmitter,
  NativeModules
} from 'react-native'
const DemoModuleEvent = new NativeEventEmitter(NativeModules.DemoModuleEvent);
DemoModuleEvent.addListener('nativeNotification', (msgDic) => {
  console.log(msgDic);
});

```
