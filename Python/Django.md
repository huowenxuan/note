[TOC]
# Django
> Django 中提供了开发网站经常用到的模块，常见的代码都为你写好了，通过减少重复的代码，Django 使你能够专注于 web 应用上有 趣的关键性的东西。为了达到这个目标，Django 提供了通用Web开发模式的高度抽象，提供了频繁进行的编程作业的快速解决方法，以及为“如何解决问题”提供了清晰明了的约定。Django的理念是DRY(Don't Repeat Yourself)来鼓励快速开发！

## 让我们一览 Django 全貌
**urls.py**  
网址入口，关联到对应的views.py中的一个函数（或者generic类），访问网址就对应一个函数。
* **views.py**
处理用户发出的请求，从urls.py中对应过来, 通过渲染templates中的网页可以将显示内容，比如登陆后的用户名，用户请求的数据，输出到网页。
models.py
与数据库操作相关，存入或读取数据时用到这个，当然用不到数据库的时候 你可以不使用。
* **forms.py**  
表单，用户在浏览器上输入数据提交，对数据的验证工作以及输入框的生成等工作，当然你也可以不使用。templates 文件夹views.py 中的函数渲染templates中的Html模板，得到动态内容的网页，当然可以用缓存来提高速度。
* **admin.py**  
后台，可以用很少量的代码就拥有一个强大的后台。
* **settings.py**  
Django 的设置，配置文件，比如 DEBUG 的开关，静态文件的位置等。

# 环境搭建
## MAC：
### 为默认版本安装
下载： https://www.djangoproject.com/download/
下载Django-1.8.6.tar.gz，解压得到Django-1.8.6
终端cd进Django-1.8.6目录
```
# cd /Users/Huo/Downloads/Django-1.8.6
```
运行安装文件
```
# sudo INSTALL 
```
打开python
```
# python
```
 
查看版本号：如果出现，就说明安装成功
```
>>> import django
>>> django.VERSION
(1, 8, 6, 'final', 0)
>>> django.get_version()
'1.8.6'
```
 
下载pip： https://pip.pypa.io/en/latest/installing/  找到get-pip.py，右键直接下载
cd进入get-pip.py的目录，使用python安装pip：（必须为系统默认的python位置放置django的的两个文件，否则运行会出错）
```
# python get-pip.py 
```
使用pip安装django
```
# pip install Django
```
会自动下载安装
 
输入django-admin
成功则说明安装成功
 
###为Python3.5安装
（mac自带2.6 、2.7、3.4、3.5版本的Python，默认2.7）
执行完上面的步骤后
进入 /Library/Frameworks/Python.framework/Versions/2.7/lib/python2.7/site-packages/
找到django  和 Django-1.8.6.dist-info 两个目录 复制到
/Library/Frameworks/Python.framework/Versions/3.5/lib/python3.5/site-packages/
ok

##Linux：
下载pip：
```
# wget https://bootstrap.pypa.io/get-pip.py
```
按照mac的步骤
 
如果在python3.5 manage.py  runserver时出现No module named _sqlite3错误
解决：
1. 首先安装 sqlite-devel
yum install sqlite-devel
2. 重新编译python
从下载开始
```
# wget https://www.python.org/ftp/python/3.5.0/Python-3.5.0b4.tgz
```
到`make install`，就可以用了
 
# 基本命令
1. 新建一个 django-project 
	一个 project 一般为一个项目
	
	```
	# django-admin.py startproject project-name
	```
2. 新建 app
	一般一个项目有多个app, 当然通用的app也可以在多个项目中使用。
	
	```
	# python manage.py startapp app-name
	# django-admin.py startapp app-name
	```
3. 同步数据库
	```
	# python manage.py makemigrations
	# python manage.py migrate
	```
	注意：Django 1.7.0及以下的版本需要用以下命令
	
	```
	# python manage.py syncdb
	```
	
	这种方法可以创建表，当你在models.py中新增了类时，运行它就可以自动在数据库中创建表了，不用手动创建。
	备注：对已有的 models 进行修改，Django 1.7之前的版本的Django都是无法自动更改表结构的，不过有第三方工具 south,详见 Django 数据库迁移一节。
4. 使用开发服务器
	```
	# python manage.py runserver
	```

	当提示端口被占用的时候，可以用其它端口：
	```
	# python manage.py runserver 8001
	# python manage.py runserver 9999
	```
	
	监听所有可用 ip
	```
	# python manage.py runserver 0.0.0.0:8000
	```
	
	如果是外网或者局域网电脑上可以用其它电脑查看开发服务器
	访问对应的 ip加端口，比如`http://172.16.20.2:8000`
5. 清空数据库
	此命令会询问是 yes 还是 no, 选择 yes 会把数据全部清空掉，只留下空表。
	```
	# python manage.py flush
	```
	
6. 创建超级管理员
	```
	# python manage.py createsuperuser
	```
7. 导出数据 导入数据
	关于数据操作 详见：数据导入数据迁移，现在了解有这个用法就可以了。
	```
	# python manage.py dumpdata appname > appname.json
	# python manage.py loaddata appname.json
	```
8. django 项目环境终端
	```
	# python manage.py shell
	```
	如果你安装了 bpython 或 ipython 会自动用它们的界面，强烈推荐用 bpython
9. 数据库命令行
	```
	# python manage.py dbshell
	```
	Django 会自动进入在settings.py中设置的数据库，如果是 MySQL 或 postgreSQL,会要求输入数据库用户密码。
	在这个终端可以执行数据库的SQL语句。如果您对SQL比较熟悉，可能喜欢这种方式。
10. 更多命令
	终端上输入 `python manage.py` 可以看到详细的列表，在忘记了名称的时候特别有用。




