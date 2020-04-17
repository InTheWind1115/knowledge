1、什么是css?
(1)css是层叠样式表语言。【cascading style sheet】
(2)作用：修饰html页面，设置html页面中的某些元素的样式，让html页面更好看。Css好比是html的化妆品一样。
(3)Html还是主体，css依赖html。Css的存在就是修饰html，所以新建的文件夹还是xx.html文件。
(4)掌握程度：常见的css样式要求会写。别人写的css样式要能看懂。


2、在html页面中嵌套使用css的三种方式：
    (1)在标签内部使用style属性来设置元素的css样式，这种方式成为内联定义方式。
        ①语法格式：
        1)<标签 style=“样式名：样式值；样式名：样式值；样式名：样式值；...”></标签>
    (2)第二种方式：在head标签中使用style块，这种方式被称为样式块方式。
    ①语法格式：
    <head>
        <style type=”text/css”>
            选择器{             //id选择器 标签选择器 类选择器
                样式名：样式值；
                样式名：样式值；
                ...
            }
            选择器{
                样式名：样式值；
                样式名：样式值；
                ...
            }
        </style>
    </head>
    第三种方式：外入外部链式表文件，这种方式最常用。（将样式写到一个独立的xxx.css文件当中，在需要的网页上直接引入css文件，样式就引入了）
        语法格式：
            <link type="text/css" rel="stylesheet" href="css文件的路径" />

        这种方式容易维护，维护成本降低。
            xxx.css文件
                1.html中引入了
                2.html中引入了
                3.html中引入了
                4.html中引入了

//第一种方式代码：内联定义方式
    {
        <div style="width : 300px; height : 300px; background-color : #CCFFFF; display : block></div>
        //样式还能这样写
            border : 1px solid black
    }
//第二种方式代码：样式块
    {
        <style type=”text/css”>
            #usernameMsg {             //id选择器 
                color : red;
                font-size : 12px;
            }
        </style>


        <style type=”text/css”>
            div {             //标签选择器 标签选择器的作用范围比id选择器广
                background-color : black;
                border : 1px solid red;
                width : 100px;
                height : 100px;
            }
        </style>

        <style type=”text/css”>
            .类名 {             //类选择器 作用：可以跨标签 在html标签中用class=“类名” 来定义类
                样式名：样式值；
                样式名：样式值；
                ...
            }
        </style>

    }
//第三种方式：引入外部独立的css文件
    {
        <link rel="stylesheet" type="text/css" href="css/1.css">
    }


3、列表样式
    ul {
        list-style-type: none;
    }


4、css样式的绝对定位
    #div1 {
        background-color: red;
        border: 1px black solid;
        width: 300px;
        height: 300px;
        position: absolute; //绝对定位
        left: 100px;
        right: 100px;
    }