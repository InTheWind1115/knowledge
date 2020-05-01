1、css简介[code01.html]
    语法规范：
        选择器 + 声明样式

        属性和属性值以键值对方式出现，用：隔开，后面一定要加分号;

    代码规范：
        样式格式书写：
            紧凑格式
                h2 {color: red;font-size: 12px;}

            展开风格: //推荐此方式
                h2 {
                    color: red;
                    font-size: 12px;
                }

        样式大小写：
            采用小写字母来写

        空格规范：
            属性值前面，冒号后面添加一个空格
            选择器和大括号之间也保留一个空格

2、选择器的作用：
    根据不同需求把不同的标签选出来这就是选择器的作用，简单来说就是选择标签

3、基础选择器
    标签选择器
        标签名 {
            属性：属性值;
            属性：属性值;
            属性：属性值;
            ...
        }

    类选择器
        .类名 {
            属性：属性值;
            属性：属性值;
            属性：属性值;
            ...
        }

        需要配合标签的class属性
            
        一个标签可以有多个类名:
            <div class="red green"></div> //用空格隔开

    id选择器
        #id名 {
            属性值: 属性值;
            属性值: 属性值;
            属性值: 属性值;
            ...
        }

    通配符选择器
        * {
            属性值: 属性值;
            属性值: 属性值;
            属性值: 属性值;
            ...
        }

        选择所有的标签

4、css字体属性
    字体系列:
        font-family: ...;

        如果写了多个字体，系统会看您有没有装载此字体，前面的优先使用。

    字体大小：
        font-size: 100px;

    字体粗细：
        font-weight: 

    文体样式：
        font-style: ...; //italic变倾斜 normal不倾斜

        //设置斜体...之类的效果

    字体复合属性
        body {
            font: font-style font-weight font-size/line-height font-family;
        }

        //代码简写 注意顺序不能改变

        不需要设置的属性可以省略，但必须保留font-size 和 font-family

5、文本属性
    文本颜色：
        color: red;
        color: #ffff00; //十六进制用的最多
        color: rgb(220, 0, 230);

    对齐文本：
        text-align: ...;

        只能设置水平对齐方式

        值：
            center
            left //默认值
            right

    装饰文本：
        text-decoration: ...;

        可以给文本添加下划线，删除线，上划线

        值：
            none //默认值
            underline 下划线
            overline 上划线
            line-through 删除线

    文本缩进
        用来指定文本的第一行的缩进，通常是段落首行的缩进

        text-indent: 20px;
        text-indent: 2em; //em是一个相对单位，就是当前元素（文字）的大小，2em就是两个文字的大小

    行间距
        line-height: 26px;

        组成：
            上间距
            文本高度
            下间距

        实际改变的是上下间距的大小

6、css的引入方式
    行内样式表
        适合修改一些简单样式的时候。

        <p style="color: red; font-size: 25px"></p>

    内部样式表
        把所有的css代码抽出来，放到一个style标签里面。


    外部样式表 //吐血推荐
        适合于样式比较多的情况，核心是样式单独写到css文件中，之后把css文件引入到HTML页面中使用。

        步骤；
            新建一个后缀为.css样式文件，把所有css代码都放入此文件中

            在html文件中使用<link>标签引入，<link rel="stylesheet" href="css文件路径">

7、Emmet语法
    快速生成HTML结构
        生成标签 直接输入标签名按tab键即可 比如 div 然后 tab键，就可以生成<div></div>

        如果想要生成多个相同标签 加上*就可以了 比如 div*3 就可以快速生成3个div

        如果有父子关系级的标签，可以用> 比如 ul > li 就可以了

        如果有兄弟关系的标签 用 + 就可以了 比如 div + p

        如果生成带有类名或者id名字的，直接写 .demo 或者 #two tab键就可以了

        如果生成的div类名是有顺序的，可以用自增符号$

        如果想要在生成的标签内部写内容可以用 {} 表示

    快速生成css结构

8、复合选择器
    后代选择器
        语法规范：
            元素1 元素2 {
                样式说明;
            }
        
            元素2必须是元素1的后代

            元素2可以是儿子，也可以是孙子等...

            元素1 元素2可以是类选择器 标签选择器 id选择器

    子选择器
        语法规范：
            元素1>元素2 {
                样式说明;
            }

            选择的是亲儿子，跟孙子没有关系

    并集选择器
        语法格式
            元素1,
            元素2,
            元素3... {
                样式声明;
            }

            任何选择器都可以成为并集选择器的一部分

    伪类选择器
        语法格式
            a:link      选择所有未被选择的链接
            a:visited   选择所有访问过的链接
            a:hover     选择鼠标指针正在放在上面的标签
            a:active    选择鼠标正在按下还没有弹起鼠标的链接

            千万注意：按照上面四种顺序来 不能乱着来

    :focus伪类选择器
        语法格式
            input:focus {
                样式说明;
            }

        :focus伪类选择器用于选择获得焦点的表单元素

        焦点就是光标，一般情况<input>类表单元素才能获取，因此这个选择器也主要针对于表单元素来说。

9、元素显示模式
    什么是元素的显示模式：
        就是元素(标签)以什么方式进行显示

    块元素：
        <h1> ~ <h6>
        <p>
        <div>
        <ul>
        <li>....等

        特点：
            比较霸道，自己独占一行

            高度 宽度 外边距以及内边距都可以控制

            宽度默认是容器（父级宽度）的100%

            是一个容器及盒子，里面可以放行内或者块级元素

        注意：
            文字类的元素内不能使用块级元素，比如<p>标签 和 <h1>---<h6>

    行内元素：
        <a> <strong> <b> <em> <i> <del> <s> <ins> <u> <span>

        特点：
            相邻行内元素在一行上，一行可以显示多个

            高度 宽度直接设置是无效的

            默认宽度就是它本身内容的宽度

            行内元素只能容纳文本或其他行内元素

        注意：
            链接里面不能再放链接

            链接<a>标签里面可以放置块级元素，但是给<a>转换一下块级模式最安全

    行内块元素：
        <img /> <input /> <td />

        特点：
            和相邻行内元素（行内块）在一行上，但是他们之间会有空白缝隙，一行可以显示多个（行内元素特点）

            默认宽度就是它本身内容的宽度（行内元素特点）

            高度 行高 外边距以及内边距都可以控制（块级元素特点）

    元素显示模式转换：
        转换为块级元素：
            display: block;

        转换为行内元素：
            display: inline;

        转换为行内块元素：
            dispaly: inline-block;
    
    一个小技巧 单行文字垂直居中
        让文字的行高等于盒子的高度
            a {
                display: block;
                height: 40px;
                line-height: 40px;
            }

        如果文字的行高小于或大于盒子的高度，那么从上面开始贴合

10、css的背景
    背景颜色：
        background-color: 值;

        值默认是transparent
    
    背景图片：
        background-image: none | url(URL);

        背景平铺：
            background-repeat: repeat | no-repeat | repeat-x | repeat-y;

            默认情况下背景图片是平铺的repeat

    页面元素既可以添加背景颜色又可以添加背景图片，只不过背景图片会压着背景颜色

    背景图片位置：
        background-positon: x y;

        x y可以使用方位名词和精确单位

        方位名词：
            如果x y都是方位名词，那么x y前后位置无关

            如果只指定了一个方位名词，那么另外一个默认居中

            top | bottom | left | center | right 

        精确单位：
            如果x y都是精确单位，那么x y顺序要严格要求

        混合单位：
            方位名词和精确单位可以混合使用

    背景图像固定：
        background-attachment: scroll | fixed;

        默认是scroll 背景图片随着滚动
        fixed        背景图片固定

    背景复合写法：
        background: 背景颜色 背景图片地址 背景平铺 背景图像滚动 背景图片位置;

        顺序没有要求，但是开发时一般这么写。 

    背景色半透明：
        background: rgba(0, 0, 0, 0.3);
            最后一个参数是a 是alpha透明度的简写 取值范围为0.0 - 1.0 0为全透明 1为不透明

            可以省略0 例如：rgba(0, 0, 0, .3);

        背景半透明是指盒子背景半透明，盒子里面的内容不受影响。

11、css的三大特性
    层叠性：
        样式冲突，就近原则

        样式不冲突，不会层叠

    继承性：
        子标签会继承父标签的一些样式，例如文本颜色和大小

        text- font- line- 这些开头的都可以继承 color也可以

        行高的继承性：
            body {
                font: 12px/1.5 'Microsoft YaHei';
            }

            行高可以跟单位也可以不跟单位，不跟单位指定行高是目前文字大小的1.5倍

    优先级：
        选择器相同，则执行层叠性

        选择器不同，则根据选择器权重

            继承 或者 *         0 0 0 0     0
            元素选择器          0 0 0 1     1
            类选择器 伪类选择器  0 0 1 0     10
            id选择器            0 1 0 0     100
            行内样式 style=""   1 0 0 0     1000
            !important 重要的   无穷大      ∞
                div {
                    color: pink!important;
                }

            a浏览器默认制定了一个样式 蓝色的 有下划线 相当于 a {color: blue;}

        权重的叠加  
            ul li {
                color: pink;
            }
                权重: 0 0 0 1 + 0 0 0 1 = 2

            .nav li {
                color: pink;
            }
                权重： 0 0 1 0 + 0 0 0 1 = 0 0 1 1

            权重有叠加 但永远不会进位⭐⭐⭐⭐⭐

12、盒子模型
    看透网页布局的本质
        网页布局过程：
            先准备好相关的网页元素，网页元素基本都是盒子Box

            利用css设置好盒子样式，然后摆放到相应的位置

            往盒子里面装内容

    盒子模型
        css盒子模型实际上就是一个盒子

        组成：
            border  边框

            content 内容

            padding 内边距

            margin  外边距

    边框border
        border可以设置元素的边框，边框有三部分组成，边框宽度（粗细）边框样式 边框颜色

        语法：
            border: border-width || border-style || border-color

            border-width: 10px;

            border-style: solid || dashed || dotted; //实线虚线点线

            border-color: blue;

        边框可以分开写：
            border-top: 5px solid pink;
            border-bottom: 10px dashed purple;
            border-left: 5px solid pink;
            border-right: 10px dashed purple;

        border-collapse: collapse; //相邻边框合并到一起

        边框会影响盒子的实际大小

    内容content

    内边距padding
        边框与内容之间的距离

        属性：
            padding-top
            padding-bottom
            padding-left
            padding-right

        padding: 5px; 只有一个值 说明上下左右都是5px
        padding: 5px, 10px; 只有两个值 上下是5px 左右是10px
        padding: 5px, 10px, 20px; 有三个值，说明上5px 左右10px 下面20px
        padding: 5px, 10px, 20px, 30px; 分别是上右下左 顺时针方向

        内边距会影响盒子的大小

        如何让内边距不影响盒子的大小
            不写width属性

    外边距margin
        属性：
            margin-left
            margin-right
            margin-top
            margin-bottom

        典型应用：

            外边距可以让块级盒子水平居中

                盒子必须已经指定了宽度
                
                margin: 0 auto;

            行内元素或者行内块元素要想水平居中，只需让其父亲元素添加属性text-align: center;即可

        如何解决外边距塌陷问题：
            可以为父元素定义上边框

            可以为父元素定义上内边距

            可以为父元素添加overflow: hidden;

    如何清除内外边距

        <!-- 这也是我们css的第一行代码 -->

        * {
            padding: 0;
            margin: 0;
        }

    行内元素尽量只设置左右的内外边距，但是转换为块级元素或者行内块元素就可以设置了

13、ps的使用

    打开图片

    视图—>标尺->右击标尺->改为像素

14、list-style: none; //去除无序列表前面的小圆点

15、圆角边框

      border-radius: 值px; 

      参数值可以用精确值也可以用百分比来实现

      圆形的做法：

        参数值设置为高度和宽度的一半，或者用百分比表示：

        border-radius: 50%;

      圆角矩形的做法：

        参数值设置为高度的一半

        border-radius: 50px; //假设height: 100px;

      可以设置不同的圆角：
        border-top-left-radius
        border-top-right-radius
        border-bottom-left-radius
        border-bottom-right-radius

16、盒子阴影⭐⭐⭐⭐⭐

    box-shadow: h-shadow v-shadow blur spread color inset;

        h-shadow    必须，水平阴影的位置，允许负值

        v-shadow    必须，垂直阴影的位置，允许负值

        blur        可选，模糊距离

        spread      可选，阴影的尺寸

        color       可选，阴影的颜色 一半用rgba(0, 0, 0, .3); 阴影效果更佳逼真

        inset       可选，将外部阴影(outset)改为内部阴影

    刚开始盒子没有影子，当鼠标经过添加影子：
        
        div:hover {
            box-shadow: 10px 10px 10px 10px rgba(0, 0, 0, .3) inset;
        }

17、文字阴影

    text-shadow: h-shadow v-shadow blur color;

18、浮动

    传统布局的三种方式

        标准流

            定义：就是标签按照规定好的默认方式排列

            块级元素会独占一行，行元素一行可以有多个

        浮动

        定位

    为什么需要浮动：

        可以让多个块级元素一行内排列显示

    网页布局第一准则：

        多个块级元素纵向排列找标准流，多个块级元素横向排列找浮动 

    float属性用于创建浮动框，将其移动到一边，直到左边缘或右边缘触及包含块或另一个浮动框的边缘。

    语法：

        选择器 { float: 属性值;}

        属性值

            none

            left

            right

    浮动特性：⭐⭐⭐⭐⭐

        浮动元素会脱离标准流，移动到指定位置，俗称脱标

        浮动的盒子不再保留原先的位置，会让其它的标准流盒子占有

        如果多个盒子都设置了浮动，则它们会按照属性值一行内显示并且顶端对齐排列

            浮动的元素是相互贴在一起的(不会有空隙)，若父级盒子装不下，则会另起一行

        任何元素都可以浮动，不管原先是什么模式的元素，添加浮动之后具有行内块元素相似的特性。

            如果块级盒子没有设置宽度，默认宽度和父亲一样宽，但是添加浮动后，它的大小根据内容来决定

            浮动的盒子中间是没有缝隙的，是紧挨着一起的

            行内元素同理

    浮动元素经常和标准流父级搭配使用

        为了约束浮动元素位置，我们网页布局一半采取的错略是：
            先用标准流的父元素排列上下位置，之后内部子元素采取浮动排列在左右位置，符合网页布局第一准则

19、清除浮动
    所有的父盒子都必须要有高度吗?
        理想中的状态，让子盒子撑开父亲，有多少孩子，我父盒子就有多高。

    为什么要清除浮动?
        由于父级盒子很多情况下，不方便给高度，但是子盒子浮动又不占有位置，最后父级盒子高度为0时，就会影响下面的标准流盒子。

        由于浮动元素不在占用原文档流的位置，所以它会对后面的元素排版产生影响。

    清除浮动本质
        消除浮动元素的影响

    语法：
        选择器 {clear: 属性值;}

        属性值：
            left
                不允许左侧有浮动元素(清除左侧浮动的影响)

            right
                不允许左侧有浮动元素(清除左侧浮动的影响)

            both
                同时清除左右侧浮动的影响 

    清除浮动方法
        额外标签法也成为隔墙法，是w3c推荐的做法

            额外标签法会在浮动元素末尾添加一个空的标签，例如<div style="clear: both;"></div>,或者其它块级元素标签
            
            优点：简单易懂 书写方便

            缺点：添加许多无意义的标签，结构化较差

            注意：要求这个标签必须是块级元素

        父级添加overflow属性

            overflow: hidden;

            优点：代码简洁

            缺点：无法显示溢出的部分

        父级添加after伪元素

            .clearfix:after {
                content: "";
                display: block;
                height: 0;
                clear: both;
                visibility: hidden;
            }
            .clearfix {     /* IE6、7专有 */
                *zoom: 1;
            }

        父级添加双伪元素

            .clearfix:before,
            .clearfix:after {
                content: "";
                display: table;
            }
            .clearfix:after {
                clear: both;
            }
            .clearfix {     /* IE6、7专有 */
                *zoom: 1;
            }

20、开发技巧
    实际开发中，我们不会直接用链接a而是用li包含链接(li + a)的做法
        li + a语义更清晰，一看这就是有条理的列表型内容

        如果直接用a，搜索引擎容易辨别为堆砌关键字嫌疑，从而影响网站排名 











         