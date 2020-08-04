常用属性：

​	-color

​		transparent：透明

​	-opacity

​	-font--大小/行高 字体

​		-font-style：文本斜体

​		-font-weight：设置文本的粗细

​		-font-size：字体大小

​		-font-family：字体种类

-文本属性：

​	-white-space-文字空白处的处理

​	-direction-文本的方向

​	-text-align-水平对齐方式

​	-line-height-文本行高

​	-vertical-align-文本所在行高的垂直对齐方式

​	-text-indent-文本缩进

​	-letter-spacing-字母间的空白

​	-word-spacing-单词间的空白

​	-text-transform-文本的大小写

​	-text-overflow-文本溢出样式

​	-text-decoration-文本的装饰

​	-word-wrap-自动换行

-背景属性:

​	-background-image:

​	-background-position:

​	-background-repeat:

​	--background

-z-index：仅在定位元素上有效，position



布局：	

-flex布局：只要设置display：flex

​	-一些属性：flex-direction-盒子的排列方向，flex-wrap-控制是否换行（这两个可以合并使用一个flex-flow）justify-content-盒子内元素在横轴方向上的对齐方式，align-items-多行的flex容器，在纵轴上的对齐方式（这两个可以合并使用一个align-contant）

​	-flex项目属性(对一个小格子的控制)：order：数字-用来个盒子进行编号。flex-grow：flex-shrink-项目在多余的空间中如何放大缩小。flex-basis：指定项目的初始大小。align-self：控制单个项目沿着纵轴上的方向。

-grid布局：设置display：grid

​	-属性：grid-template-columns-一个grid的横向上的宽，grid-template-rows-竖向上的高，(可以随意的控制格子的大小)。 grid-column-以竖向划分。如果是3*3的区域，那么column的数量就有4个，grid的竖向对个格子的大小进行划分，从start开始，到end结束，(1/4--从第一根开始到第四根结束。)grid-row-以横向划分，其余均同上。





##### 预处理语言-less：

-在vue框架中添加scoped属性，表示该style标签所包含的样式仅仅作用于当前的vue组件，这样不会产生样式的全局污染。lang标签则是规定了使用哪种css预处理语言。

-less在css语言的基础上增加了，变量，混合(mixin)，函数等功能。

-格式：@变量名：值

-混合：将一组属性从一个规则集包含到另一个规则集中。.class{style...}  使用--.class1{ style... ;  .class(); }，这样，class1就可以使用class的样式。

​	可以将伪选择器和混入一起使用。.class{ style...  &:after{  } }(&表示当前选择器的父级)

`.clearfix {  display: block;  zoom: 1;   &:after {    content: " ";    display: block;    font-size: 0;    height: 0;    clear: both;    visibility: hidden;  } }`

-嵌套：就是把可以复用的样式写在一起，格式---#最外层的块{ 样式... .下面的class{ class自己的样式 }}

​	@规则可以和选择器以相同的方式进行嵌套

`.component {  width: 300px;  @media (min-width: 768px) {    width: 600px;    @media  (min-resolution: 192dpi) {      background-image: url(/img/retina2x.png);    }  }  @media (min-width: 1280px) {    width: 800px;  } }`

-运算&函数：运算--可以做四则，属性和颜色的运算。calc()不进行运算，但在嵌套函数中，会计算变量和数学公式的值。？？？

-转义：允许你使用任意字符串作为属性或变量值。格式---@变量名：~“字符串”，编译后都会原样输出。



