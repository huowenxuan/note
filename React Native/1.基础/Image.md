```
// 将图片尺寸装换为屏幕尺寸
let PixelRatio = require('PixelRatio')
let pixelRatio = PixelRatio.get()

let realWidth = imageWidth / pixelRatio
let realHeight = imageHeight / pixelRatio
```


加载网络图片
```
<Image source={{uri: ''}} />
```
加载静态资源
```
<Image source={require('')} />
```
