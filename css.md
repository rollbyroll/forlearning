boxsizing:border-box:宽度和高度设置整个盒子可见框的大小

outline:设置一个轮廓，不会影响页面布局（不挤元素）

box-shadow:20px 10px 20px orange:设置阴影。第一个设置水平像素偏移，第二个垂直，第三个设置颜色模糊效果（模糊半径），颜色可以设置rgba设置透明效果

boder-radius:设置圆角，一个元素就是圆角，两个就是椭圆角，如果元素50%，那么就是呈现的就是一个圆 元素/元素：表示横向是第一个元素的值第二个是纵向的值

属性选择器(平时好像没怎么用到)

语法：[属性名]选择含有指定属性的元素

[属性名=属性值]选择含有指定属性和属性值的元素

[属性名^=属性值]选择属性值以指定开头的元素

[属性名$=属性值]选择属性值以指定值结尾的元素

[属性名*=属性值]悬念则属性值中含有某值的元素

例子p[tittle]{

color：orange;

}

子元素选择器：父元素>子元素

后代选择器：祖先 后代

兄弟选择器：兄弟1 + 兄弟2 还有一种是选择后面所有兄弟：兄弟1~兄弟x

###### 伪类选择器：一般以  ：开头

：first-child 第一个子元素

：last-child最后一个子元素

：nth-child(x)选中第x个子元素

***x:第x个，范围从0到正无穷***

***2n或者even：选中偶数位的元素***

***2n+1或者odd：选中奇数位的元素***

：first-of-type同类型中的第一个子元素

：last-of-type同类型中的最后一个子元素

：nth-of-type(n)选中同类型中的第n个子元素

：not()否定伪类，将符合条件的元素从选择器中去除

：link未访问的链接

：visited已访问的链接：这个伪类只能修改链接的颜色

：hover鼠标悬停的链接

：active鼠标点击的链接

###### 伪元素选择器

以：：开头

：：first-letteer表示第一个字母

：：first-line第一行

：：selection表示选中的内容

：：before元素的开始

：：after元素的最后

：：before和：：after必须结合content属性来使用

###### **样式概念**

em：em是相对元素的字体大小来计算的

rem：rem是相对根元素的字体大小来计算：可以在style样式里面吧html的fontsize改

###### **边框**

solid实线

dotted点状虚线

dashed方块虚线

double双实线

###### **overflow处理元素溢出**

使用overflow / overflow-x / overflow-y属性来设置父元素处理溢出的子元素

可选值：

visible 溢出内容会在父元素外部位置显示，是默认值

hidden 溢出内容会被裁剪，不会显示

scroll生成两个滚动条，通过滚动条来查看完整的内容

auto 自动生成荷属的滚动条

###### **盒模型**

visibility用来设置元素的显示状态

visible 默认值，元素在页面中正常显示

hidden元素在页面中隐藏不显示，但是依然占据页面的位置（display：none 不会占位置）

***box-sizing用来设置盒子尺寸的计算方式（宽和高）***

可选值

content-box默认值，宽度和高度用来设置内容区的大小

border-box宽度和高度用来设置整个盒子大小

***轮廓***

outline用来设置元素的轮廓线，用法和border一样

和边框不同的是，轮廓不会影响到可见框的大小

***阴影***

box-shadow用来在一个元素框架外设置阴影效果

第一个值：水平偏移量-设置阴影的水平位置

（正数向右）

第二个值；垂直偏移

（正值向下）

第三个值：模糊半径

第四个：阴影的颜色

***圆角***

border-radius使一个元素的外边框的角变圆

有分top   bottom  left  right  

设置为50%就是一个圆

四个值：左上  右上  右下  左下  

三个值：左上  右上左下  右下

两个值： 左上右下  右上左下

一个：全部同时设置

与border不同的是，border是从上开始顺时针设置，而圆角是从左上角开始

***解决高度塌陷***

clear：清除浮动元素对当前元素产生的影响

可选值

left

right

both 清除两侧影响较大的一侧的元素影响

**第一种**

使用伪元素after

在父元素里面添加如下代码

父元素::after{

content:";  设置一个没有属性的值

clear:both;  清除对自身影响最大的浮动

display:block;  展示为块元素

}

**第二种**

父元素::before{

content:";

display:table;

}

高度塌陷问题一般用after

外边距重叠问题一般用before；

具体我也不知道为什么》~《

**第三种**（**完美的方法**）****

使用clearfix

.clerafix::before(解决外边距重叠问题)

.clearfix::after{(解决高度塌陷问题)

content:";

display:table;

clear:both;

}

定位的简介（position）

| 可选值   | 含义                             |
| -------- | -------------------------------- |
| static   | 不开启定位，元素是静置的，默认值 |
| relative | 开启元素的相对定位               |
| absolute | 开启元素的绝对定位               |
| fixed    | 开启元素的固定定位               |
| sticky   | 开启元素的粘滞定位               |
|          |                                  |

相对定位：不设置偏移值不会变化，相对定位参照与自身原始位置定位

​					  相对定位会提升元素的层级（覆盖其他元素）

​					  相对定位不会改变元素的性质：块还是块，行内还是行内 

绝对定位：不设置偏移值不会变化，相对定位参照与自身原始位置定位

​					  开启绝对定位后元素会从文档流中脱离

​					  绝对定位会改变元素的性质：行内变成块，块宽高被内容撑开

​					  开启后会是元素提升一个层级

​					  相对于其包含块进行定位（离档当前元素最近的开启了定位的祖先元素）

水平居中：     /* 左右外边距设置为auto */
     					   margin-left: auto;
    					    margin-right: auto;
   					     /* 绝对定位 */
     					   position: absolute;
 					       left: 0;
					        right: 0;

垂直居中：	上面需要设置块的样式，水平居中也要

​						 margin-top: auto;
 					   margin-bottom: auto;
  					  /* 绝对定位 */
  					  position: absolute;
 					   top: 0;
​					    bottom: 0;

​						加上left:0  right:0就是水平垂直居中了

固定定位：永远参照可视窗口进行定位，不会随着滚动条改变

粘滞定位：设置top之类的属性后（比如top：50px）往下滚动后

​					  一开始会随着滚动而改变，而到top50px位置就定在那了

###### 5. 几种定位的对比

我们通过上面的学习，知道`position`属性有五个可选值

但`static`是默认值，即不开启定位，所以我们只需要对比4种定位方式即可

| 定位方式               | 是否不设置偏移量，元素不会发生改变 | 是否脱离文档流 | 是否改变元素性质 | 是否提升元素层级 | 参考系                     |
| ---------------------- | ---------------------------------- | -------------- | ---------------- | ---------------- | -------------------------- |
| ``relative（相对定位） | √                                  | ×              | ×                | √                | 参照于元素在文档流中的位置 |
| ``absolute（绝对定位） | ×                                  | √              | √                | √                | 参照于其包含块             |
| ``fixed（固定定位）    | ×                                  | √              | √                | √                | 参照于浏览器的视口         |
| ``sticky（粘滞定位）   | ×                                  | √              | √                | √                | 参照于浏览器的视口         |

z-index 值越大层级越高（在其他比它低层级的上面覆盖）

### 字体

font-family字体族：可以同时指定多个字体，字体之间用‘，’隔开

@font-face可以将服务器的字体提供给用户使用

@font-face {
     指定字体名字 */
    font-family: 'myFont1';
    /* 服务器中字体路径 */
    src: url('/font/ZCOOLKuaiLe-Regular.woff'),
        url('/font/ZCOOLKuaiLe-Regular.otf'),
        url('/font/ZCOOLKuaiLe-Regular.ttf') format('truetype');/* 指定字体格式，一般不写 

**字体一些属性**：

font-variant：normal（默认）/smoll-caps（把字体小写变大写，大写变更大写）

**文本对齐方式**：****

**text**-**align******设置文本水平对齐****

left 左对齐			right  右对齐

center 居中对齐   		justify 两端对齐

**vertical**-align**设置元素垂直对齐**

baseline 基线对齐      		top  顶部对齐

bottom  底部对齐  			 middle 居中对齐（基线高度+x的高度/2）

图片去缝：图片属于替换元素，特点与文本一致，也有自己的基线，默认也是基线对齐。而基					 线位置不在最底部，所以会出现缝隙，使用vertical-align：top去除

##### 背景：

- `background-color` 设置背景颜色

- `background-image` 设置背景图片 

- - 如果背景图片大小小于元素，则背景图片会自动在元素中平铺将元素铺满

- - 如果背景图片大小大于元素，则背景图片一部分会无法完全显示

- - 如果背景图片大小等于元素，则背景图片会直接正常显示

- `background-repeat` 设置背景图片的重复方式 

- - `repeat` 默认值，背景图片沿着x轴和y轴双方向重复

- - `repeat-x` 背景图片沿着x轴方向重复

- - `repeat-y` 背景图片沿着y轴方向重复

- - `no-repeat` 背景图片不重复

- `background-position` 设置背景图片的位置 

- - 通过`top` `left` `right` `bottom` `center`几个表示方位的词来设置背景图片的位置：使用方位词时必须要同时指定两个值，如果只写一个则第二个默认就是`center`

- - 通过偏移量来指定背景图片的位置：水平方向偏移量、垂直方向变量

- `background-clip` 设置背景的范围 

- - `border-box` 默认值，背景会出现在边框的下边

- - `padding-box` 背景不会出现在边框，只出现在内容区和内边距

- - `content-box` 背景只会出现在内容区

- `background-origin` 背景图片的偏移量计算的原点 

- - `border-box` 背景图片的变量从边框处开始计算

- - `padding-box` 默认值，`background-position`从内边距处开始计算

- - `content-box` 背景图片的偏移量从内容区处计算

- `background-size` 设置背景图片的大小 

- - 第一个值表示宽度，第二个值表示高度；如果只写一个，则第二个值默认是`auto`

- - `cover` 图片的比例不变，将元素铺满

- - `contain` 图片比例不变，将图片在元素中完整显示

- `background-attachment` 背景图片是否跟随元素移动 

- - `scroll` 默认值，背景图片会跟随元素移动

- - `fixed` 背景会固定在页面中，不会随元素移动

可以同时设置背景图片和背景颜色，这样背景颜色将会成为图片的背景色

background的简写属性：

**注意**

- `background-size`必须写在`background-position`的后边，并且使用/隔开`background-position/background-size`

- `background-origin background-clip` 两个样式，`orgin`要在`clip`的前边

线性渐变：background-image：linear-gradient（渐变方向（可不设置），颜色，可以设       					 置无限个）

渐变方向属性：to left / to right /to bottom/ deg(表示度数)/turn(表示圈)

可以平铺的线性渐变：background-image：`repeating-linear-gradient(颜色（可以添加像素大小，如50px），颜色（同上）)` 颜色重复

径向渐变；background-image：radial-gradient（（可以选择设置形状或者位置,位置前面					 加at），颜色前面都可以加  at位置，颜色）

形状：circle圆形    	ellipse：椭圆

位置：top   right   left   center   bottom

大小：（后面都加at像素大小位置）

- `closest-side` 近边

- `farthest-side` 远边

- `closest-corner` 近角

- `farthest-corner` 远角

径向渐变的渐变方向以圆心为起点，往四周扩散

### **表格**

通过table标签创建一个表格

在table中使用tr表示表格中的一行，有几个tr就有几行

在tr中使用td表示一个单元格，有几个td就有几个单元格

rowspan纵向的合并单元格

colspan横向的合并单元格



可以将一个表格分成三部分

头部 thead

主体 tbody

底部 tfoot

th表示头部的单元格

在之中使用到一个“border-collapse：collapse来合并边框

​									 border-spacing：指定边框之间的距离



表单@form action的使用

<form action="niubi.html" method="get">
    <p>
        这里输入名字：<input type="text"name="名字"(要提交服务器就需要设置name)>
    </p>
    <input type="submit" value="提交"/>
</form>

文本框  input type ="text "

密码框                               password

提交按钮                           submit

单选框                               radio

多选框                               checkbox 单选框和多选框在value后面加checked为默认选择

下拉列表

<select name = "haha">
    <option value="i">选项一</option>
    <option value="ii"selected//默认选择>选项二</option>
    <option value="iii">选项三</option>
</select>

按钮

<button type="submit">提交</button>
<button type="reset">重置</button>
<button type="button">普通按钮</button>

br标签是换行

<input type="submit">

<input type="reset">

<input type="button" value="按钮">

这三个效果和上面三个效果是一致的

区别在于input是自闭和标签不需要</input>结束

botton是成对出现的，使用起来更加灵活可以嵌套其他标签

### 过渡

transition-property  指定要执行过度的属性

​											多个属性用，隔开

​											如果所有属性要过度则使用all关键词

​											过度是一个有效数字向另一个有效数值之间的过度

transition-duration：指定过度效果的持续时间

transition-delay：过度的延迟，等待一段时间

transition-timing-funciton：过度的时序函数

* linear 匀速运动
* ease 默认值 慢速开始，先加速后减速
* ease-in加速运动
* ease-out 减速运动
* ease-in-out 先加速后减速
* cubic-bezier()来指定时序函数 用好几个值来做贝塞尔曲线https://cubic-bezier.com
* steps()分布执行过度效果可以设置第二个值
* * end在时间结束时执行过度（默认
  * start在时间开始时执行过度

*  transition简写属性如果要写延迟，则两个时间中第一个是持续时间，第二个是延迟

  

### 动画

和过度类似，都是可以实现一些动态效果不同的是：

* 过度需要在某个属性发生变化时才会触发
* 动画可以自动触发动态效果

设置动画效果，需要先设置一个关键帧

@keyframes test{

​		from{

​			margin-left:0;

​		}

​		to{

​			margin-left:900px

​		}

}

`animation-name` 指定动画的关键帧名称

`animation-duration`：指定动画效果的持续时间

`animation-delay`：动画效果的延迟，等待一段时间后在执行动画

`animation-timing-function`：动画的时序函数

`animation-iteration-count` 动画执行的次数

- `infinite` 无限执行

`animation-direction` 指定动画运行的方向

- `normal` 从`from`向`to`运行，每次都是这样，默认值

- `reverse` 从`to`向`from`运行，每次都是这样

- `alternate` 从`from`向`to`运行，重复执行动画时反向执行

- `alternate-reverse` 从`to`向`from`运行，重复执行动画时反向执行

`animation-play-state` 设置动画的执行状态

- `running` 动画执行，默认值

- `paused` 动画暂停

`animation-fill-mode` 动画的填充模式

- `none` 动画执行完毕，元素回到原来位置，默认值

- `forwards` 动画执行完毕，元素会停止在动画结束的位置

- `backwards` 动画延时等待时，元素就会处于开始位置

- `both` 结合了`forwards`和`backwards`

animation-name: test;
animation-duration: 2s;
animation-delay: 2s;
animation-timing-function: linear;
animation-iteration-count: infinite;
animation-direction: alternate;
animation-fill-mode: both; */

简写属性animation: test 2s 2s linear infinite alternate both;

### 变形：平移 旋转与缩放

变形不会影响页面布局

transform用来设置元素的变形效果

##### 平移

- `translateX()` 沿着x轴方向平移

- `translateY()` 沿着y轴方向平移

- `translateZ()` 沿着z轴方向平移平移元素

z轴平移需要在html设置perspective：xxpx属性（视距

###### 旋转

旋转可以使元素沿着x y或z轴旋转指定的角度

- `rotateX(里面可以设置度数deg)`

- `rotateY()`

- `rotateZ()`

###### 缩放

* scalex() 水平方向缩放
* scaleY() 垂直方向缩放
* scale() 双方向的缩放

###### 弹性盒

flex可以使元素具有弹性，让元素可以跟随页面的大小改变而改变

通过display来设置弹性容器

display：flex设置为块级弹性容器

display：inline-flex设置为行内的弹性容器

主轴与侧轴

主轴：弹性元素的排列方向称为主轴

侧轴：与主轴垂直方向的成为侧轴

**主轴排列方式**：****

flex-direciton指定容器中弹性元素的排列方式

row默认  弹性元素在容器中水平排列

row-reverse弹性元素在容器中反向水平排列

column 纵向排列（自上向下

column-reverse弹性元素反向排列（自下而上



flex-wrap设置弹性元素是否在弹性容器中自动换行

* nowrap默认，元素不会自动换行

* wrap 元素沿着辅轴方向自动换行

  

flex-flow是wrap和direction的简写属性



justify-content如何分配主轴的空白空间（如何排列

flex-start元素沿着主轴起边排列

flex-end沿着主轴终边排列

center元素居中排列

space-around 空白分布到元素两侧

space-between空白均匀分布到元素间

space-evenly空白分布到元素的单侧



辅轴对齐

alignitems元素在辅轴上如何对齐

stretch 默认，将元素的长度设置为相同的值

flex-start元素不会拉伸，沿着辅轴起边对齐

flex-end沿着辅轴的终边对齐

center居中对齐

baseline极限对齐

空白空间

align-content如何分配辅轴上的空白空间（辅轴元素如何排列

flex-start元素沿着辅轴起边排列

flex-end元素沿着辅轴终边排列

center 元素居中排列

spacearound 空白分布到元素两侧

space-bettween空白均匀分布到元素间

space-evenly空白分布到元素的单侧

弹性居中：利用弹性盒对元素进行水平垂直居中

justify-content：center

align-items：center

###### 伸展系数

flex-grow指定弹性元素的伸展系数，默认为0

当父元素有对于空间，子元素如何伸展

父元素的剩余空间会按照比例进行分配

可以对子元素单独设置伸展系数分配空白空间

**缩减系数**

flex-shrink指定弹性元素的收缩系数，默认为1

当元素中的空间不足以容纳所有子元素时如何对子元素进行收缩

缩减系数的计算方式复杂，根据缩减系数和元素大小进行计算

### 基础长度

`flex-basis` 指定的是元素在主轴上的基础长度

- 如果主轴是横向的，则该值指定的就是元素的宽度

- 如果主轴是纵向的，则该值指定的就是元素的高度

- 默认值是`auto`，表示参考元素自身的高度或宽度

- 如果传递了一个具体的数值，则以该值为准

**简写属性**

flex`可以设置弹性元素所有的三个样式 `flex: 增长 缩减 基础

- `initial`：`flex: 0 1 auto`

- `auto`：`flex: 1 1 auto`

- `none`：`flex: 0 0 auto` 弹性元素没有弹性

###### 排列顺序

order决定弹性元素的排列顺序

可选值：正整数

覆盖辅轴

align-self覆盖当前元素上的align-items

