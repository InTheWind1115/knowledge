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

21、浮动的盒子不会有外边距合并问题

22、定位
    为什么需要定位：
        某个元素可以自由的在一个盒子内移动距离或者固定在屏幕中的某个位置

    定位组成
        定位：将盒子定在某一个位置

        定位 = 定位模式 + 边偏移

    定位模式
        语法格式：
            position: 值;

        值：
            static      静态定位

            relative    相对定位

            absolute    绝对定位

            fixed       固定定位

            sticky      粘性定位

    边偏移
        语法格式：
            top: **px;

            bottom: **px;

            left: **px;

            right: **px;

    静态定位：
        position: static;

        静态定位按照标准流特性拜访位置，它没有边偏移

        静态定位很少在布局中使用

    相对定位：⭐⭐⭐
        position: relative;

        根据自己原来的位置坐标来移动的

        原来在标准流的位置继续占有，后面的盒子仍以标准流的方式对待它

    绝对定位：⭐⭐⭐
        position: absolute;

        元素在移动位置的时候，是相对于他的祖先元素来说的

        特点：
            如果没有祖先元素或者祖先元素没有定位，则以浏览器为准定位(Document文档)

            如果祖先元素有定位(相对 绝对 固定定位)，则以最近一级的有定位祖先元素为参考点移动位置

            绝对定位不再占有原先的位置(会脱标)

    子绝父相：⭐⭐⭐
        意思：子级是绝对定位的话，父级要用相对定位

        因为父级需要占有位置，因此是相对定位，子盒不需要占有位置，则是绝对定位

        当然，子绝父相不是永远不变的，如果父元素不需要占有位置，子绝父绝也会遇到

    固定定位：⭐⭐⭐
        position: fixed;

        特点：
            以浏览器的可视窗口为参照点移动元素
                跟父元素没有任何关系

                不随滚动条滚动

            固定定位不在占有原先的位置
                固定定位也是脱标的，其实固定定位也可以看作是一种特殊的绝对定位

        应用：固定在版心右侧位置
            让固定定位的盒子left: 50%; 走到浏览器可视区(也可以看作版心)的一半位置。

            让固定定位的盒子margin-left: 版心宽度的一半距离; 多走版心宽度的一半位置

    粘性定位：
        position: sticky;
        
        跟随页面滚动搭配使用，兼容性较差，IE不支持

        特点：
            以浏览器的可视窗口为参照点移动元素(固定定位特点)

            粘性定位占有原先的位置(相对定位特点)

            必须添加top、left、right、bottom其中一个才有效

    定位叠放次序
        z-index: 数值;

        数值可以是正整数、负整数、或0，默认是auto，数值越大，盒子越靠上

        如果属性值相同，则按照书写顺序，后来居上

        数字后面不能加单位

        只有定位的盒子才有z-index属性

    绝对定位的盒子居中
        加了绝对定位的盒子不能通过 margin: 0 auto水平居中，但是可以通过以下计算方法实现水平和垂直居中

        left: 50%; //让盒子的左侧移动到父级元素的水平中心位置
        margin-left: -100px; //让盒子向左移动自身宽度的一半

    定位特殊特性
        绝对定位和固定定位也和浮动类似

        行内元素添加绝对或者固定定位，可以直接设置高度和宽度

        块级元素添加绝对或者固定定位，如果不给宽度或者高度，默认大小是内容的大小

    脱标的盒子不会触发外边距塌陷
        浮动元素、绝对定位、固定定位元素的都不会触发外边距合并的问题

    绝对定位、固定定位会完全压住盒子
        浮动元素不同，只会压住它下面标准流的盒子，但是不会压住下面标准流盒子里面的文字(图片)

        但是绝对定位(固定定位)会压住下面标准流所有的内容

        浮动之所以不会压住文字，因为浮动产生的目的最初是为了做文字环绕效果的。文字会围绕浮动元素

23、元素的显示与隐藏
    本质：让一个元素在页面中隐藏或者显示出来

    display属性⭐⭐⭐⭐⭐
        display: none; //隐藏对象

        display: block; //出来转换为块级元素之外，同时还有显示元素的意思

        display隐藏元素后，不再占有原来的位置

    visibility属性
        visibility: hidden; //元素隐藏

        visibility: visible; //元素可视

        visibility隐藏元素后，继续占有原来的位置。

        如果隐藏元素想要原来的位置，就用visibility: hidden;

        如果隐藏元素不想要原来的位置，就用display: none;

    overflow溢出属性
        overflow: hidden; //不剪切内容也不添加内容

        overflow: visible; //不显示超过对象尺寸的内容，超出的部分隐藏掉

        overflow: scroll; //不管超出内容与否，总是显示滚动条

        overflow: auto; //超出自动显示滚动条，不超出不显示滚动条

        一般情况下，我们都不想让溢出的内容显示出来，因为溢出的部分会影响布局

        但是如果有定位的盒子，请慎用overflow: hidden; 因为它回隐藏多余的部分

24、精灵图
    精灵图主要针对于小的背景图片的使用

    主要借助于背景位置来实现---background-position;

    一般情况下精灵图都是负值。

    缺点：
        图片文件还是比较大的

        图片本身放大和缩小会失真

        一旦图片制作完毕想要更换非常复杂

25、字体图标
    字体图标使用场景：主要用于显示网页中通用、常用的一些小图标

    字体图标可以为前端工程师提供一种方便高效的图标使用方式，展示的是图标，本质属于字体。

    优点：
        轻量级：一个图标字体要比一系列的图像要小，一旦字体加载了，图标就会马上渲染出来，减少了服务器请求。

        灵活性：本质其实是文字，可以很随意的改变颜色、产生阴影、透明效果、旋转等

        兼容性：几乎支持所有的浏览器，请放心使用

    字体图标的下载
        http://icomoon.io
        http://www.iconfonr.cn/

    字体的引用
        把下载包里面的fonts文件夹放入页面根目录下

        在css样式中全局声明字体：简单理解把这些字体文件通过css引入到我们页面中，一定要注意字体文件路径的问题

        html标签内添加小图标

    字体图标的追加
        把压缩包里面的selection.json重新上传，然后选中自己想要 新的图标，重新下载压缩包，并替换原来的文件即可

26、css三角的做法
    span {
        width: 0px;
        height: 0px;
        border: 10px solid transparent;
        border-top-color: blue; //向下的箭头
    }

27、用户界面样式
    鼠标样式cursor
        cursor: 样式;

        样式：
            default     小白 默认

            pointer     小手

            move        移动

            text        文本

            not-allowed 禁止

    轮廓线outline
        给表单添加outline: 0;或者outline: none;样式之后，就可以去掉默认地蓝色功能

        input {
            outline: none;
        }

    防止拖拽文本域resize
        实际开发中，我们本文域右下角是不可以拖拽地

        textarea {
            resize: none;
        }

28、vertical-align属性
    使用场景：经常用于设置图片或者表单(行内块元素)和文字垂直对齐

    官方解释：用于设置一个元素地垂直对齐方式，但是它只针对于行内元素或者行内快元素有效

    语法：
        vertical-align: baseline | top | middle | bottom;

        baseline    默认。元素放置在父元素的基线上

        top         把元素地顶端于行中最高元素地顶端对齐

        middle      把此元素防止在父元素地中部

        bottom      把元素地顶端与行中最低地元素的顶端对齐

29、溢出的文字省略号显示
    单行文本溢出显示省略号，必须满足三个条件
        div {
            //先强制一行内显示文本 (默认normal自动换行)
            white-space: nowrap;
            //超出的部分隐藏
            overflow: hidden;
            //文字用省略号替代超出的部分
            text-overflow: ellipsis;
        }

    多行文本溢出显示省略号
        多行文本溢出显示省略号，有较大的兼容性问题，适合于webKit浏览器或移动端(移动端大部分是webKit内核)

        div {
            overflow: hidden;
            text-overflow: ellipsis;
            //弹性伸缩盒子模型显示
            display: -webkit-box-;
            //限制在一个块元素显示的文本的行数
            -webkit-line-clamp: 2;
            //设置或检索伸缩盒对象的子元素的排列方式
            -webkit-box-orient: vertical;
        }

30、开发技巧
    margin负值运用：
        淘宝多框图片，去掉重复的边框

        ul li {
            float: left;
            list-style: none;
            width: 150px;
            height: 200px;
            border: 1px solid red;
            margin-left: -1px;
        }
            有人会说都往左移动1px，那不守恒了吗？实际上li是一个一个渲染的
            第一个摆放好然后左移，然后第二个li，因为先浮动，所以紧贴，在往左移，故可以

31、HTML5新特性
    HTML5新增的语义化标签
        <header> 头部标签

        <nav> 导航标签

        <article> 内容标签

        <section> 定义文档某个区域

        <aside> 侧边栏标签

        <footer> 尾部标签

        注意：
            这种语义化标准主要时针对搜索引擎的

            这些新标签页面中可以使用多次

            在IE9中，需要把这些元素转换为块级元素

            其实，我们移动端更喜欢使用这些标签

            HTML5还增加了很多其他标签，我们后面再慢慢学

    <video>视频
        语法
            <videos src="文件地址" controls="controls"></videos>

            或者下面这种兼容性更强的写法
            <video controls="controls" width="300">
                <source src="move.ogg" type="video/ogg">
                <source src="move.mp4" type="video/mp4">
                您的浏览器暂不支持<video>标签播放视频
            </video>

        常见属性
            去w3cschool查看

     <audio>音频
        语法
            <audio src="文件地址" controls="controls"></audio>

            或者下面这种兼容性更强的写法
            <audio controls="controls" width="300">
                <source src="move.mp3" type="audio/mpeg">
                <source src="move.ogg" type="audio/ogg">
                您的浏览器暂不支持<audio>标签播放视频
            </audio>

        常见属性
            去w3cschool查看

    HTML5新增的input类型
        去w3cschool查看

    HTML5新增的表单属性
        去w3cschool查看

        可以通过以下设置方式修改placeholder里面的字体颜色
            input::placeholder {
                color: pink;
            }

32、CSS3新特性
    属性选择器
        属性选择器可以根据元素特定属性的来选择元素，这样就可以不用借助于类或者id选择器

        选择符                  简介
        E[att]                  选择具有att属性的E元素
        E[att="val"]            选择具有att属性且属性值等于val的E元素
        E[att^="val"]           匹配具有att属性且值以val开头的E元素
        E[att$="val"]           匹配具有att属性且值以val结尾的E元素
        E[att*="val"]           匹配具有att属性且值中含有val的E元素

        注意：类选择器、属性选择器、伪类选择器、权重为10

    结构伪类选择器
        结构伪类选择器主要根据文档结构来选择器元素，常用于根据父级选择器里面的子元素

        选择符                  简介
        E:first-child           匹配父元素中的第一个子元素E
        E:last-child            匹配父元素中的最后一个子元素E
        E:nth-child(n)          匹配父元素中的第n个子元素E
        E:first-of-type         指定类型E的第一个
        E:last-of-type          指定类型E的最后一个
        E:nth-of-type(n)        指定类型E的第n个

        区别
            nth-child对父元素里面所有孩子排序选择(序号是固定的) 先找到第n个孩子，然后看看是否和E匹配

            nth-of-type对父元素里面指定子元素进行排序选择。先去匹配E，然后再根据E找第n个孩子

        nth-child(n)选择某个父元素的一个或多个特定的子元素
            n可以是数字，关键字和公式

            n如果是数字，就是选择第n个子元素，里面数字从1开始

            n可以是关键字:even偶数 odd奇数

            n可以是公式:常见的公式如下(如果n是公式，则从0开始计算，但是第0个元素或者超出了元素的个数会被忽略)
                2n      偶数
                2n+1    奇数
                5n      5 10 15...
                n+5     从第五个开始(包含第五个)到最后
                -n+5    前五个(包含第五个)

    伪元素选择器⭐⭐⭐⭐⭐
        伪元素选择器可以帮助我们利用CSS创建新标签元素，而不需要HTML标签，从而简化HTML结构

        选择符          简介
        ::before        在元素内部的前面插入内容        
        ::after         在元素内部的后面插入内容

        注意：
            before和after创建一个元素，但是属于行内元素
            新创建的这个元素在文档树中是找不到的，所以我们称为伪元素
            语法:element::before {}
            before和after必须有content属性
            before在父元素内容的前面创建元素，after在父元素内容的后面插入元素
            伪元素选择器和标签选择器一样，权重为1

        应用：
            伪元素清除浮动
                .clearfix:after{
                    content: "";    //伪元素必须写的属性
                    display: block; //插入的元素必须是块级
                    height: 0;      //不要看见这个元素
                    clear: both;    //核心代码清除浮动
                    visitbility: hidden;    //不要看见这个元素
                }

            伪元素清除浮动
                后面两种伪元素清除浮动算是第一种额外标签法的一个升级和优化

                .clearfix:before, .clearfix:after {
                    content: "";
                    display: table;     //转换为块级元素并且一行显示
                }

                .clearfix:after {
                    clear: both;
                }

    CSS3盒子模型
        CSS3中可以通过box-sizing来指定盒模型，有2个值:即可指定为content-box、boder-box，这样
        我们计算盒子大小的方式就发生了改变

        可以分成两种情况:
            box-sizing: content-box 盒子大小为width + padding + border (以前默认的)

            box-sizing: border-box 盒子大小为width

        如果盒子模型我们改为了box-sizing: border-box, 那padding和border就不会撑大盒子了(前提padding和border不会超过width宽度)

    CSS3滤镜filter：
        filter CSS属性将模糊或颜色偏移等图形效果应用于元素

        filter: 函数(); //例如: filter: blur(5px); blur模糊处理 数值越大越模糊

    CSS3 calc 函数:
        calc()此CSS函数让你在声明CSS属性值时执行一些计算

        width: calc(100% - 80px);

        括号里面可以使用+ - * /来进行计算

        应用：子盒子永远比父盒子小固定的px

    CSS3过渡(重点)⭐⭐⭐⭐⭐
        transition: 要过渡的属性 花费时间 运动曲线 何时开始;

        属性：想要变化的css属性，宽度高度 背景颜色 内外边距都可以，如果想要所有的属性都变化过渡，写一个all就可以

        花费时间：单位是秒(必须写单位) 比如0.5s

        运动曲线: 默认是ease(可以省略)

        何时开始: 单位是秒(必须写单位) 可以设置延迟触发时间 默认是0s (可以省略)

        记住过渡的使用口诀: 谁做过渡给谁加

33、网站favicon图标
    制作favicon图标
        把图片切成png格式图片

        把png图片转换为ico图标，第三方转换网站: http://www.bitbug.net/

    favicon图标放到网站根目录下

    HTML页面引入favicon图标
        <link rel="shortcut icon" href="favicon.ico" type="image/x-icon" />

34、网站TDK三大标签SEO[搜索引擎]优化
    title网站标题
        title具有不可替代性，是我们内页的第一个重要标签，是搜索引擎了解网页的入口和对网页主题归属的最佳判断点。

        建议: 网站名(产品名)-网站的介绍(尽量不要超过30个汉字)

        例如: 京东(JD.COM)-综合网购首选-正品低价、品质保障、配送及时、轻松购物！
              
    description网站说明
        简要说明我们网站主要是做什么的

        我们提倡，description作为网站的总体业务和主题概括，多采用"我们是...", "我们提供...", "xxx网作为...", "电话: 010..."之类语句

        例如：
            <meta name="description" content="京东JD.COM-专业的综合网上购物商城, 销售家电、数码通讯等数万个品牌优质的商品, 便捷、诚信的服务, 为您提供愉悦的网上购物体验!" />

    keywords关键字⭐⭐
        keywords是页面关键词，是搜索引擎的关注点之一。

        keywords最好限制为6 ~ 8个关键词, 关键词之间用英文逗号隔开, 采用关键词1,关键词2的形式

        例如：
            <meta name="keywords" content="网上购物,网上商城,手机,笔记本,电脑,MP3,京东" />

35、LOGO SEO优化
    logo里面首先放一个h1标签，目的是为了提权，告诉搜索引擎，这个地方很重要

    h1里面再放一个链接，可以返回首页的，把logo的背景图片给链接即可

    为了搜索引擎收录我们，我们链接里面要放文字(网站名称)，但是文字不要显示出来
        方法1：text-indent移动到盒子外面(text-indent: -9999px),然后overflow: hidden, 淘宝的做法

        方法2: 直接给font-size: 0;就看不到文字了，京东的做法

    最后给链接一个title属性，这样鼠标放到logo上就可以看到提示文字了
    
36、2D转换
    转换之移动translate
        语法
            transform: translate(x, y);
            transform: translateX(n);
            transform: translateY(n);

        重点
            定义2D转换中的移动，沿着X和Y轴移动元素

            translate最大的优点：不会影响到其他元素的位置

            translate中的百分比单位是相对于自身元素的translate(50%, 50%);

            对行内标签没有效果

        块元素垂直居中显示应用，用translate来做
            p {
                position: absolute;
                top: 50%;
                left: 50%;
                width: 200px;
                height: 200px;
                transform: translate(-50%, -50%);
                /* 
                    本来是
                    margin-top: -100px;
                    margin-left: -100px;
                */
            }

    旋转rotate
        语法
            transform: rotate(度数);

        重点
            rotate里面跟度数，单位是deg，比如rotate(45deg)

            角度为正时，顺时针，负时，为逆时针

            默认旋转的中心点时元素的中心点

    2D转换中心点transform-origin
        语法
            transform-origin: x y;

        重点
            注意x y之间用空格隔开
            x y默认转换的中心是元素的中心点 (50% 50%)
            还可以给x y 设置像素 或者方位名词 (top bottom left right center)

    缩放scale
        语法
            transform: scale(x, y);
            
        重点    
            注意用空格隔开
            transform: scale(1, 1);宽和高都放大一倍 相对于没有变化
            transform: scale(2, 2);宽和高都放大了2倍
            transform: scale(2);只写一个参数，第二个参数则和第一个参数一样，相当于scale(2, 2);
            transform: scale(0.5, 0.5);缩小
            scale缩放最大的优势：可以设置转换中心点缩放，默认以中心点缩放的，而且不影响其它盒子

    综合写法
        transform: translate() rotate() scale()...
        顺序会影响转换的效果(先旋转会改变坐标轴方向)
        当我们同时有位移和其他属性的时候，记得要将位移放到最前

37、动画
    步骤
        先定义动画
            用keyframes定义动画(类似定义类选择器)

            @keyframes 动画名称 {
                0% {
                    width: 100px;
                }

                100% {
                    width: 200px;
                }
            }

        再使用动画
            div {
                animation-name: 动画名称;
                animation-duration: 持续时间;
            }

    动画序列
        0%是动画的开始，100%是动画的完成，这样的规则就是动画序列

        在@keyframes种规定某项CSS样式，就能创建由当前样式逐渐改变为新样式的动画效果

        动画是使元素从一种样式逐渐变化为另外一种样式的效果，可以改变任意多的样式任意多的次数

        请用百分比来规定变化发生的时间，或用关键词"from"和"to"，等同于0%和100%

    常用属性
        w3c查看

38、3D转换
    三维坐标系
        x轴：水平向右       右为正 左为负
        y轴：垂直向下       下为正 上为负
        z轴：垂直屏幕       外为正 里为负

    3D移动
        transform: translateX(100px);仅仅是在x轴上移动
        transform: translateY(100px);仅仅是在y轴上移动
        transform: translateZ(100px);仅仅是在z轴上移动      //有了透视才能看到
        transform: translate3d(x, y, z);

    3D旋转
        左手准则
            左手的手指指向x/y/z轴的正方向
            4指弯曲方向就是沿x/y/z轴旋转的方向

        transform: rotateX(45deg);沿着X轴正方向旋转45度
        transform: rotateY(45deg);沿着y轴正方向旋转45度
        transform: rotateZ(45deg);沿着z轴正方向旋转45度
        transform: rotate3d(x, y, z, 45deg);沿着自定义旋转轴旋转 了解即可

    3D呈现
        transform-style: flat | preserve-3d;

        flat:子元素不开启3d立体空间 默认的

        preserve-3d:子元素开启立体空间

        代码写给父级，但是影响的是子盒子

        这个属性很重要，后面必用

39、浏览器私有前缀
        
        
        




