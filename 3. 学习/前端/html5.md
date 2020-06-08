[TOC]

新特性

- 用于绘画的 canvas 元素
- 用于媒介回放的 video 和 audio 元素
- 对本地离线存储的更好的支持
- 新的特殊内容元素（语义元素布局），比如 article、footer、header、nav、section
- 新的表单控件，比如 calendar、date、time、email、url、search

### 结构元素

header用于页头（网页名称、Logo、顶部导航、介绍信息）、文章头部article（文章标题、meta信息（作者、点赞数、评论数等））、区块头部section（标题）

nav 顶部导航、侧栏导航、分页导航。可放在header里或外，主导航一般用无序列表实现

article只用于文章内容部分，可当做独立的部分，可包含header、section、footer，每个artlce内部都应该有一个header

aside 相关内容。用在article和section中表示和内容相关，用在他们之外表示和整个页面相关，如相关文章、链接、广告等

section 需要标题（header）的区块。不需要标题则直接使用div。

优先使用语义化更好的article和aside，再考虑用section

footer 页面底部（友情链接、版权、备案等）、文章底部（分页、分类、发布信息等）

### 表单元素

#### input type

email、tel、url、range数值滑块、number数值微调按钮、color、date、time、month、week

必须点击submit，浏览器的验证机制才会触发

#### 元素

output：用在form中，和input搭配使用，表示输出结果

datalist：为文本框提供一个可选列表。input使用list绑定列表。用于自动联想等场景

```html
<input type='text' list='urlList'/>
<datalist id='urlList'>
  <option label='百度' value='https://www.baidu.com'></option>
  <option label='Google' value='https://www.google.com'></option>
</datalist>
```

address 地址信息（就是一个语义化的div），一般放在footer

time 显示日期时间信息 `<time datetime='时间'>时间</time>`datetime中的时间是给搜索引擎看的，可省略，time标签的内容才是给用户看的

progress进度条 max value当前值

meter 进度条，和progress不同的是，用来显示静态的数据，例如男生占全班人数的比例

figure、figcaption 语义化图片+ 图注

```html
<figure>
  <img/>
  <figcaption>图注</figcaption>
</figure>
```

fieldset、legend  fieldset给表单分组，legend定义某组表单的标题。用于语义化和通过fieldset的disabled来禁用整个组的表单元素。使用fieldset后，表单形成书签效果

```html
  <fieldset>
    <legend>登录</legend>
    <label for='name'></label>
    <input type='text' id='name' name='name' />
  </fieldset>
```

#### 改良元素

a：download属性表示下载文件，属性值表示新的文件名，忽略属性值表示仅下载，用旧的文件名

```
<a href='img/1.png' download="2.png">下载图片</a>
<a href='img/1.png' download>下载图片</a>
```

small 语义化 元素表示小字印刷体，用于底部免责声明、版权声明等

script 增加defer、async，加快页面加载速度。defer异步加载外部js，加载完成后，不会立即执行，html加载完成后才会执行。async异步加载外部js，加载完成后立即执行。defer更符合大多数场景

### 新增属性

#### 公共属性

大多数元素的属性

hidden 显示或隐藏 `hidden='hidden'`或直接 `hidden`

draggable 是否可被拖动 true/false。只可被拖动，放手后不会改变位置

contenteditable 元素是否可被编辑 true/false 

data-xxx 自定义属性。可用于JS动画

```
  <p data-color='red'></p>      通过obj.dataset.color获取值
  <p data-bg-color='white'></p> 通过obj.dataset.bgColor获取值
```

#### input新增属性

autocomplete 自动提示 on/off，一般结合 datalist 元素使用。用于所有文本类型的input

autofocus 自动聚焦 `autofocus='autofocus'` `autofocus`。用于所有文本类型

placeholder 文本提示内容

required 文本输入框内容不能为空 `required='required'` `required`

pattern 文本框增加验证功能

#### form属性

novalidate：`novalidate` 取消所有input内置的验证机制，用于需要手动通过js来完成更为复杂的验证 

### 元素拖放

H5之前，想实现只能结合onmousedown、onmousemove、onmouseup等事件完成，代码量大，且只能在浏览器，不能跨应用

源元素事件：ondragstart、ondrag、ondragend

目标元素事件：ondragenter 被拖放元素进入本元素、ondragover 被拖放元素在本元素内移动时、ondragleave 离开、ondrop 源元素释放到本元素时

完整的顺序：dragstart -> dragenter -> dragover -> dragleave -> drop -> dragend

实例：拖放图片并移动位置

```html
<!DOCTYPE html>
<html>

<head>
  <style>
    body {position: relative;}
    img {position: absolute;}
  </style>
  <script>
    window.onload = function () {
      let img = document.getElementsByTagName('img')[0]
      let offsetX, offsetY

      img.ondragstart = function (e) {
        // offsetX offsetY 图片初始位置
        offsetX = e.offsetX
        offsetY = e.offsetY
      }

      img.ondrag = function (e) {
        // pageX pageY 表示鼠标在窗口中的坐标
        if (e.pageX == 0 && e.pageY == 0)
          return
        img.style.left = (e.pageX - offsetX) + 'px'
        img.style.top = (e.pageY - offsetY) + 'px'
      }
    }
  </script>
</head>

<body>
  <img style="width: 150px; height: 150px;" src="/Users/huowenxuan/Pictures/查理王/333.jpg" draggable="true" />
</body>

</html>
```

页头包含：等

文章头包含：

区块头部包含：标题内容 

种子源元素和目标元素传递数据用dataTransfer对象。ondragstart调用setData保存数据，放入目标元素ondrop时调用getData读取

```js
setData(format, data) // format为数据格式，有text/plain text/html text/xml text/url-list
source.ondragstart = function(e) {
	e.dataTransfer.setData('text/plain', e.target.id)
}

getData(format)
target.ondragover = function(e) {
  e.preventDefault() // 屏蔽元素默认行为，否则ondrop不会被触发
}
target.ondrop = function(e) {
  e.preventDefault()
  let id = e.dataTransfer.getData('text/plain')
} 
```

### 文件操作

html的文件操作都是读取、创建、上传。修改、移动、压缩做不到

#### input file

文件上传使用 `<input type='file'/>`，mutiple表示是否选择多个文件，accept为过滤类型MIME类型（`image/jpeg、image/*、audio/*、video/*`），多个类型逗号隔开 

样式美化：使用opacity:0 将表单透明，但是还占据位置，再使用呢绝对定位在表单原来位置定义一个label

```html
样式美化   
.filePicker 
    {
      position: relative;
      width: 100px;
      height: 44px;
      text-align: center;
      line-height: 44px;
      color: #ffffff;
      background: #00b7ee;
    }
    .filePicker input[type='file']
    {
      position: absolute;
      top:0;
      left:0;
      width: 100px;
      height: 44px;
      opacity: 0;
      cursor: pointer;
    }
    
  <script>
    // 获取文件信息
    let f = document.getElementById('fileInput')
    f.onchange = function (e) {
      let file = f.files[0] // files所有文件的集合
      file.name
      file.type
      file.size // 单位B，÷ 1024 = kb 
      file.lastModifiedDate
    }
  </script>

<div class="conntainer">
  <label>点击选择</label>
  <input id='fileInput' type='file'/>
</div>
```

#### FileReader

读取文件数据

以不同类型读取文件：readAsText readAsDataURL readAsBinaryString二进制编码 readAsArrayBuffer

中止读取：abort()

事件：onloadstart onprogress onload成功读取 onloadend读取完成无论成功失败 onabort onerror

```js
    // 读取文本 readAsText
		let f = document.getElementById('fileInput')
    f.onchange = function (e) {
      let file = f.files[0] // files所有文件的集合
      let reader = new FileReader()
      reader.readAsText(file, 'gbk') // 第二个参数为编码，默认utf-8
      reader.onload = function () {
        console.log(this.result) // 文件内容。读取失败文件内容为null
      }
    }

		// 预览图片 readAsDataURL
    let f = document.getElementById('fileInput')
    f.onchange = function (e) {
      let file = f.files[0] 
      let reader = new FileReader()
      reader.readAsDataURL(file) // 转为base64
      reader.onload = function () {
        img.src = this.result
      }
    }
```

#### blob

原始二进制数据，File继承于Blob

```
var blob = new Blob(dataArray, type)
var blob = new Blob([text], {type: "text/plain"})
```

第一个参数是一个数组，数组中的元素可以是：

1. String
2. Blob：其他blob
3. ArrayBuffer
4. ArrayBufferView

第二个参数type是字符串，mime

```js
// 创建并下载txt文件（不需添加多余元素）
let blob = new Blob([text], {type: 'text/plain'})
let a = document.createElement('a')
// 重点 生成网络地址。可用来预览本地图片或视频
let url = window.URL.createObjectURL(blob)
a.download = '1.txt'
a.href = url
document.body.appendChild(a)
// 重点
a.click()
document.body.removeChild(a)

// 下载canvas是一样的原理，调用canvas对象的toBlob，将blob保存
```



### 视频 video

### 本地存储

html4只能用cookie存储，缺点：1）大小限制：最大为4kb；2）数量限制：每个站点最多存储20个，旧的丢弃；3）默认情况下会随着http请求发送到后台，但大多数都是不需要的

#### localStorage

永久存储少量数据，关闭浏览器数据不丢失，每个域名保存5MB

setItem(k,v) getItem(k) removeItem(key) clear()请空所有 key(n)获取第n个值

#### sessionStorage

用于临时保存的少量数据，页面关闭，数据消失。和localStorage方法相同。用处较少

#### indexedDB

用于永久保存大量数据。存储在客户端本地的NoSQL数据库

### Video

Chrome只支持 MPEG 4

标签属性

| 属性                                                         | 值       | 描述                                                         |
| :----------------------------------------------------------- | :------- | :----------------------------------------------------------- |
| [autoplay](https://www.w3school.com.cn/tags/att_video_autoplay.asp) | autoplay | 如果出现该属性，则视频在就绪后马上播放。                     |
| [controls](https://www.w3school.com.cn/tags/att_video_controls.asp) | controls | 如果出现该属性，则向用户显示控件，比如播放按钮。             |
| [height](https://www.w3school.com.cn/tags/att_video_height.asp) | *pixels* | 设置视频播放器的高度。                                       |
| [loop](https://www.w3school.com.cn/tags/att_video_loop.asp)  | loop     | 完成播放后再次开始播放。                                     |
| [preload](https://www.w3school.com.cn/tags/att_video_preload.asp) | preload  | 视频在页面加载时进行加载，并预备播放。如果使用 "autoplay"，则忽略。auto 预加载（默认） metadata 只预加载元数据（媒体字节数、第一帧、播放列表等） none |
| [src](https://www.w3school.com.cn/tags/att_video_src.asp)    | *url*    | 要播放的视频的 URL。                                         |
| [width](https://www.w3school.com.cn/tags/att_video_width.asp) | *pixels* | 设置视频播放器的宽度。                                       |

dom

属性中只有 videoWidth 和 videoHeight 属性是立即可用的。在视频的元数据已加载后，其他属性才可用

| 方法        | 属性        | 事件           |
| :---------- | :---------- | :------------- |
| play()      | currentSrc  | play           |
| pause()     | currentTime | pause          |
| load()      | videoWidth  | progress       |
| canPlayType | videoHeight | error          |
|             | duration    | timeupdate     |
|             | ended       | ended          |
|             | error       | abort          |
|             | paused      | empty          |
|             | muted       | emptied        |
|             | seeking     | waiting        |
|             | volume      | loadedmetadata |
|             | height      |                |
|             | width       |                |

```
<video src="movie.ogg" controls="controls">
之间的内容是供不支持 video 元素的浏览器显示的
</video>

<video  controls="controls">
允许多个 source 元素。source 元素可以链接不同的视频文件。浏览器将使用第一个可识别的格式
  <source src="movie.ogg" type="video/ogg">
  <source src="movie.mp4" type="video/mp4">
</video>
```

#### 自定义

TODO

### 音频 audio

Safair只支持mp3和wav，Chrome只支持mp3和ogg

```
<audio controls="controls">
  <source src="song.ogg" type="audio/ogg">
  <source src="song.mp3" type="audio/mpeg">
不支持时显示的内容
</audio>
```

标签的属性

| 属性                                                         | 值       | 描述                                                         |
| :----------------------------------------------------------- | :------- | :----------------------------------------------------------- |
| [autoplay](https://www.w3school.com.cn/tags/att_audio_autoplay.asp) | autoplay | 如果出现该属性，则音频在就绪后马上播放。                     |
| [controls](https://www.w3school.com.cn/tags/att_audio_controls.asp) | controls | 如果出现该属性，则向用户显示控件，比如播放按钮。             |
| [loop](https://www.w3school.com.cn/tags/att_audio_loop.asp)  | loop     | 如果出现该属性，则每当音频结束时重新开始播放。               |
| [preload](https://www.w3school.com.cn/tags/att_audio_preload.asp) | preload  | 如果出现该属性，则音频在页面加载时进行加载，并预备播放。如果使用 "autoplay"，则忽略该属性。 |
| [src](https://www.w3school.com.cn/tags/att_audio_src.asp)    | *url*    | 要播放的音频的 URL。                                         |

### 存储

- localStorage - 没有时间限制的数据存储
- sessionStorage - 针对一个 session 的数据存储，关闭窗口数据删除

