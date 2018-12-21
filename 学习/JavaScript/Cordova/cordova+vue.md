---
title: cordova+vue
---

## 初始化
使用vue-cli创建基于webpack的项目
> vue init webpack ProjectName

## 合并
生成的build、config、index.html、static、src移动到cordova项目根目录中，node_module不变，合并package.json。

index.html就作为程序入口，src作为项目代码目录  
1. static虽然为空，但是不能删除，vue存放静态资源，webpack也会用到

## 配置cordova
删掉www/下所有文件

## 配置vue
将webpack打包prodution后的index.html以及js文件都自动打包到www/下，供cordova使用

修改config/index.js中的build
> index: path.resolve(__dirname, '../www/index.html'),
> assetsRoot: path.resolve(__dirname, '../www'),
> assetsPublicPath: './', // 从'/'改为'./'，否则在手机上为空白页面


                      