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

##Image
* resizeMode 显示模式
  * cover 等比例填充，如果超出区域，就缩小到区域大小，如果没超出，就放大到区域大小
  * contain 等比例，如果图片超过区域大小，就缩小到区域边界，如果比区域小，就不缩放
  * stretch 不等比，完全填充
* tintColor: ios only，让图片的非透明区域有被染色的效果
* overlayColor: android only，某些情况无法用过borderRadius设置圆角，用这个属性将圆角部分使用指定颜色填充，实现圆角效果

##Text TextInput
> Text不使用flexbox布局, justifyContent无效，想要垂直居中，需要在Text外套一个View
* fontFamily
* fontSize
* fontWeight 粗细
  * normal bold 100 200 300 400 500 600 700 800 900
* textAlign
  * auto left right center justify
* letterSpacing: int 每个字符之间插入多少控件
* writingDirection 文本方向
  * auto
  * ltr 左向右
  * rtl 右向左
* lineHeight 每行高度 (之前android会crash)
* textDecorationLine 线样式
  * none
  * underline: 下划线
  * line-through：贯穿线
  * underline line-through: 下划线+贯穿线
* textDecorationStyle 线风格, 设置了textDecorationLine才管用
  * solid 实线
  * double 双实线
  * dotted 长条虚线
  * dashed 虚线
* textShadowOffset {
    width
    height
  }
* textShadowRadius
* textShadowColor
