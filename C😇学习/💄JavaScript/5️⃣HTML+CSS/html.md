[TOC]



避免使用center、font、basefont、s、strike、u标签，align、bgcolor、color属性，使用样式代替

### HTML

* 块元素block独占一行`<h1>~<h6> <p> <div> ol ul hr`，可设置宽高，默认为父级的100%，行内元素inline可以和其他元素位于同一行`strong em u s a span img input`，不能设置宽高，默认宽度为文字宽度
* 加粗尽量用string不用b，更有语义
* 斜体用em，不用i，cite
* 水平线 `<hr/>`
* 复选框是checkbox必须和label标签配合使用的
* `<input type="submit" />` 和 `<input type="button" />`，button是定义一个按钮，onclick可执行js，submit是提交表单
* input type="hidden"，用于隐藏，后台传递数据（不要使用hidden来传递敏感信息）
* button标签和 `<input type="button" />`的区别是button开始符号和结束符号中间可以插入其他标签或文本。在表单中使用input，因为需要提交数据，在开发中一般使用div+css来制作美观的按钮
* name是HTML中的标准，而id是XHTML中的标准，现在网页的标准都是使用id
* 表格只用来做表格数据展示，不建议使用表格布局，已被抛弃

### 语义化

#### 标题

* 尽量一个页面只能有一个h1

* h1-h6不要断层

* 不要用h1-h6来定义样式

  不应该使用标签来控制样式，结构（html）和样式（css）应该分开

* 不要用div来代替h1-h6

  标题就应该用标题

* 一般只用h1-h4，不会用到那么多级标题，而且搜索引擎优化会给h1-h4一定权重，而h5、h6和普通标签差不多

#### 图片

图片+图注使用 figure+figcaption，而不是img+span

#### 换行

`<br/>`只用来做段落(p)中的换行，不能用来做其他标签之间的换行以及间距

#### 列表

对于列表类型使用无序列表或有序列表，而不是div

大多数使用无序列表，因为有序列表数字外观是固定的，不方便定制

#### strong加粗 em斜体

仅仅为了实现加粗和斜体不建议使用strong和em，有强调的语义，搜索引擎也会赋予有权重，使用span

一般情况下去掉strong和em的默认样，CSS重新定义，同时会保留强调语义与权重

#### img和背景图

如果图片作为HTMl的一部分，比如图片列表，且希望被搜索引擎识别，就用img

如果不希望被搜索引擎识别，也不是html的一部分，就用背景图片

#### 语义化验证

想验证一个页面的语义是否良好，去掉css样式，看页面是否还具有良好的可读性

使用网页调试插件`Web Developer`工具栏CSS -> Disable Styles -> Disable All Styles

### head

```html
<!-- base元素：页面上的所有链接规定默认地址或默认目标 -->
<base href="http://www.w3school.com.cn/images/" />
<base target="_blank" />

link外部资源
<link rel="stylesheet" type="text/css" href="mystyle.css" />

meta元数据
页面描述
<meta name="description" content="Free Web tutorials on HTML, CSS, XML" />
针对搜索引擎的关键字
<meta name="keywords" content="HTML, CSS, XML" />
```

### 响应式

尺寸可变，使用平板和移动设备

```html
<style>
.city {
	float: left;
}
</style>

<div class="city">
</div>
<div class="city">
</div>
<div class="city">
</div>
```

### window

一个浏览器窗口就是一个window对象，操作浏览器窗口的一个对象。document对象、history对象等都是window对象的子对象

| 方法                           | 说明               |
| :----------------------------- | :----------------- |
| open(url, 名称, 参数)、close() | 打开窗口、关闭窗口 |
| resizeBy()、resizeTo(px, px)   | 改变窗口大小       |
| moveBy()、moveTo()             | 移动窗口           |

### history

window的属性，因为window为全局对象，调用时可省略`window.history === history`

| 属性     | 说明                                     |
| :------- | :--------------------------------------- |
| current  | 当前窗口的URL                            |
| next     | 历史列表中的下一个URL                    |
| previous | 历史列表中的前一个URL                    |
| length   | 历史列表的长度，用于判断列表中的入口数目 |

| 方法      | 说明           |
| :-------- | :------------- |
| go()      | 进入指定的网页 |
| back()    | 返回上一页     |
| forward() | 进入下一页     |

```
window.history.back()
history.back()
```

### 对话框

alert、confirm、prompt

```
alert('message')

if (confirm("确认？")) {
} else {
}

let name = prompt("请输入你的名字");
```

### document

文档对象，操作HTML文档

| 属性             | 说明                      |
| :--------------- | :------------------------ |
| title            | 文档标题，即title标签内容 |
| URL              | 文档地址                  |
| fileCreateDate   | 文档创建日期              |
| fileModifiedDate | 文档修改时间（精确到天）  |
| lastModified     | 文档修改时间（精确到秒）  |
| fileSize         | 文档大小                  |
| fgColor          | 定义文档的前景色          |
| bgColor          | 定义文档的背景色          |
| linkColor        | 定义“未访问”的超链接颜色  |
| alinkColor       | 定义“被激活”的超链接颜色  |
| vlinkColor       | 定义“访问过”的超链接颜色  |

| 方法                         | 说明                                                        |
| :--------------------------- | :---------------------------------------------------------- |
| document.write()             | 输入文本到当前打开的文档                                    |
| document.writeIn()           | 写入到文档并添加“\n”                                        |
| document.getElementById()    | 获取某个id值的元素，返回一个元素                            |
| document.getElementsByName() | 获取某个name值的元素，用于表单元素<input name="">，返回数组 |
| document.createElement()     | 创建元素节点                                                |
| document.createTextNode()    | 创建文本节点                                                |

```
var e = document.createElement("input");        //创建元素节点
e.id = 'submit'
var t = document.createTextNode("元素内容");     //创建文本节点
e.appendChild(t);                               //把元素内容插入元素中去
document.body.appendChild(e)                    // 新的节点插入到当前节点的“内部”

obj.appendChild(new)
obj.insertBefore(new, ref)
obj.removeChild(oldChild)
obj.cloneNode(bool) // 参数表示是否复制子节点
obj.replaceChild(new,old) // obj为父节点
```



### DOM

Document Object Model 文档对象模型。是一个接口，通过它来操作页面中各种元素。DOM采用树形结构分层，树节点作为各种元素或内容

每一个元素节点都看成一个“**对象**”。由于元素节点也是一个对象，因此他们有自身的属性和方法。

| 属性            | 说明                                            |
| :-------------- | :---------------------------------------------- |
| parentNode      | 获取当前节点的父节点                            |
| childNodes      | 获取当前节点的子节点集合                        |
| firstChild      | 获取当前节点的第一个子节点                      |
| lastChild       | 获取当前节点的最后一个子节点                    |
| previousSibling | 获取当前节点的前一个兄弟节点                    |
| nextSibling     | 获取当前节点的后一个兄弟节点                    |
| attributes      | 元素的属性列表                                  |
| hasChildNodes   | 是否有子节点                                    |
| innerHTML       | 元素包含的html文本                              |
| innerText       | 元素包含的文本内容 IE、Chrome支持，Firfox不支持 |
| style           | css样式，样式使用驼峰法                         |

### 事件

调用事件方式有两种

```js
// 在script中调用
var e = document.getElementById('元素id')
e.onclick = function() { // 变量名.事件处理器
}
// 在元素中调用事件
<script type="text/javascript">
	function alertMessage() {
  	alert("绿叶学习网");
  	this.style.color = 'red'
	}
</script>
<input type="button" onclick="alertMessage('')" value="按钮"/>
```

#### 鼠标事件

| 事件        | 说明         |
| :---------- | :----------- |
| onclick     | 鼠标单击事件 |
| ondbclick   | 鼠标双击事件 |
| onmouseover | 鼠标移入事件 |
| onmouseout  | 鼠标移出事件 |
| onmousemove | 鼠标移动事件 |
| onmousedown | 鼠标按下事件 |
| onmouseup   | 鼠标松开事件 |

#### 键盘事件

| 方法       | 说明                                 |
| :--------- | :----------------------------------- |
| onkeydown  | 按下事件（包括字符键、功能键）       |
| onkeypress | 按下事件（只包含字符键）             |
| onkeyup    | 按下后放开事件（包括数字键、功能键） |

```js
function refresh() {
		//判断是否按下大写R键
		if (window.event.keyCode == 82) {
			location.reload();    //刷新页面
		}
}
//调用函数
document.onkeypress = refresh;
```

字符键包括A-Z、数组，功能键包括ctrl、shift、alt、F等

按下字符键会同时触发onkeydown和onkeypress，onkeydown先于onkeypress执行

#### 表单事件

| 事件     | 说明                                |
| :------- | :---------------------------------- |
| onfocus  | 获取焦点事件 text，textarea，select |
| onblur   | 失去焦点事件 text，textarea，select |
| onchange | 状态改变事件 text，textarea，select |
| onselect | 选中文本事件 text，textarea         |

#### 编辑事件

| 方法                                             | 说明                        |
| :----------------------------------------------- | :-------------------------- |
| oncopy                                           | 复制事件                    |
| oncut                                            | 剪切事件                    |
| onpaste                                          | 粘贴事件                    |
| onbeforecopy<br />onbeforecut<br />onbeforepaste | 复制之前触发，返回false禁止 |

```js
obj.oncopy=function(){
	alert("版权所有，禁止复制！");
  return false;  //返回false，表示屏蔽复制功能。浏览器禁用Javascript后失效
}
```

#### 页面相关事件

window.xxx = xxx

| 方法     | 说明                                                         |
| :------- | :----------------------------------------------------------- |
| onload   | 页面加载事件。文档加载完毕再执行。在head > script中onload完成后才能对dom进行操作 |
| onresize | 页面大小改变事件                                             |
| onerror  | 页面或图片加载出错事件，只在IE有效 <br />`<img src="logo.jpg" onerror="alert('图片没有加载成功！')"/>` |

### 其他

#### 标题栏小图标

小图标格式为ico，搜索“在线ico”制作

`<link rel="shortcut icon" type="image/x-icon" href="favicon.ico"/>`

