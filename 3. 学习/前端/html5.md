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

aside TODO

页头包含：等

文章头包含：

区块头部包含：标题内容 

### 视频 video

Chrome只支持 MPEG 4

标签属性

| 属性                                                         | 值       | 描述                                                         |
| :----------------------------------------------------------- | :------- | :----------------------------------------------------------- |
| [autoplay](https://www.w3school.com.cn/tags/att_video_autoplay.asp) | autoplay | 如果出现该属性，则视频在就绪后马上播放。                     |
| [controls](https://www.w3school.com.cn/tags/att_video_controls.asp) | controls | 如果出现该属性，则向用户显示控件，比如播放按钮。             |
| [height](https://www.w3school.com.cn/tags/att_video_height.asp) | *pixels* | 设置视频播放器的高度。                                       |
| [loop](https://www.w3school.com.cn/tags/att_video_loop.asp)  | loop     | 如果出现该属性，则当媒介文件完成播放后再次开始播放。         |
| [preload](https://www.w3school.com.cn/tags/att_video_preload.asp) | preload  | 如果出现该属性，则视频在页面加载时进行加载，并预备播放。如果使用 "autoplay"，则忽略该属性。 |
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