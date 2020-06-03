## 选择器

* 子元素选择器：/#father div{...} 选择 id 为father的元素下的所有div元素
* 相邻选择器：\#lv+div {...} 选择id为lv相邻的下一个兄弟元素div
* 群组选择器：h3,div,p,span {...}

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

所有元素都可看做是一个盒子，占据空间，盒子由content内容、padding内边距、margin外边距、border组成。内容有3个属性：width、height、overflow(指定超出如何处理)

宽高是针对内容区的，只有块元素能设置宽高，行内元素无法设置

```
div {display: inline-block} /* 将块元素转换为inline-block元素 */
```

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

行内元素可以和其他元素并列，块元素可以有宽高

block 呈现为块元素

inline 呈现为行内元素

inline-block 让元素既可以和其他元素并列，又可以设置宽高

none 不显示，不占据空间（visibility:hidden 不显示，但是占据空间）