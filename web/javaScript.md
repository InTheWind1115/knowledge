1、什么是javaScrpit，有什么用？
    JavaScript是运行在网页上的脚本语言。简称JS
    JavaScript是网景（NetScape)的布兰登艾奇开发的，最初叫做LiveScirpt。
    它让浏览器更加的生动了，不再是单纯的静态页面了。页面更具有交互性。
    在历史的某个阶段，SUN公司和网景公司他们之间有合作关系，SUN公司把LiveScript的名字修改为JavaScript。
    JavaScript这个名字中虽然带有“Java"，但是和Java没有任何关系，只是语法上有点类似。他们运行的位置不同。

    JavaScript程序不需要我们程序员手动编译，编写完源代码之后，浏览器直接打开解释执行。
    JavaScript的”目标程序“以普通文本形式保存，这种语言叫做”脚本语言“。


2、在html文件中嵌入JavaScript的三种方式：
    第一种方式：
    <!doctype html>
    <html>
        <head>
            <title>HTML嵌入JS代码的第一种方式</title>
        </head>
        <body>
            <!--
                1、要实现的功能：
                    用户点击一下按钮，弹出消息框
                2、JS是一门事件驱动类型的编程语言，依靠时间去驱动，然后执行对应的程序。
                在JS中有很多时间，其中有一个事件叫做：鼠标单击，单词：click。并且任何
                事件都会对应一个事件句柄叫做：onclick。【注意：事件和事件句柄的区别是：
                事件句柄实在时间单词前添加一个on。】，而事件句柄是以html标签的属性存在的。
                3、onclick=”js代码“，执行原理是什么？
                    页面打开的事件，js代码并不会执行，只是把这段js代码注册到按钮的click
                    事件上了。等这个按钮发生click事件之后，注册在onclick后面的js代码会被
                    浏览器自动调用。
                4、怎么使用js代码弹出消息框？
                    在js中有一个内置的对象叫做window，全部小写，可以直接拿来使用，window代表的是浏览器对象。
                    window对象有一个函数叫做：alert，用法是window。alert("msg");这样就可以弹窗了。
                5、js中的字符串可以使用双引号，也可以使用单引号。
                6、js中的一条语句结束之后可以使用分号”；“，也可以不用。
            -->
            <!--
                window可以省略不写
            -->
            <input type="button" value="hello" onclick="window.alert('hello js')"/>
            <input type="button" value="hello" onclick="window.alert("hello js");
                                                        window.alert("hello js");
                                                        window.alert("hello js");"/>
        </body>
    </html>

    第二种方式：脚本块
    <!--
        javascript出现的地方随意，并且自上而下执行。
        js的注释和c++一样
    -->
    <!doctype html>
    <html>
        <head>
            <title>HTML嵌入JS代码的第二种方式</title>
        </head>
        <body>
            <script type="text/javascript">
                /*
                    暴露在脚本块当中的程序，在页面打开的时候执行。
                    并且遵守自上而下的顺序依次执行。(这个代码的执行不需要事件)
                */
                window.alert("hello world!");
            </scirpt>
            <input type="button">我是一个按钮</inpput>
        </body>
    </html>

    第三种方式：引入外部独立的js文件
    1.js
    {
        window.alert("hello world);
    }

    <!doctype html>
    <html>
        <head>
            <title>HTML嵌入JS代码的第一种方式</title>
        </head>
        <body>
            <!--
                在需要的位置引入js脚本文件
                js问价自上而下的执行
            -->
            <script type="text/javascipt" src="js/.1.js"></scipt>

            <!--这种方式不行，结束的script标签必须有-->
            <script type="text/javascipt" src="js/.1.js" />

            <script type="text/javascipt" src="js/.1.js">
                window.alert("hello"); //这行代码不会执行，这是引入外部独立的js文件，但是下面不是引入外部文件的则可以
            </scipt>

            <script type="text/javascipt">
                alert("hello")
            </scipt>
        </body>
    </html>


3、关于js中的变量：
    <!doctype html>
    <html>
        <head>
            <title>HTML嵌入JS代码的第一种方式</title>
        </head>
        <body>
            <script type="text/javascript">
            /*
                如何声明变量？
                    var 变量名；

                怎么给变量赋值？
                    变量名 = 值；

                JavaScript是一种弱类型语言，没有编译阶段，一个变量可以随意赋值，赋什么类型的值都行。
                var i = 100;
                i = false;
                i = "abc";
                i = new Object();
                i = 3.14

                在js中，当一个变量没有手动赋值的时候，系统默认赋值undefined，undefined在js中是一个具体的值。

                如果一个变量没有声明/定义，直接访问有语法错误 ××× is not defined
            */                                                                      
            </script>
        </body>
    </html>


4、函数的定义与调用：
    <!doctype html>
    <html>
        <head>
            <title>HTML嵌入JS代码的第一种方式</title>
        </head>
        <body>
            <script type="text/javascript">
            /*
                js中的函数，等同于java语言中的方法。

                js中的变量是一种弱类型的，那么函数应该怎么定义呢？
                    语法格式:
                        第一种方式：
                        function 函数名(形式参数列表) {
                            函数体;
                        }
                        第二种方式：
                        函数名 = function(形式参数列表) {
                            函数体；
                        }
            */

            function sum(a, b) {
                alert(a + b)
            }       
            //函数必须调用才能执行
            sum(10, 20);  

            /*
                在js中，如果两个函数同名，那么下面的函数会覆盖掉上面的函数。
            */                                                             
            </script>
        </body>
    </html>


5、变量：
    全局变量：
        在函数体之外声明的变量属于全局变量，全局变量的生命周期是：
            浏览器打开时声明，浏览器关闭时销毁，尽量少用，因为全局变量会一直在浏览器的内存当中，耗费内存。
    局部变量：
        在函数体当中声明的变量，包括形式参数。
        局部变量的生命周期是：函数开始执行局部变量的内存空间开辟，函数执行结束后，局部变量的内存空间销毁。
        局部变量生命周期较短。
    注意：
        当一个变量声明的时候没有使用var关键字，那么不管这个变量在哪里声明的，都是全局变量。


6、关于JS中的数据类型
    虽然js中的变量在声明的时候不需要指定的数据类型，但是在赋值，每一个数据还是有类型的，所以这里也需要学习一下js包括哪些数据类型？
        js中的数据类型有，原始类型，引用类型。
        原始类型：Undefined, Number, String, Boolean, Null
        引用类型：Object以及Object的子类

    ES规范（ECMAScipt规范），在ES6之后，又基于以上的6种类型之外添加了一种新的类型：Symbol

    字符串比较用双等号==

    js中有一个运算符叫做typeof，这个运算符可以在程序运行阶段动态的获取变量的数据类型。
        语法格式：
            typeof 变量名
        运算结果：//六个字符串 注意全部是小写
            undefined
            number
            string
            boolean
            object
            function
        //求和，要求a b变量必须是数字，不能是其它类型
        {
            function sum(a, b) {
                if (typeof a == "number" && typeof b == "number") {
                    return a + b;
                }
                alert(a + "," + "b" + "必须都为数字！");
            }
        }

    Undefined数据类型：
        Undefined数据类型只有一个值，这个值就是undefined //注意大小写
        当一个变量没有手动赋值，系统默认赋值undefined
        或者也可以给一个变量手动赋值undefined

    Number数据类型:
        Number数据类型包括哪些值：
            整数 小数 正数 负数 不是数字[NaN] 无穷大

        NaN：alert(100 / "中国人");

        Infinity：当除数为0的时候，结果为无穷大

        isNaN(数据); 此函数为内置函数 判断是否为一个数字 结果返回Boolean类型 true表示不是数字 false表示是数字

        parseInt()函数 //可以将字符串自动转换成数字 并且取整数位

        parseFloat() //将字符串自动转换为数字

        Math.ceil() //向上取整

    Boolean数据类型：
         js中的数据类型永远都只有两个值，true和false，这一点和java相同

         Boolean()函数
            作用：将非Boolean类型转换为Boolean类型
            规律：“有”就转换成true，“没有”就转换成false

    Null数据类型只有一个值：null，但是typeof null 会显示object //有人说是设计者的一个bug

    String数据类型：
        在js当中字符串可以使用"", 也可以使用''

        两种方式：
            //小string 属于原始类型String
            var s = "abc"; //typeof s 结果为 string

            //大string 属于Object类型
            var s = new String("abc); //typeof s 结果为 object

        无论是小String还是大String 它们的属性和方法都是通用的
            alert(s.length);
        
        String是一个内置的类，可以直接用，String的父类是Object

        关于String类型的常用属性以及函数：
            s.length

            函数：
            indexOf() //获取指定字符串在当前字符串中第一次出现出的索引
            lastIndexOf() //获取指定字符串在当前字符串中最后一次出现出的索引
            replace() //替换第一个 想全部替换使用正则表达式
            substring(start, end) //不包含end 
            substr(start, length) 

    Object类型：
        Object类型是所有类型的超类，自定义的任何类型默认继承Object.

        Object类包括哪些属性呢?
            prototype属性 (常用的) //作用是给类动态的扩展属性和函数
            constructor属性

        方法：
            toString()
            valueof()
            toLocaleString()

        在js中如何定义类？如何new对象？
            定义类的语法：
                第一种方式：
                    function 类名(形参) {

                    }

                第二种方式：
                    类名 = function(形参) {

                    }

            创建对象的语法：
                new 构造方法名(实参)； //构造方法名和类名一致

        sayHello(); //把sayHello当作一个普通的函数来调用
        new sayHello(); //这种方式表示把sayHello当作一个类来创建对象

        {
            //定义一个学生类
            function Student() {
                alert("Student......");
            }

            //当作普通函数调用
            Student();
            //当作类来创建对象
            var stu = new Student();

            //js中的类的定义，同时又是一个构造函数的定义
            //在js中类的定义和构造函数的定义是放在一起来完成的
            function User(a, b, c) {
                //声明属性 (this表示当前对象)
                //User类中有三个属性:sno/sname/sage
                this.sno = a;
                this.sname = b;
                this.sage = c;
            }
            //创建对象
            var u1 = new User(111, "zhangsan", 30);
            //访问对象的属性
            alert(u1.sno);
            alert(u1.sname);
            alert(u1.sage);
            //访问对象的属性还可以这样做：
            alert(u1["sno"]);
            alert(u1["sname"]);
            alert(u1["sage"]);
        }

        {
            Product = function(pno, pname, price) {
                //attribue
                this.pno = pno;
                this.pname = pname;
                this.price = price;

                //function
                this.getPrice = function() {
                    return this.price;
                }
            }

            var xigua = new Product(111, "watermelon", 4.0);
            var pri = xigua.getPrice();
            alert(pri);

            //可以通过prototype这个属性来给类动态扩展属性以及函数
            Product.prototype.getPname = function() {
                return this.pname;
            }
            //调用后期扩展的getPname函数
            var pname = xigua.getPname();
            alert(pname);

            //给String扩展一个函数
            String.prototype.suiyi = function() {
                alert("这是给String类型扩展的一个函数，叫做suiyi");
            }

            "abc".suiyi();
        }


7、null NaN undefined这三个有什么区别：
    三个的数据类型不一样
    typeof null //object
    typeof NaN //number
    typeof undefined //undefined

    null == undefined

    == //只判断值是否相等
    === //判断值和数据类型是否相等

8、js中的常用事件
    blur失去焦点
    focus获得焦点

    click鼠标单击
    dblclick鼠标双击

    keydown键盘按下
    keyup键盘向弹起

    mousedown鼠标按下
    mouseover鼠标经过
    mousemove鼠标移动
    mouseout鼠标离开
    mouseup鼠标弹起

    reset表单重置
    submit表单提交

    change下拉列表选中项改变，或文本框内容改变
    select文本被选定
    load页面加载完毕

    任何一个事件都会对应一个事件句柄，事件句柄是在事件前加on。
    onXXX这个事件句柄出现在一个标签的属性位置上。(事件句柄以属性的形式存在)
    

9、回调函数
    特点：自己把这个函数代码写出来，但是自己不去调用，由程序调用。

10、注册事件的两种种方式
    <!doctype html>
    <html>
        <head>
            <title></title>
        </head>
        <body>
            <script type="text/javascript">      
                function sayHello() {
                    alert("hello js");
                }                    
            </script>
            //第一种方式
            <input type = "button" value = "hello" onclick = "sayHello()" />
            //第二种方式
            <input type = "button" value = "hello2" id = "mybyon" />
            <script type="text/javascript">
                //第一步先获取这个按钮对象
                var btnObj = document.getElementById("mybtn");
                //第二步给按钮对象的onclick属性赋值
                btnObj.onclick = sayHello; //注意 千万不要加小括号 btnObj.onclick = sayHello()是错误的写法
                //或者这样写 写一个匿名函数
                btnObj.onclick = function() {
                    alert("hello js");
                }
            </script> 
        </body>
    </html>

11、关于js代码的执行顺序
    和c++类似，必须在用之前定义。可以用load事件解决这个问题
    <!doctype html>
    <html>
        <head>
            <title></title>
        </head>
        <body onload="ready()">
            <script type="text/javascript">
                function ready() {
                    var btn document.getElementById("btn");
                    btn.onclick = function() {
                        alert("hello js);
                    }
                }
            </script>
            <input type="button" value="hello" id="btn" />
        </body>
    </html>

    //或者这样也可以
    <!doctype html>
    <html>
        <head>
            <title></title>
        </head>
        <body>
            <script type="text/javascript">

                window.onload = ready;

                function ready() {
                    var btn document.getElementById("btn");
                    btn.onclick = function() {
                        alert("hello js);
                    }
                }
            </script>
            <input type="button" value="hello" id="btn" />
        </body>
    </html>

12、代码设置标签的属性
    <!doctype html>
    <html>
        <head>
            <title></title>
        </head>
        <body>
            <script type="text/javascript">
                window.onload = function() {
                    document.getElementById("btn").onclick = function() {
                        var mytext = document.getElementById("mytext");
                        //一个节点对象中只要有属性的都可以
                        mytext.type = "checkbox";
                    }
                }
            </script>
            <input type="text" id="mytext" />
            <input type="button" value="将文本框修改为复选框" id="btn" />
        </body>
    </html>

13、js代码捕捉回车键
    <!doctype html>
    <html>
        <head>
            <title></title>
        </head>
        <body>
            <script type="text/javascript">
                window.onload = function() {
                    var usernameElt = document.getElementById("username");
                    //回车键的键值是13 esc的键值是27
                    usernameElt.onkeydown = function(event) {
                        //获取键值
                        //对于键盘对象事件来说 都有keyCode属性来获取键值
                        alert(event.keyCode);

                        //按回车键 提交登陆
                        if (event.keyCode == 13)
                            alert("正在登陆...");
                    }
                }

            </script>
            <input type="text" id="username" />
        </body>
    </html>

14、js中的void运算符
    //需求：既保留超链接的样式，同时用户点击该超链接的时候执行一段js的代码，但页面还不能不能跳转
    <!doctype html>
    <html>
        <head>
            <title></title>
        </head>
        <body>
            页面顶部
            <br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>
            <br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>
            <br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>


            //void运算符的语法：void(表达式)
            //运算原理：执行表达式，但不返回任何结果。
            <a href="javascript:void(0)" onclick="window.alert('test code')>既保留超链接的样式，同时用户点击该超链接的时候执行一段js的代码，但页面还不能不能跳转</a>
            <script type="text/javascript"></script>
        </body>
    </html>

15、js中的控制语句
    和java语句相同

    for...in语句和with语句
    {
        //创建js数组
        var arr = [false, true, 1, 2, "abc", 3.14]; //js数组中的元素类型随意
        //遍历数组 第一种方式 for语句
        for(var i = 0; i < arr.length; i++) {
            alert(arr[i]);
        }

        //for...in语句
        for (var i in arr) { //i是arr数组的下标
            alert(arr[i])
        }

        //for...in语句可以遍历对象的属性
        User = function(username, password) {
            this.username = username;
            this.password = password;
        }
        var u = new User("zhangsan", "444");
        for (var shuXingMing in u) {
            alert(shuXingMing);
            alert(typeof shuXingMing); //shuXingMing是一个字符串
            alert(u[shuXingMing]);
        }

        with (u) { //访问变量时 前面会自动添加u 但这种方式可读性不好 最好别用
            alert(username + "," + password);
        }
    }





























<!doctype html>
    <html>
        <head>
            <title></title>
        </head>
        <body>
            <script type="text/javascript"></script>
        </body>
    </html>
    

    