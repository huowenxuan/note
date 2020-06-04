[TOC]

### 选择器

* 子元素选择器：/#father div{...} 选择 id 为father的元素下的所有div元素
* 群组选择器：h3,div,p,span {...}
* 后代选择器：M N    元素内部所有子元素和后代元素
* 子代选择器：M > N 元素内部所有一级子元素
* 兄弟选择器：M ~ N 元素之后的所有同级
* 相邻选择器：\#lv+div {...} 选择id为lv相邻的下一个同级元素div
* :first-letter: 选中元素内容第一个字
* :first-line：第一行

| 选择器                                                       | 例子                  | 例子描述                                            | CSS  |
| :----------------------------------------------------------- | :-------------------- | :-------------------------------------------------- | :--- |
| [.*class*](https://www.w3school.com.cn/cssref/selector_class.asp) | .intro                | 选择 class="intro" 的所有元素。                     | 1    |
| [#*id*](https://www.w3school.com.cn/cssref/selector_id.asp)  | #firstname            | 选择 id="firstname" 的所有元素。                    | 1    |
| [*](https://www.w3school.com.cn/cssref/selector_all.asp)     | *                     | 选择所有元素。                                      | 2    |
| [*element*](https://www.w3school.com.cn/cssref/selector_element.asp) | p                     | 选择所有 <p> 元素。                                 | 1    |
| [*element*,*element*](https://www.w3school.com.cn/cssref/selector_element_comma.asp) | div,p                 | 选择所有 <div> 元素和所有 <p> 元素。                | 1    |
| [*element* *element*](https://www.w3school.com.cn/cssref/selector_element_element.asp) | div p                 | 选择 <div> 元素内部的所有 <p> 元素。                | 1    |
| [*element*>*element*](https://www.w3school.com.cn/cssref/selector_element_gt.asp) | div>p                 | 选择父元素为 <div> 元素的所有 <p> 元素。            | 2    |
| [*element*+*element*](https://www.w3school.com.cn/cssref/selector_element_plus.asp) | div+p                 | 选择紧接在 <div> 元素之后的所有 <p> 元素。          | 2    |
| [[*attribute*\]](https://www.w3school.com.cn/cssref/selector_attribute.asp) | [target]              | 选择带有 target 属性所有元素。                      | 2    |
| [[*attribute*=*value*\]](https://www.w3school.com.cn/cssref/selector_attribute_value.asp) | [target=_blank]       | 选择 target="_blank" 的所有元素。                   | 2    |
| [[*attribute*~=*value*\]](https://www.w3school.com.cn/cssref/selector_attribute_value_contain.asp) | [title~=flower]       | 选择 title 属性包含单词 "flower" 的所有元素。       | 2    |
| [[*attribute*\|=*value*\]](https://www.w3school.com.cn/cssref/selector_attribute_value_start.asp) | [lang\|=en]           | 选择 lang 属性值以 "en" 开头的所有元素。            | 2    |
| [:link](https://www.w3school.com.cn/cssref/selector_link.asp) | a:link                | 选择所有未被访问的链接。                            | 1    |
| [:visited](https://www.w3school.com.cn/cssref/selector_visited.asp) | a:visited             | 选择所有已被访问的链接。                            | 1    |
| [:active](https://www.w3school.com.cn/cssref/selector_active.asp) | a:active              | 选择活动链接。                                      | 1    |
| [:hover](https://www.w3school.com.cn/cssref/selector_hover.asp) | a:hover               | 选择鼠标指针位于其上的链接。                        | 1    |
| [:focus](https://www.w3school.com.cn/cssref/selector_focus.asp) | input:focus           | 选择获得焦点的 input 元素。                         | 2    |
| [:first-letter](https://www.w3school.com.cn/cssref/selector_first-letter.asp) | p:first-letter        | 选择每个 <p> 元素的首字母。                         | 1    |
| [:first-line](https://www.w3school.com.cn/cssref/selector_first-line.asp) | p:first-line          | 选择每个 <p> 元素的首行。                           | 1    |
| [:first-child](https://www.w3school.com.cn/cssref/selector_first-child.asp) | p:first-child         | 选择属于父元素的第一个子元素的每个 <p> 元素。       | 2    |
| [:before](https://www.w3school.com.cn/cssref/selector_before.asp) | p:before              | 在每个 <p> 元素的内容之前插入内容。                 | 2    |
| [:after](https://www.w3school.com.cn/cssref/selector_after.asp) | p:after               | 在每个 <p> 元素的内容之后插入内容。                 | 2    |
| [:lang(*language*)](https://www.w3school.com.cn/cssref/selector_lang.asp) | p:lang(it)            | 选择带有以 "it" 开头的 lang 属性值的每个 <p> 元素。 | 2    |
| [*element1*~*element2*](https://www.w3school.com.cn/cssref/selector_gen_sibling.asp) | p~ul                  | 选择前面有 <p> 元素的每个 <ul> 元素。               | 3    |
| [[*attribute*^=*value*\]](https://www.w3school.com.cn/cssref/selector_attr_begin.asp) | a[src^="https"]       | 选择其 src 属性值以 "https" 开头的每个 <a> 元素。   | 3    |
| [[*attribute*$=*value*\]](https://www.w3school.com.cn/cssref/selector_attr_end.asp) | a[src$=".pdf"]        | 选择其 src 属性以 ".pdf" 结尾的所有 <a> 元素。      | 3    |
| [[*attribute**=*value*\]](https://www.w3school.com.cn/cssref/selector_attr_contain.asp) | a[src*="abc"]         | 选择其 src 属性中包含 "abc" 子串的每个 <a> 元素。   | 3    |
| [:first-of-type](https://www.w3school.com.cn/cssref/selector_first-of-type.asp) | p:first-of-type       | 选择属于其父元素的首个 <p> 元素的每个 <p> 元素。    | 3    |
| [:last-of-type](https://www.w3school.com.cn/cssref/selector_last-of-type.asp) | p:last-of-type        | 选择属于其父元素的最后 <p> 元素的每个 <p> 元素。    | 3    |
| [:only-of-type](https://www.w3school.com.cn/cssref/selector_only-of-type.asp) | p:only-of-type        | 选择属于其父元素唯一的 <p> 元素的每个 <p> 元素。    | 3    |
| [:only-child](https://www.w3school.com.cn/cssref/selector_only-child.asp) | p:only-child          | 选择属于其父元素的唯一子元素的每个 <p> 元素。       | 3    |
| [:nth-child(*n*)](https://www.w3school.com.cn/cssref/selector_nth-child.asp) | p:nth-child(2)        | 选择属于其父元素的第二个子元素的每个 <p> 元素。     | 3    |
| [:nth-last-child(*n*)](https://www.w3school.com.cn/cssref/selector_nth-last-child.asp) | p:nth-last-child(2)   | 同上，从最后一个子元素开始计数。                    | 3    |
| [:nth-of-type(*n*)](https://www.w3school.com.cn/cssref/selector_nth-of-type.asp) | p:nth-of-type(2)      | 选择属于其父元素第二个 <p> 元素的每个 <p> 元素。    | 3    |
| [:nth-last-of-type(*n*)](https://www.w3school.com.cn/cssref/selector_nth-last-of-type.asp) | p:nth-last-of-type(2) | 同上，但是从最后一个子元素开始计数。                | 3    |
| [:last-child](https://www.w3school.com.cn/cssref/selector_last-child.asp) | p:last-child          | 选择属于其父元素最后一个子元素每个 <p> 元素。       | 3    |
| [:root](https://www.w3school.com.cn/cssref/selector_root.asp) | :root                 | 选择文档的根元素。                                  | 3    |
| [:empty](https://www.w3school.com.cn/cssref/selector_empty.asp) | p:empty               | 选择没有子元素的每个 <p> 元素（包括文本节点）。     | 3    |
| [:target](https://www.w3school.com.cn/cssref/selector_target.asp) | #news:target          | 选择当前活动的 #news 元素。                         | 3    |
| [:enabled](https://www.w3school.com.cn/cssref/selector_enabled.asp) | input:enabled         | 选择每个启用的 <input> 元素。                       | 3    |
| [:disabled](https://www.w3school.com.cn/cssref/selector_disabled.asp) | input:disabled        | 选择每个禁用的 <input> 元素                         | 3    |
| [:checked](https://www.w3school.com.cn/cssref/selector_checked.asp) | input:checked         | 选择每个被选中的 <input> 元素。                     | 3    |
| [:not(*selector*)](https://www.w3school.com.cn/cssref/selector_not.asp) | :not(p)               | 选择非 <p> 元素的每个元素。                         | 3    |
| [::selection](https://www.w3school.com.cn/cssref/selector_selection.asp) | ::selection           | 选择被用户选取的元素部分。                          | 3    |

### CSS规范

#### 文件命名

reset.css重置，重置元素默认样式；global.css 全局样式；theme主题；module模块；master母版；column专栏；form表单；mend补丁。以上是开发阶段，发布时使用webpack打包

#### id、class命名
为了避免class命名重复，一般取父元素的class名作为前缀：column column-title。
主体命名：wrapper最外层；content/container主体；sidebar侧栏；column栏目；main-left左侧；main主体；menu菜单；submenu
导航：main-nav、sub-nav、side-nav边导航、leftside-nav左导航、top-nav
其他：tool toolbar工具条、related相关文章、siteinfolegal法律声明

#### 书写顺序

按样式功能的重要性排列；对于实现某一功能的集中列出；最好都加注释

| 属性类别   | 举例                                              |
| ---------- | ------------------------------------------------- |
| 布局       | display、position、float、clear                   |
| 自身盒模型 | width、height、padding、marginn、border、overflow |
| 文本       | font、line-height、text-align、text-indent        |
| 装饰       | color、background-color、opacity、cursor          |
| 其他       | content等                                         |

### CSS Rest 重置样式
不同浏览器默认样式不同，需要重置
不建议使用 `*{padding: 0; margin: 0}`，性能低，对于表格、input是不希望去掉的
可以参考Eric Meyer重置样式表，更建议自己根据需求来定制

### 单位
绝对单位：cm、mm、in、pt、pc
相对单位：px、%、em、rem
px属于相对单位是因为屏幕分辨率大小不同，1px大小也不同，但不考虑分辨率就可作为绝对单位
%: width、height、font-size百分比相对于父元素的相同属性值计算的；line-height相对于当前元素的font-size；vertical-align相对于当前元素line-height
1em = 当前元素字体大小font-size的px，当前元素没定义则找父元素，浏览器默认16px。技巧：
* 首行缩进使用text-indent: 2em
* 使用em作为字体大小单位。百分比作为字体大小不符合习惯，使用em，当网页字体需要修改时直接改变根元素的大小即可
* 使用em作为统一单位
  ```
  因为浏览器默认16px，提前声明 body{font-size: 62.5%}，可使默认你字体大小变为16*62.5% = 10px; 则：
  1em = 10px
  0.75em = 7.5px
  1.5em = 15px
  
  例：p元素width 150px，height 75px，font-size 15px，使用em：
  {
  	font-size: 1.5em;
  	width: 10em;
  	height: 5em
  }
  为什么width不是15em，而是10em：因为em相对于当前元素字体大小而言，所以需要以当前元素的font-size值再算一次，则 width: 150px / 15px = 10em
  ```

1rem = 根元素字体大小。css3，移动端布局产常用

### css特性

继承性：除了padding、margin、border等，子元素都会继承父元素的某些样式属性
> 例外：a元素因自身有颜色，所以默认不继承，想要继承使用 {color: inherit};

层叠性：同一个元素重复定义相同属性，权重相同的后面覆盖前面
> 权重：
> 引用方式优先级：行内样式 > (内部样式 = 外部样式)
> 继承方式优先级：最近的祖先最优先；
> 选择器权重：只针对当前元素，不能用于继承样式。行内样式 1000 > id选择器 100 > class选择器=伪类=属性选择器 10 > 元素选择器=伪元素 1 > 通配符 0。权重累加：#outer .inner strong 的权重为 100 + 10 + 1 = 111
> 指定样式 > 继承样式
> !important优先级最高。两个important以后面为主

### css加载方式
外部样式表：使用link，当被应用到多个页面是最理想的选择
内部样式表：某个页面的个别样式表，如果放在公共的外部样式表，会导致每个页面都会加载一次，影响加载速度
行内样式表：出现一两次、修改幅度小、优先级高的样式

### 文字样式

| 属性        | 说明                                                         |
| :---------- | :----------------------------------------------------------- |
| font-family | 字体类型                                                     |
| font-size   | 字体大小 px em 百分比                                        |
| font-weight | 字体粗细                                                     |
| font-style  | 字体斜体 normal; italic斜体; 对于没有斜体的特殊字体，使用oblique将字体倾斜 |
| color       | 颜色                                                         |

### 段落样式

段落样式设涉及多个文字（整个段落）的排版效果，注重整体。font前缀是文字样式，text前缀是段落样式

| 属性            | 说明                                                         |
| :-------------- | :----------------------------------------------------------- |
| text-decoration | none、下划线underline、删除线line-through、顶划线overline    |
| text-transform  | （英文）文本大小写 uppercase lowercase capitalize首字母大写  |
| font-varient    | 将英文文本转换为“小型”大写字母 normal small-caps。不常用     |
| text-indent     | 段落首行缩进值，一个字的缩进值为font-size值                  |
| text-align      | 文本水平对齐方式 left center right justify两端对齐 inherit从父元素继承，只对文本文字和img有效 |
| line-height     | 行高                                                         |
| letter-spacing  | 字距                                                         |
| word-spacing    | 词距                                                         |

### 边框样式

任何块元素和行内元素都可设置，div、img、table、span

三个元素要同时设置

| 属性             | 说明                                                         |
| :--------------- | :----------------------------------------------------------- |
| border-width     | 边框的宽度，一般只会用到solid、dashed。 none、hidden 和none相同，对于表解决边框冲突、solid实线、dashed虚线、dotted点线、double双线 |
| border-style     | 边框的外观（3D边框样式） inset内凹、outset外凸、ridge脊线、groove槽线 |
| border-color     | 边框的颜色                                                   |
| border           | 简洁写法 border:1px solid Red;     border: 1px;              |
| border-top-width | 局部样式，可对上下左右的width、style、color设置              |
| border-top       | 局部样式的简洁写法                                           |

### 背景样式
| 属性                  | 说明                                                         |
| :-------------------- | :----------------------------------------------------------- |
| background-color      | 背景色                                                       |
| background-image      | 背景图像的路径（元素必须有宽高） url(...)                    |
| background-repeat     | 背景图如何平铺<br />no-repeat不平铺、repeat-y纵向平铺、repeat-x横向平铺、repeat两个方向都平铺（默认） |
| background-position   | 设置背景图像的位置，只能用于块级元素和替换元素（img、input、textarea、select和object）  <br />像素值：80px 40px 表示距离左边80，上边40<br />关键字：top left左上、center center居中、bottom right右下等 |
| background-attachment | 设置背景图像是随对象滚动还是固定不动 scroll/fixed            |
| background-color      |                                                              |

### 超链接样式 a

a标签外观

去除a的下划线：text-decoration:none;

#### 超链接伪类

使用伪类定义不同状态下a标签的样式，4种样式定义顺序不能改变

| 属性      | 说明                     |
| :-------- | :----------------------- |
| a:link    | 定义a元素未访问时的样式  |
| a:visited | 定义a元素访问后的样式    |
| a:hover   | 定义鼠标经过显示的样式   |
| a:active  | 定义鼠标单击激活时的样式 |

一般情况下只用到两种状态：未访问状态 `a{...}`（不需要a:link）、鼠标经过状态`a:hover{...}`

####鼠标样式

div {cursor: default}  default/pointer/not-allow....

#### hover伪类

:hover伪类可以定义任何一个元素（块元素+行内元素）在鼠标经过时的样式。例 div:hover{}

### 图片样式 img

width/height/border

父元素设置水平对齐 text-align(left right center)

父元素设置垂直对齐 vertical-align(top middle bottom baseline基线对齐)

### 列表样式 ol、ul

在ol、ul中，设置列表符号是通过type定义，在css中使用`list-style-type`，设置为none为去除符号

`list-style-image:url(...)`设置图像

### 表格样式 table

`border-collapse` table独有属性，设置单元格间隙，separate（边框分开）/collapse（边框合并）

border-spacing:px 边框间隔

caption-side:top/bottom 表格标题的位置

### 盒子模型

所有元素都可看做是一个盒子，占据空间，盒子之间互相影响，盒子由content内容、padding内边距、margin外边距、border组成。内容有3个属性：width、height、overflow(指定超出如何处理 visible默认，可见；hidden；scroll显示滚动条；auto在需要时给滚动条)

border:0和border:none：border:0浏览器依然会渲染一个0px的border，占用内存，border:none不占用内存，在IE6IE7有兼容性问题，可忽略

宽高是针对内容区的，只有块元素能设置宽高，行内元素无法设置

```
div {display: inline-block} /* 将块元素转换为inline-block元素 */
```

#### margin叠加 外边距叠加

两个marin相遇，会合并，叠加之后为两个边距的最大值，只有垂直外边距会存在叠加，只针对block、inline-block元素，因为inline的margin无效

解决：（非必要）可统一使用margin-top或margin-bottom，不混合，降低风险

#### 负margin

当margin-left或top为负数，当前元素被拉向指定方向，bottom和right为负数，后续元素拉向指定方向

应用：

1. 图片与文本对齐

   当图片和文字放一起时，底部水平方向是不对齐的，因为都是基线对齐，vertical-align:baseline，可改为vertical-align:text-bottom;或使用负margin

2. 自适应两列布局：其中一列宽度固定，另一列宽度自适应

   用浮动只能实现固定的左右两列布局，无法实现其中一列自适应

   ```css
   #main, #sidebar 
   {
     float:left;
   }
   #main
   {
     width:100%;
     margin-right:-200px;
   }
   #sidebar
   {
     width: 200px;
   }
   #main p {margin-right: 210px;} /* 防止浏览器可视宽度不足发生文本重叠 10为边距 */
   
   <div id="mainn"><p>自适应</p></div>
   <div id="sidebar"><p>固定</p></div>
   ```

3. 元素垂直居中：父元素position:relative; 子元素position:absolute;top:50%;left:50%;margin-top:height一半的负数;margin-left:width一半的负数

### 浮动布局

正常文档流：从上到下分成一行一行，块元素占一行，相邻行内元素在每行中按从左到右依次排列

float:left/right 浮动使任何元素向左或向右浮动

```css
/* 图文混排，文字环绕图片布局 */
img{float: left/right; margin:20px;}
p{}
```

clear:left/right/both 清除浮动

```css
/* 对p清除浮动，p元素的前一个元素产生的浮动不会对后续元素产生影响，因此p不会环绕在浮动元素周围 */
p {clear: both;}
```

### 定位布局

静态定位static，默认，没有定位

固定定位fixed，相对于浏览器窗口位置定位

```css
{position:fixed; left:0px; top:10px;} /* 固定元素，不会随滚动条拖动而改变位置 */
```

相对定位relative，相对于其本身位置进行定位

```css
{position:relative; left:0px; top:10px;}
```

绝对定位absolute，相对于不是 static 定位的第一个父元素进行定位。脱离文档流

**要使用position来布局，父级元素的position必须为relative；absolve不受父元素padding的影响**

### display
* block 呈现为块元素。独占一行，内部可容纳块元素和行内元素，可定义宽高、margin
* inline 呈现为行内元素。可以和其他元素同一行，内部可容纳行内不可容纳块，无法定义宽高，可定义margin-left和right，无法定义bottom、top
* inline-block 行内块元素。可以和其他元素并列，又可以设置宽高，最常用的inline-block有img和input
* table 表格形式显示，类似table
* table-row 表格行形式，类似tr
* table-cell 以表格单元格形式，具有td的特点
* none 隐藏，不占据空间（visibility:hidden 不显示，但是占据空间）

table-cell用途：

1. 图片垂直居中于元素

   ```css
   父元素
   {
   	display: tabel-cell;
     vertical-align:middle;
   }
   img {vertical-align:middle;}
   ```

2. 等高布局：同一行的单元格高度是相等的

   ```
   TODO
   ```

   