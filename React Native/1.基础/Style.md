## flexbox
####位置、宽高
* position
  * relative 默认，相对布局
  * absolute 绝对布局，margin、padding等不管用， 可以设置top、left、right、bottom
* width
* height
* maxHeight
* maxWidth
* minHeight
* minWidth
####对齐
* flexDirection 子组件对齐方式
  * row 横向
  * column 纵向
* flexWrap 子组件是否自动换行
  * wrap 自动换行
  * nowrap 默认，不自动换行
* justifyContent 子组件在一个方向上的排列方式
  * flex-start
  * flex-end
  * center
  * space-between 拉伸到父组件
  * space-around  拉伸并居中
* alignItems 子组件对齐方式
  * flex-start
  * flex-end
  * center
  * stretch 拉长对齐
* flex 是否自动缩放
  * 0 默认，不自动缩放
  * 1 自动缩放以拉伸空白区域
* alignSelf 自己的对齐方式
  * auto 使用父组件的alignItems
  * flex-start
  * flex-end
  * center 居中
  * stretch 拉伸
####边框
* borderWidth
* borderHorizontalWidth
* borderVerticalWidth
* borderTopWidth
* borderRightWidth
* borderLeftWidth
* borderBottomWidth
####空隙
* margin
* marginHorizontal 水平的两个方向
* marginVertical 竖直的两个方向
* marginTop
* marginRight
* marginLeft
* marginBottom
####填充
* padding
* paddingHorizontal
* paddingVertical
* paddingTop
* paddingRight
* paddingLeft
* paddingBottom

##View
* opacity 透明度0-1
* overflow 是否隐藏子组件超出部分
  * visible 默认，显示
  * hidden 隐藏
* backfaceVisibility
  * visible
  * hidden
#### 边框
* borderRadius
* borderTopLeftRadius
* borderTopRightRadius
* borderBottomLeftRadius
* borderBottomRightRadius
* borderColor
* borderTopColor
* borderRightColor
* borderLeftColor
* borderBottomColor
* borderStyle
  * solid 实线
  * dotted 点
  * dashed 虚线
####阴影
ios：
* shadowColor 阴影颜色
* shadowOffset 阴影位移值
* shadowOpacity 阴影透明度
* shadowRadius 阴影圆角率

android：
* elevation: float 安卓阴影
####变形
* transform
  * perspective: number 3D变形
  * rotate: string 旋转 eg: 45deg(45°)
  * rotateX
  * rotateY
  * rotateZ
  * scale: number 缩放
  * scaleX
  * scaleY
  * translateX: number 平移
  * translateY
  * skewX: string 倾斜 eg: 45deg(45°)
  * skewY

  `旋转与倾斜：旋转不发生形变，倾斜按照3D空间进行形变`
