# JS调用原生view
```objective-c
// iOS
// WebImageManager.h
#import "RCTViewManager.h"
@interface WebImageManager : RCTViewManager
@end

// WebImageManager.m
#import "WebImageManager.h"
#import "WebImage.h"
@implementation WebImageManager
RCT_EXPORT_MODULE()
// 供外部调用的参数，可直接修改-(UIView *)view中返回view的参数
// 例：修改url，会直接调用WebImage中的setUrl方法
RCT_EXPORT_VIEW_PROPERTY(url, NSString)
- (UIView *)view{
  return [[WebImage alloc] init];
}
// 放到主线程来更新UI
- (dispatch_queue_t)methodQueue {
	return dispatch_get_main_queue();
}

// WebImage.h
#import <UIKit/UIKit.h>
@interface WebImage : UIView
@property(strong, nonatomic) NSString *url;
@end

// WebImage.m
#import "WebImage.h"
#import "UIImageView+WebCache.h"
#import "UIView+CSFrame.h" // UIView+CSFrame 在本目录下

// 如果想设置圆角，在js的css中设置overflow: 'hidden'
@interface WebImage ()
@property(strong,nonatomic)UIImageView *imv;
@property(strong,nonatomic)UIImage *showIm;

@end

@implementation WebImage

- (instancetype)init
{
  self = [super init];
  if (self) {
    self.imv = [[UIImageView alloc]init];
    self.imv.contentMode = UIViewContentModeScaleAspectFill;
    [self addSubview:self.imv];
  }
  return self;
}

- (void)layoutSubviews{
  [super layoutSubviews];
  [self layout];
}

- (void)layout{
  CGFloat height = self.bounds.size.height;
  CGFloat width = self.bounds.size.width;

  self.imv.frame = CGRectMake(0, 0, width, height);
}

-(void)setUrl:(NSString *)url
{
  _url = url;
  if([url hasPrefix:@"http"]){
    [self.imv sd_setImageWithURL:[NSURL URLWithString:url] placeholderImage:[UIImage imageNamed:@"placeholder_image"] completed:^(UIImage * _Nullable image, NSError * _Nullable error, SDImageCacheType cacheType, NSURL * _Nullable imageURL) {
      [self layout];
    }];

  }else{
    [self.imv setImage:[UIImage imageWithContentsOfFile:url]];
    [self layer];
  }

}

```

```java
// Android
// ViewPackage.java
import com.facebook.react.ReactPackage;
import com.facebook.react.bridge.JavaScriptModule;
import com.facebook.react.bridge.NativeModule;
import com.facebook.react.bridge.ReactApplicationContext;
import java.util.ArrayList;
import java.util.Arrays;
import java.util.Collections;
import java.util.List;

public class ViewPackage implements ReactPackage {
    @Override
    public List<NativeModule> createNativeModules(ReactApplicationContext reactContext) {
        return Collections.emptyList();
    }
    @Override
    public List<Class<? extends JavaScriptModule>> createJSModules() {
        return Collections.emptyList();
  }
    @Override
    public List<ViewManager> createViewManagers(ReactApplicationContext reactContext) {
        List<ViewManager> viewManagerList = new ArrayList<>();
				// 可以添加多个viewManager
        viewManagerList.add(new WebImageManager());
        return viewManagerList;
    }
}

// WebImageManager.java
import com.facebook.react.uimanager.annotations.ReactProp;
import com.facebook.react.uimanager.ThemedReactContext;
import com.facebook.react.uimanager.ViewGroupManager;

public class WebImageManager extends ViewGroupManager<WebImage> {
    @Override
    public String getName() {
        return "WebImage";
    }

    @Override
    protected WebImage createViewInstance(ThemedReactContext reactContext) {
        return new WebImage(reactContext);
    }

    @ReactProp(name = "url")
    // 返回值必须是void
    public void setUrl(WebImage view, String url) {
        view.setUrl(url);
    }
}

// WebImage.java
import android.content.Context;
import android.graphics.Bitmap;
import android.view.Display;
import android.view.View;
import android.view.ViewGroup;
import android.widget.ImageView;
import android.widget.RelativeLayout;

import com.nostra13.universalimageloader.core.DisplayImageOptions;
import com.nostra13.universalimageloader.core.ImageLoader;
import com.nostra13.universalimageloader.core.ImageLoaderConfiguration;
import com.nostra13.universalimageloader.core.assist.ImageSize;
import com.nostra13.universalimageloader.core.download.ImageDownloader;
import com.nostra13.universalimageloader.core.listener.SimpleImageLoadingListener;

import javax.xml.validation.Schema;

public class WebImage extends ViewGroup{

    private ImageView imageView;

    public WebImage(Context context) {
        super(context);
        this.imageView = new ImageView(context);
        RelativeLayout.LayoutParams params = new RelativeLayout.LayoutParams(LayoutParams.MATCH_PARENT, LayoutParams.MATCH_PARENT);
        params.addRule(RelativeLayout.ALIGN_PARENT_TOP);
        params.addRule(RelativeLayout.ALIGN_PARENT_RIGHT);
        imageView.setLayoutParams(params);
        addView(imageView);

        ImageLoaderConfiguration configuration = ImageLoaderConfiguration.createDefault(context);
        ImageLoader.getInstance().init(configuration);
    }

    public void setUrl(String url) {
        if (!url.contains("http")) {
            // 没有http, 设置为本地图片url
            url = ImageDownloader.Scheme.FILE.wrap(url);
        }

        DisplayImageOptions options = new DisplayImageOptions.Builder()
                .showImageOnLoading(R.drawable.placeholder_image)
                .cacheInMemory(true)
                .cacheOnDisk(true)
                .build();
        ImageLoader.getInstance().displayImage(url, imageView, options);
    }

    @Override
    protected void onLayout(boolean changed, int l, int t, int r, int b) {
        int count = getChildCount();
        int prevChildRight = 0;
        int prevChildBottom = 0;
        for (int i = 0; i < count; i++) {
            final View child = getChildAt(i);
            child.layout(prevChildRight, prevChildBottom,
                    prevChildRight + child.getMeasuredWidth(),
                    prevChildBottom + child.getMeasuredHeight());
            prevChildRight += child.getMeasuredWidth();
        }
    }

    @Override
    protected void onMeasure(int widthMeasureSpec, int heightMeasureSpec) {
        super.onMeasure(widthMeasureSpec, heightMeasureSpec);
        int count = getChildCount();
        for (int i = 0; i < count; i++) {
            final View child = getChildAt(i);
            measureChild(child, widthMeasureSpec, heightMeasureSpec);
        }
    }
}

// 在MainApplication的getPackages中添加
new ViewPackage()
```

```javascript
// JavaScript
import requireNativeComponent from 'react-native'
varDemoView=requireNativeComponent('WebImage',null); // 必须去掉Manager, 否则得不到View

<WebImage url={'http://'}/>
```
