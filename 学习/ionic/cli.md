### 创建项目

```
ionic start HelloWorld tutorial(模板)
```

查看所有模板：

```
ionic start --list
```
> tutorial：带侧边栏的一个主页、一个可push列表
tabs
blank：空白项目


### 启动本地开发服务器
默认会在浏览器运行、调试。并且热更新

```
ionic serve
```

--consolelogs | -c	输出应用控制台日志
--serverlogs | -s	 输出开发服务器日志
--nobrowser | -b	不启动浏览器
--nolivereload | -d	不使用live reload，默认启用
--browser | -w	
--lab | -l	在不同的屏幕尺寸和平台类型上测试你的应用
--platform | -t	

### 添加运行平台

```
ionic platform add/rm ios/android
```
--noresources|-r	不要添加默认的Ionic图标和启动屏幕资源
--nosave|-e	 不要把平台保存到package.json 文件中


### 运行

在所有连接的设置上运行
```
ionic cordova run
```
--livereload | -l：热更新代码
--consolelogs | -c：向Ionic CLI输出应用控制台日志 (需要livereload)
--serverlogs | -s：向Ionic CLI输出开发服务日志 (需要livereload)
--debug | --release	
--device | --emulator | --target=FOO	

#### 运行android

``` 
ionic cordova run android --devices
```
报错：
`No installed build tools found. Please install the Android build tools`
运行`ionic cordova run android --devices`时候报该错误，原因不知，重新安装android就好了。

删除platforms/android目录，修改platforms/platforms.json文件，删掉android，重新运行

```
ionic cordova  platform add android
ionic cordova run android --devices
```

#### 运行iOS

安装ios-deploy

```
// 正确
sudo npm install --global --unsafe-perm ios-deploy
// 错误，报错：Code signing is required for product type 'Command-line Tool' in SDK 'macOS 10.13'
sudo npm install -g ios-deploy
```

运行：

```
ionic cordova run ios --devices 
```

报错：`Signing for "MyApp" requires a development team. Select a development team in the project editor.`
如果USB插着手机，会装到手机上，需要把USB拔掉。或者打开项目，选择一个开发团队，即可同时运行到真机


### 编译

使用ionic build代替cordova build
```
ionic build ios
ionic build android
```

### 部署项目到模拟器或仿真机

```
ionic cordova emulate ios/android
```

--livereload | -l		
--consolelogs|-c	输出app控制台日志（需要livereload）
--serverlogs|-s	输出开发服务器日志（需要livereload）
--debug | --release	
--device|--emulator|--target=FOO	
### 生成页面和服务

创建页面：

```
# ionic g page <PageName> 
ionic g page myPage 
√ Create app/pages/my-page/my-page.html 
√ Create app/pages/my-page/my-page.ts 
√ Create app/pages/my-page/my-page.scss
```

你可以把page改成provider来创建一个service，会创建一个标准的类，包含一个简单的的http的get请求，使用了Angular的http类。

```
ionic g provider MyData 
√ Create app/providers/my-data/my-data.ts
```



