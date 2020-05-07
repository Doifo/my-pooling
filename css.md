#### IE盒模型和W3C标准盒模型的区别

（1）W3C标准盒模型：属性width，height只包含内容content，不包含border和padding 

（2）IE盒模型：属性width，height包含content、border和padding，指的是content +padding+border。



#### 清除浮动

1. 浮动元素后使用带clear属性的空元素
2. 给浮动元素的容器添加overflow:hidden;或overflow:auto;
3. 给浮动元素的容器也添加上浮动属性即可清除内部浮动
4. 给浮动元素的容器添加一个clearfix的class，然后给这个class添加一个:after伪元素实现元素末尾添加一个看不见的块元素（Block element）清理浮动



#### ：：与：的区别

：：指伪元素，：指伪类

伪元素是一个附加至选择器末的关键词，允许你对被选择元素的**特定位置**修改样式

伪类是添加到选择器的关键字，指定要选择的元素的**特定状态**



#### display与visibility

visibility:hidden可以隐藏某个元素，但隐藏的元素仍需占用与未隐藏之前一样的空间。

display:none可以隐藏某个元素，且隐藏的元素不会占用任何空间。也就是说，该元素不但被隐藏了，而且该元素原本占用的空间也会从页面布局中消失。



#### css选择器

id选择器

类选择器

标签选择器

通配符选择器

伪类选择器

伪元素选择器

属性选择器` [attr = value]`

后代选择器` 空格`

子（直接后代）选择器`ul>li`

兄弟选择器（`A~B` 选择`A`元素之后所有同层级`B`元素）

相邻兄弟选择器`li+a`



#### css哪些属性可以继承

每个CSS属性定义的概述都指出了这个属性是默认继承的，还是默认不继承的。这决定了当你没有为元素的属性指定值时该如何计算值。  

当元素的一个继承属性没有指定值时，则取父元素的同属性的计算值。只有文档根元素取该属性的概述中给定的初始值（这里的意思应 该是在该属性本身的定义中的默认值）。 

当元素的一个非继承属性（在Mozillacode里有时称之为resetproperty）没有指定值时，则取属性的初始值initialv alue（该值在该属性的概述里被指定）。  

有继承性的属性：  

（1）字体系列属性 font、font-family、font-weight、font-size、font-style、font-variant、font-stretch、font-size-adjust  

（2）文本系列属性 text-indent、text-align、text-shadow、line-height、word-spacing、letter-spacing、 text-transform、direction、color

（3）表格布局属性 caption-sideborder-collapseempty-cells  

（4）列表属性 list-style-type、list-style-image、list-style-position、list-style  

（5）光标属性 cursor  

（6）元素可见性 visibility  

（7）还有一些不常用的；speak，page，设置嵌套引用的引号类型quotes等属性   

注意：当一个属性不是继承属性时，可以使用inherit关键字指定一个属性应从父元素继承它的值，inherit关键字用于显式地 指定继承性，可用于任何继承性/非继承性属性。



#### 关于伪类 LVHA 的解释

a标签有四种状态：链接访问前、链接访问后、鼠标滑过、激活，分别对应四种伪类:link、:visited、:hover、:active；  当链接未访问过时：  （1）当鼠标滑过a链接时，满足:link和:hover两种状态，要改变a标签的颜色，就必须将:hover伪类在:link伪 类后面声明； （2）当鼠标点击激活a链接时，同时满足:link、:hover、:active三种状态，要显示a标签激活时的样式（:active）， 必须将:active声明放到:link和:hover之后。因此得出LVHA这个顺序。  当链接访问过时，情况基本同上，只不过需要将:link换成:visited。  这个顺序能不能变？可以，但也只有:link和:visited可以交换位置，因为一个链接要么访问过要么没访问过，不可能同时满足， 也就不存在覆盖的问题。



#### 居中div

1. 给 div 设置一个宽度，然后添加 margin:0auto 属性

2. 父元素：text-align: center;          div：display: inline-block;

3. 让绝对定位的 div 居中

   ```
   div {
     position: absolute;
     width: 300px;
     height: 300px;
     margin: auto;
     top: 0;
     left: 0;
     bottom: 0;
     right: 0;
     background-color: pink; /*方便看效果*/
   }
   
   div{
       position:absolute;/*绝对定位*/
       width:500px;
       height:300px;
       top:50%;
       left:50%;
       margin:-150px00-250px;/*外边距为自身宽高的一半*/
       background-color:pink;/*方便看效果*/
   }
   
   div {
     position: absolute; /*相对定位或绝对定位均可*/
     width: 500px;
     height: 300px;
     top: 50%;
     left: 50%;
     transform: translate(-50%, -50%);
     background-color: pink; /*方便看效果*/
   }
   ```

4. flex布局 `align-items:center ;justify-content:center`



#### css3新特性

新增各种CSS选择器    （:not(.input)：所有class不是“input”的节点） 

圆角        （border-radius:8px） 

多列布局    （multi-columnlayout） 

阴影和反射    （Shadow\Reflect） 

文字特效        （text-shadow） 

文字渲染        （Text-decoration） 

线性渐变        （gradient） 

旋转            （transform） 

缩放，定位，倾斜，动画，多背景 

例如：transform:\scale(0.85,0.90)\translate(0px,-30px)\skew(-9deg,0deg)\Animation:



#### CSS 多列等高如何实现

（1）利用padding-bottom|margin-bottom正负值相抵，不会影响页面布局的特点。设置父容器设置超出隐藏（overflow: hidden），这样父容器的高度就还是它里面的列没有设定padding-bottom时的高度，当它里面的任一列高度增加了，则 父容器的高度被撑到里面最高那列的高度，其他比这列矮的列会用它们的padding-bottom补偿这部分高度差。  

（2）利用table-cell所有单元格高度都相等的特性，来实现多列等高。  

（3）利用flex布局中项目align-items属性默认为stretch，如果项目未设置高度或设为auto，将占满整个容器的高度 的特性，来实现多列等高。



#### li之间存在空白间隔

浏览器会把inline元素间的空白字符（空格、换行、Tab等）渲染成一个空格。而为了美观。我们通常是一个<li>放在一行， 这导致<li>换行后产生换行字符，它变成一个空格，占用了一个字符的宽度。  解决办法：  

（1）为<li>设置float:left。不足：有些容器是不能设置浮动，如左右切换的焦点图等。  

（2）将所有<li>写在同一行。不足：代码不美观。  

（3）将<ul>内的字符尺寸直接设为0，即font-size:0。不足：<ul>中的其他字符尺寸也被设为0，需要额外重新设定其他 字符尺寸，且在Safari浏览器依然会出现空白间隔。  

（4）消除<ul>的字符间隔letter-spacing:-8px，不足：这也设置了<li>内的字符间隔，因此需要将<li>内的字符 间隔设为默认letter-spacing:normal。



#### 为什么要初始化 CSS 样式

因为浏览器的兼容问题，不同浏览器对有些标签的默认值是不同的，如果没对CSS初始化往往会出现浏览器之间的页面显示差异。



####  visibility 属性有个 collapse 属性值

（1）对于一般的元素，它的表现跟visibility：hidden;是一样的。元素是不可见的，但此时仍占用页面空间。  

（2）但例外的是，如果这个元素是table相关的元素，例如table行，tablegroup，table列，tablecolumngroup，它的 表现却跟display:none一样，也就是说，它们占用的空间也会释放。  

在不同浏览器下的区别：  

在谷歌浏览器里，使用collapse值和使用hidden值没有什么区别。  

在火狐浏览器、Opera和IE11里，使用collapse值的效果就如它的字面意思：table的行会消失，它的下面一行会补充它的位 置



#### 图片 base64 编码的优点和缺点

base64编码是一种图片处理格式，通过特定的算法将图片编码成一长串字符串，在页面上显示的时候，可以用该字符串来代替图片的 url属性。  

使用base64的优点是：  （1）减少一个图片的HTTP请求  

使用base64的缺点是：  

（1）根据base64的编码原理，编码后的大小会比原文件大小大1/3，如果把大图片编码到html/css中，不仅会造成**文件体 积的增加**，影响文件的加载速度，还会增加浏览器对html或css文件解析**渲染的时间**。  

（2）使用base64**无法直接缓存**，要缓存只能缓存包含base64的文件，比如HTML或者CSS，这相比域直接缓存图片的效果要差很多。  

（3）兼容性的问题，ie8以前的浏览器不支持。  一般一些网站的小图标可以使用base64图片来引入。



#### CSS的长度单位

em 相对父级字体大小

rem 相对根元素字体的大小

vw,vh 相对视窗的宽高

vmin，vmax vm和vh中较小（大）的

ex 相对与当前字体x字母的高度

ch 相对与当前字体0的宽度

%

px

绝对长度：cm，mm，in，pt，pc



#### sass



#### z-index

对于一个已经定位的盒子（即其 `position` 属性值不是 `static`，这里要注意的是 CSS 把元素看作盒子），`z-index` 属性指定：

1. 盒子在当前堆叠上下文中的堆叠层级。
2. 盒子是否创建一个本地堆叠上下文。