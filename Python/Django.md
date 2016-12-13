[TOC]
# Django
> Django 中提供了开发网站经常用到的模块，常见的代码都为你写好了，通过减少重复的代码，Django 使你能够专注于 web 应用上有 趣的关键性的东西。为了达到这个目标，Django 提供了通用Web开发模式的高度抽象，提供了频繁进行的编程作业的快速解决方法，以及为“如何解决问题”提供了清晰明了的约定。Django的理念是DRY(Don't Repeat Yourself)来鼓励快速开发！

## 让我们一览 Django 全貌
* **urls.py**
网址入口，关联到对应的views.py中的一个函数（或者generic类），访问网址就对应一个函数。
* **views.py**
处理用户发出的请求，从urls.py中对应过来, 通过渲染templates中的网页可以将显示内容，比如登陆后的用户名，用户请求的数据，输出到网页。
* models.py
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
 
### 为Python3.5安装
（mac自带2.6 、2.7、3.4、3.5版本的Python，默认2.7）
执行完上面的步骤后
进入 /Library/Frameworks/Python.framework/Versions/2.7/lib/python2.7/site-packages/
找到django  和 Django-1.8.6.dist-info 两个目录 复制到
/Library/Frameworks/Python.framework/Versions/3.5/lib/python3.5/site-packages/
ok

## Linux：
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
	# python3 manage.py makemigrations
	# python3 manage.py migrate
	```
	注意：Django 1.7.0及以下的版本需要用以下命令
	
	```
	# python manage.py syncdb
	```
	
	这种方法可以创建表，当你在models.py中新增了类时，运行它就可以自动在数据库中创建表了，不用手动创建。
	备注：对已有的 models 进行修改，Django 1.7之前的版本的Django都是无法自动更改表结构的，不过有第三方工具 south,详见 Django 数据库迁移一节。
4. 使用开发服务器
5. 
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

# 开始
## 第一个网页
在http协议中可以看到，网络服务器是“请求-回应”的工作模式。客户向URL发送请求，服务器根据请求，开动后厨，并最终为客人上菜。Django采用的MVC结构，即点单、厨房、储藏室分离。

我们需要一个指挥员，将URL对应分配给某个对象处理，这需要在live/live下的urls.py设定。Python会根据该程序，将URL请求分给某个厨师。

```
live
├── manage.py
└── live
    ├── __init__.py
    ├── settings.py
    ├── urls.py
    └── wsgi.py

1 directory, 5 files
```

将urls.py修改为:
```python
from django.conf.urls import patterns, include, url

from django.contrib import admin
admin.autodiscover()

urlpatterns = patterns('',
	url(r'^admin/', include(admin.site.urls)),
	# 正则匹配url, 将url交给一个对象处理
	url(r'^$', 'live.view.home_page'),
)
```

我们添加了最后一行。它将根目录的URL分配给一个对象进行处理，这个对象是live.views.first_page。
用以处理HTTP请求的这一对象还不存在，我们在live/live下创建views.py，并在其中定义home_page函数:

```python
# -*- coding: utf-8 -*-

from django.http import HttpResponse

def first_page(request):
    return HttpResponse("<p>世界好</p>")
```

第一行说明字符编码为utf-8，为下面使用中文做准备。home_page函数的功能，是返回http回复，即这里的\<p>世界好\</p>。home_page有一个参数request，该参数包含有请求的具体信息，比如请求的类型等，这里并没有用到。

## 增加app
一个网站可能有多个功能。我们可以在Django下，以app为单位，模块化的管理，而不是将所有的东西都丢到一个文件夹中。在mysite下，运行manange.py，创建新的app：
$python3 manage.py startapp user
 
我们的根目录下，出现了一个新的叫做user的文件夹。

```
live/
├── manage.py
├── live
│   ├── __init__.py
│   ├── __init__.pyc
│   ├── settings.py
│   ├── settings.pyc
│   ├── urls.py
│   ├── views.py
│   └── wsgi.py
└── user
    ├── admin.py
    ├── __init__.py
    ├── models.py
    ├── tests.py
    └── views.py
```

我们还需要修改项目设置，说明我们要使用user。在live/setting.py中，在INSTALLED_APPS中，增加"user"：

```python
INSTALLED_APPS = (
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'user',
)
```

可以看到，除了新增加的user，Django已经默认加载了一些功能性的app，比如用户验证、会话管理、显示静态文件等。我们将在以后讲解它们的用途。
 
## 增加APP页面
我们下面为APP增加首页。我们之前是在live/urls.py中设置的URL访问对象。依然采用类似的方式设置。
另一方面，为了去耦合，实现模块化，我们应该在user/urls.py中设置URL访问对象。具体如下：
 
首先，修改live/urls.py：

```
from django.conf.urls import include, url
from django.contrib import admin
from live import view as live_views

urlpatterns = [
	url(r'^admin/', include(admin.site.urls)),
	url(r'^$', live_views.home_page),
	# 对于 user 的访问, 要参考 user/urls
	url(r'^user/', include('user.urls'))
]
```
 
随后，我们创建user/urls.py，添加内容：

```python
from django.conf.urls import patterns, include, url
from user import views

urlpatterns = patterns('',
    url(r'^$', views.home_page)
)

```

将URL对应user下，views.py中的home_page函数。
 
最后，在user下，修改views.py为:

```python
# -*- coding: utf-8 -*-

from django.http import HttpResponse

def first_page(request):
    return HttpResponse("<p>用户</p>")
```
访问http://127.0.0.1:8000/user 查看效果。
 
# 模型（数据库）
## 连接数据库
Django为多种数据库后台提供了统一的调用API。根据需求不同，Django可以选择不同的数据库后台。MySQL算是最常用的数据库。我们这里将Django和MySQL连接。

在settings.py中，DATABASES可以设置数据库，默认是项目目录下的db.sqlite3，也可以使用其他数据库，如果使用mysql：

```
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': '数据库名',
        'USER': 'user',
        'PASSWORD': 'password',
        'HOST':'localhost',
        'PORT':'3306',
    }
}
```
 
## 创建模型（建表）
> 在Django的帮助下，我们不用直接编写SQL语句。Django将关系型的表(table)转换成为一个类(class)。而每个记录(record)是该类下的一个对象(object)。我们可以使用基于对象的方法，来操纵关系型的MySQL数据库。
在传统的MySQL中，数据模型是表。在Django下，一个表为一个类。表的每一列是该类的一个属性。

>  每个表都是一个模型Model，是定义在django.db.models.fields里面，但为了使用方便，它们被导入到 django.db.models中；标准上，我们导入from django.db import models，然后使用 models.\<Foo>Field的形式定义字段。

### 字段类型 （Field types）
* AutoField 自增字段，一个根据实际ID自动增长的IntegerField . 你通常不需要直接使用;如果不指定,一个主键字段将自动添加到你创建的模型中
* BooleanField 布尔字段，如果你需要设置null 值，则使用NullBooleanField 来代替BooleanField。如果Field.default没有指定的话， BooleanField 的默认值是 None。
* IntegerField
* DecimalField 用python中 Decimal 的一个实例来表示十进制浮点数
	* max_digits：必须参数，位数总数，包括小数点后的位数。该值必须大于等于decimal_places.
	* decimal_places：必须参数，小数点后的数字数量
* FloatField 使用的是Python内部的 float 类型, 而DecimalField 使用的是Python的 Decimal 类型
* EmailField 一个CharField 用来检查输入的email地址是否合法。它使用 EmailValidator 来验证输入合法性。
* TextField 大段文字，不用会限制长度
* CharField 
	* max_length 必须参数
* URLField 如果不指定max_length，则使用默认值200。
* DateField 使用Python的datetime.date实例表示的日期  
	* auto_now：可选参数，每次保存对象时，自动设置该字段为当前时间。总是保存为当前日期，不可自己设置
	* auto_now_add：可选参数，当被创建时候保存当前日期
	* auto_now_add, auto_now, and default 这些设置是相互排斥的. 他们之间的任何组合将会发生错误的结果
* DateTimeField 它是通过Python datetime.datetime实例表示的日期和时间. 携带了跟DateField一样的额外参数
* DurationField 用作存储一段时间的字段类型 - 类似Python中的timedelta. 
* TimeField 时间字段，和Python中 datetime.time 一样

### 字段选项(Field options):

* primary_key=True 设置为主键,如果没有主键,会自动创建一个AutoField作为主键
* max_length=20 char的最大尺寸
* unique=True 唯一, 默认False
* null=True 可以保存空值, 保存为null, 默认False。如果你希望BooleanField 接受null 值，请用 NullBooleanField 代替。
* blank=True 该字段允许为空白, 默认False, 与null不同。null 纯粹是数据库范畴的概念，而blank 是数据验证范畴的。如果字段设置blank=True，表单验证时将允许输入空值。如果字段设置blank=False，则该字段为必填。
* defalut 默认值
* choices  
	任何可迭代的对象，不仅仅是列表或元组（也可自己构建），用来给这个字段提供选择项。如果设置了 choices ，默认表格样式就会显示选择框，选项就是 choices 中的元组。如果直接插入其他值也可以，数据库不会报错，choices的作用只是限制网页选择
	```python
	from django.db import models
	class Student(models.Model):
	# 定义成变量是为了可以在外部用过Student.FRESHMAN来访问 
    FRESHMAN = 'FR'
    JUNIOR = 'JR'
    YEAR_IN_SCHOOL_CHOICES = (
        (FRESHMAN, 'Freshman'), # Freshman 只起描述作用，真正保存的值是FR
        (JUNIOR, 'Junior'),
    )
    year_in_school = models.CharField(
    	max_length=2, 
    	choices=YEAR_IN_SCHOOL_CHOICES, 
    	default=FRESHMAN
    )

    def is_upperclass(self):
        return self.year_in_school in (self.JUNIOR, self.FRESHMAN)
	```
	你也可以归类可选的choices到已命名的组中用来达成组织整理的目的:
	```python
	MEDIA_CHOICES = (
		('Audio', (('vinyl', 'Vinyl'), ('cd', 'CD'))),
    	('Video', (('vhs', 'VHS Tape'), ('dvd', 'DVD'))),
    	('unknown', 'Unknown'),
	)
	```
	每个元组的第一个元素是组的名字。第二个元素是一组可迭代的二元元组，每一个二元元组包含一个值和一个给人看的名字构成一个选项。分组的选项可能会和未分组的选项合在同一个list中。 （就像例中的unknown选项）。

### 外键 
* ForeignKey 一对多
	* 一个表可以被多个用户使用
	* 反向索引（通过Field得到Model）得到QuerySet
	* 直接用等于号设置
* OneToOneField 一对一 
	* 一个表只属于一个用户
	* 和ForeignKey的区别就是，OneToOne等于ForeignKey加上unique=True属性
	* 反向索引得到Model
	* 反向索引得到一个唯一的Model，直接接用等于号设置
* ManyToManyField 多对多 
	* 多个表属于多个用户
	* 反向索引得到QuerySet
	* 通过add设置，在add前需要两个Model都save过
	* 不会显示在该表中，会放在一个新的关系表

```python
class Info(model.Model):
	pass
class Collect(models.Model):
	# 与内部类建立外键，Info需要写在上面
	user_info = models.ForeignKey(Info)
	# 如果类不知道Info，就加上引号
	user_info = models.OneToOneField('Info')
	# 与外部model建立ManyToMany
	room_info = models.ManyToManyField('room.Info')
	
# 查询
collect = Collect.objects.get(id=1)
info = Info.objects.filter(collect=collect)

collect_id = Collect.objects.get(id=1).id
info = Info.objects.filter(collect__id=collect_id)

# 查询ManyToMany
collect = Collect.objects.get(id=1) 
room_infos = collect.room_info.all() 
```
### 创建
在user/models.py中，创建一个表，即只有一个属性的类：

```python
class Info(models.Model):
	name = models.CharField(max_length=30)
	age = models.IntegerField()
	
	def __unicode__(self):
		return self.name
```

类Info定义了数据模型，它需要继承自models.Model。在MySQL中，这个类实际上是一个表。列为name、age。可以看到，name属性是字符类型，最大长度为30。
类Info有一个__unicode__()方法，用来说明对象的字符表达方式。如果是Python 3，定义__str__()方法，实现相同的功能。
 
命令Django同步数据库。Django根据models.py中描述的数据模型，在MySQL中真正的创建各个关系表：

```
# python3 manage.py makemigrations
# python3 manage.py migrate
```
注意：Django 1.7.0及以下的版本需要用以下命令

```
# python manage.py syncdb
```

同步数据库后，Django将建立相关的MySQL表格，并要求你创建一个超级用户

创建成功后，查看db.sqlite3，看到多了一个表`user_info`，是因为在user目录下创建的表，表中有自增的id主键

## 增
```python
from user.models import Info
# 1
Info.objects.create(name='11', password='haha', gender=Info.MALE)
# 2
info = Info(name='1') # 如果age不可为空，即使初始化时age为空也不会错，在save之前，不会对数据库进行操作
info.age = 3
info["age"] = 3 # 错误
setattr(info, "age", 3) # 正确
info.save()
# 3 查询或者创建，返回一个元组,第一个为Info对象, 第二个为True或False, 新建时返回的是True, 已经存在时返回False。速度较慢
Info.objects.get_or_create(name='1')

```

## 查  

```python
# 查询所有
Info.objects.all()
# 查询前100
Info.objects.all()[: 100]
Info.objects.all()[0: 100]
# 查询最后100个
Info.objects.all()[-10:] # 会报错！！！
Info.objects.all().reverse()[:100] # 最后100条
Info.objects.all().reverse()[0] # 最后一条
# 条件查询
Info.objects.filter(name='2')
# 包含 模糊查询 where name like '%2%'
Info.objects.filter(name__contains='2')
# 不区分大小写
Info.objects.filter(name__iexact='abc')
# 包含且不区分大小写
Info.objects.filter(name__icontains='2')
# 正则查询
Info.objects.filter(name__regex="^abc")
# 正则且不区分大小写
Info.objects.filter(name__iregex="^abc")

# 排除 排除包含 2 的Person对象
Info.objects.exclude(name__contains="2") 
# 查询后排除
Info.objects.filter(name__contains="2").exclude(age=23)

# TODO 多表查询
```
以上都会返回QuerySet对象

```python
# 查询一条, 如果有多个就报错
# get得到的是具体的Model，因为只会得到固定的一条数据
Info.objects.get(name='1')
```

### QuerySet
> 从数据库中查询出来的结果一般是一个集合，这个集合叫做 QuerySet

方法：
* defer 排除不需要的字段
* only 仅选择需要的字段
* distinct 去重，一般用于多表查询后结果去重
* values_list 获取元组形式结果
* values 获取字典形式的结果
`values`和`values_list`返回的并不是真正的列表或字典，也是 queryset，他们也是 lazy evaluation 的（惰性评估，通俗地说，就是用的时候才真正的去数据库查） 

### 查询到的结果转换为JSON
```python
# all或者filter得到的QuerySet转换为JSON，使用django内置的serializers，但是输出的是带有数据库信息的数据，并且对于复杂的格式无法转换
from django.core import serializers
obj = Info.objects.all()
json = serializers.serialize('json', obj)

def qs_to_list(queryset):
    """
    QuerySet转换为list
    """
    arr = list()
    for model in queryset:
        arr.append(model_to_dict(model))
    return arr


def model_to_dict(model):
    """
    Mode转换为dict
    """
    fields = []
    for field in model._meta.fields:
        fields.append(field.name)

    dic = {}
    for name in fields:
        dic[name] = field_to_var(getattr(model, name))

    return dic


def field_to_var(field):
    """
    Field转换为普通变量
    """
    import datetime
    from decimal import Decimal
    from django.db.models import Model

    # 处理datetime
    if isinstance(field, datetime.datetime):
        return field.strftime('%Y-%m-%d %H:%M:%S')
    # 处理date
    elif isinstance(field, datetime.date):
        return field.strftime('%Y-%m-%d')
    # 处理Model
    elif isinstance(field, Model):
        return model_to_dict(field)
    # 处理Decimal
    elif isinstance(field, Decimal):
        return float(field)  # 或者str()
    else:
        return field
```

## 改

```python
# 修改queryset中所有值
Info.objects.filter(name='2').update(name='5')

# 直接修改某个model
info = Info.objects.get(id=1)
info.name = "new name"
info.save()

info = Info(id=1, price=33)
info.save()
```

## 删

```python
# 删除一条记录
Info.objects.get(name='chris_unique').delete()  
# 删除多条数据  
Info.objects.filter(name='chris').delete()  
```

## 排序

```python
# 排序
Info.objects.order_by('name')
# 查询 + 逆向排序
Info.objects.filter(name='2').order_by('-name')
```

# 调试
## 输出
1. 使用print
	但是print是在子线程进行的, 可能接收不到输出，使用下面的命令，缺点是每次修改代码都需要手动重启服务器
	
	```
	python manage.py runserver --noreload
	```
2. 使用logging
	在setting.py中配置
	
	```python
	LOGGING = {
	    'version': 1,
	    'disable_existing_loggers': False,
	    'formatters': {
	        'simple': {
	            'format': '%(levelname)s %(message)s'
	        },
	    },
	    'handlers': {
	        'console': {
	            'level': 'DEBUG',
	            'class': 'logging.StreamHandler',
	            'formatter': 'simple'
	        },
	        'mail_admins': {
	            'level': 'ERROR',
	            'class': 'django.utils.log.AdminEmailHandler'
	        }
	    },
	    'loggers': {
	        'django.request': {
	            'handlers': ['mail_admins'],
	            'level': 'ERROR',
	            'propagate': True,
	        },
	        'mylogger': {
	            'handlers': ['console', ],
	            'level': 'DEBUG'
	        }
	    }
	}	
	```
	在需要输出的地方：
	
	```python
	import logging
	logging = logging.getLogger('django')
	logging.debug("debug信息")
	```

# 网络请求
在url.py中匹配网址

```python
from food import views as food_views
...
# ?P<id> 传递额外参数，在food_views.detail中必须有这个参数名
url(r'^food/(?P<id>[0-9]+)/$', food_views.detail),
```
在food/views.js中添加detail方法

```python
# 例如访问 food/1/  id 就是
def detail(request, id):
	# 区分请求方式
	if request.method == 'GET':
		# 得到get请求的某个参数, rest api一般不需要在get请求中传参数
		request.GET.get('key')
		return ...
	elif request.method == 'POST':
		# 获取post请求中的某个参数，但是这种方式只能得到通过表单POST的数据
		request.POST.get('key')
		# 要获取请的JSON数据，就要从body中获取（get请求不能有body）
		body = request.body
		# 得到类似b'{"title":"ccsdsafda","x_scale":0.3,"y_scale":0.5}'，它是一个btye类型的字符串，可以使用simplejson转化为python序列对象（json模块无法进行转换）
		import simplejson
		dic = simplejson.loads(body)
		return ...

```


