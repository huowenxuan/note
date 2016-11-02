# JS调用原生view

JS调用原生View：

iOS:

```objective-c
RCTDemoViewManager.h: 必须命名为Manager
#import <UIKit/UIKit.h>
#import "RCTViewManager.h"
// 继承RCTViewManager
@interface RCTDemoViewManager : RCTViewManager
@end
RCTDemoViewManager.m:
@implementation RCTDemoViewManager
RCT_EXPORT_MODULE();
- (UIView *)view {
// 大小由js控制, 所以如果要调整位置，必须使用layoutSubView, 如果要设置最外层的view的颜色，也必须要在layoutSubView中设置
  UIView * view = [[UIView alloc] init];
  view.backgroundColor = [UIColor redColor];
// 如果是viewController，就调用viewController.view
  return view;
}
@end
```

js:

```javascript
import requireNativeComponent from 'react-native'
varDemoView=requireNativeComponent('RCTDemoView',null); // 必须去掉Manager, 否则得不到View
render(){	
	return <DemoView style={{height:1000,width:1000}}/>
}
```