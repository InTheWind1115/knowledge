1、JQUERY学习重点
    熟练背诵JQUERY[选择器和过滤器]语法

    熟练掌握[JQUERY对象]提供[功能函数]

2、jquery学习方式
    一天理论介绍

    分段提供jquery练习内容

3、JQUERY技术介绍
    就是JavaScript的封装版

    简化JavaScript对DOM对象定位以及对DOM对象属性操作开发步骤

4、JQUERY使用
    下载jquery工具文件，并导入到工程中

    将jQuery文件加载到浏览器上

5、jQuery对象与DOM对象区别
    DOM对象：
        在我们的浏览器去加载网页时由我们的浏览器负责创建的。
        
        一个html标签对应一个DOM对象

        可以通过管理DOM对象，来对关联html标签中属性进行操作

    jQuery对象：
        是[jQuery函数 $() ]负责创建的

        jQuery对象就是一个数组

        jQuery对象中存放的本次定位的DOM对象

        可以通过jQuery对象中的功能函数，来快速的对定位DOM对象进行操作。


6、jQuery对象一般用美元符号$开头
    var $obj = $(".food");

7、jQuery对象与DOM对象转换
    如何将jQuery对象转换为DOM对象：
        for (var i = 0; i < $obj.length;  i++) {
            var domObj = $obj[i];
        }

    如何将DOM对象转换为jQuery对象：
        var $obj = $(domObj);

    注意：jQuery对象和DOM对象之间的属性和函数彼此不能调用

8、jQuery选择器语法
    什么是选择器语法：
        就是对DOM对象进行定位的条件，比如根据ID定位，根据标签类型名

        jQuery中只有三种选择器

    基本选择器：
        定位条件：可以根据ID编号，根据标签类型名，根据标签采用样式选择器

        使用：
            $("#id编号"); //replace document.getElementById("id");
                根据id标号定位对应的dom对象，让dom对象保存到一个数组中并返回，返回的这个
                对象就是jQuery对象。
            
            $(".样式选择器名称"); //replace document.getElementsByClassName("样式选择器名");

            $("标签类型名") //replace document.getElementsByTagName("标签类型名");

            $("*"); //定位浏览器中所有的DOM对象，让DOM对象保存到一个数组中并返回。

            $("条件1， 条件2"); //只要DOM对象满足其中的一种条件，就会被定位到数组中，相当于或条件。
                组合选择器

    层级选择器
        定位条件：
            可以根据标签之间的父子关系定位
            可以根据标签之间兄弟关系定位
            
        标签之间关系
            父子关系：就是包含关系
                <tr>
                    <td>
                        <input type="checkbox" />
                    </td>
                </tr>

                td是tr的直接子标签
                input是td的直接子标签
                input是tr的间接子标签

            兄弟关系：两个标签拥有相同的父标签，并且彼此之间没有包含的关系
                <body>
                    <div>1</div>    大哥
                    <div>2</div>    二哥
                    <p>段落标签</p>  三弟
                </body>

        具体使用：
            找子标签
                $("定位父标签的条件>定位子标签的条件");
                    定位当前父标签下，所有满足条件的直接子标签

                $("定位父标签的条件 定位子标签的条件");
                    定位当前父标签下，所有满足条件的直接子标签和间接子标签

            找兄弟标签
                $("定位当前标签条件~定位兄弟标签条件");
                    定位当前标签后面，所有满足条件的兄弟标签

                $("定位当前标签条件+定位兄弟标签条件")
                    定位当前标签后面与之紧邻的，并且满足条件的一个兄弟标签

                $("定位当前标签条件").sibling("定位兄弟标签条件");
                    定位当前标签前面与后面所有满足条件的兄弟标签

10、input标签选择器
    input标签组成：
        <input type="text" />
        <input type="password" />
        <input type="radio" />
        <input type="file" />
        <input type="button" />
        <input type="button" />
        <input type="reset" />

    input标签的作用：
        作为浏览器向网站发送请求时携带的请求参数

    使用：
        $(":type属性名字");

        例子：
            $(":button"); //定位页面中所有的button关联的DOM
            $(":checkbox"); //定位页面中所有的checkbox关联的DOM

            $(":table"); //无法定位任何内容

11、常用函数
    css()函数
        $obj.css("background-color", "red");

    val()函数
        读取jQuery对象的第一个DOM对象的value值

        $obj.val("值")
            为jQuery对象中所有的DOM对象的value属性值进行统一赋值

    each()函数
        each函数用来遍历jQuery对象中的DOM对象，每次读取一个DOM对象，交给我们写的函数
        
        $obj.each(myFun) //传递DOM对象的同时还传了数组下标
            //function myFun(index, domObj) {}

12、jQuery中的过滤器
    对已经定位到jQuery对象中DOM对象，进行二次过滤筛选的。

    过滤器不能独立使用，必须声明在选择器后面

    六种过滤器[三种常见的过滤器]：
        基本过滤器:
            过滤器条件：
                根据已经定位的DOM对象在我们jQuery对象中的存储位置进行二次过滤筛选

            使用：
                $("选择器:first"); //留下满足条件中的第一个DOM对象
                    例子：
                        $(":button":first); //定位页面中的第一个button

                $("选择器:last"); //留下满足条件中的最后一个DOM对象
                    例子：
                        $(":button":last); //定位页面中的最后一个button

                $("选择器:eq(下标值)"); //留下满足条件中的指定位置的DOM对象
                    例子:
                        $("div:eq(2)") //定位页面中的第三个div
                
                $("选择器:lt(下标值)"); //留下满足条件中的指定位置之前的所有DOM
                    例子:
                        $(":checkbox:lt(2)"); //页面中前两个checkbox

                $("选择器:gt(下标值)"); //留下满足条件中的指定位置之后的所有DOM
                    例子:
                        $(":checkbox:lt(3)"); //位置在第四个button之后的所有button对象

        基本属性过滤器：
            过滤条件：
                根据标签在声明时是否为指定属性进行手动赋值

                根据标签的属性内容与指定内容关系进行过滤器

            例子：
                <div>1</div>
                <div name="two">2</div>
                <div name="three">3</div>

                问题：哪一个div中没有name属性
                    所有的div标签都有name属性 

                问题：哪一个div的name属性是""
                    第一个div的name属性没有手动赋值，所以name属性值是默认值，就是""

            使用：
                $("选择器[属性名]"); //留下满足条件的并且在声明时为指定属性进行手动赋值的DOM对象
                    例子：
                        $("div[name]"); //后面两个div标签

                $("选择器[属性名='值']"); //留下满足定位条件的并且指定属性内容等于指定内容的DOM对象
                    例子：
                        $("div[name='two']"); //第二个标签
                        $("div[name='']"); //第一个标签

                $("选择器:[属性名^='值']"); //留下满足定位条件的并且指定属性内容以指定内容为开头的所有DOM对象
                    例子：
                        $("div[name^='t']"); //后面的两个div标签，因为two three都是以t开头

                $("选择器:[属性名$='值']"); //留下满足定位条件的并且指定属性内容以指定内容为结尾的所有DOM对象
                    例子：
                        $("div[name^='e']"); //第三个div标签 因为three以e结尾

                $("选择器:[属性名*=值']"); //留下满足定位条件的并且指定属性内容包含指定内容的DOM对象
                    例子：
                        $("div[name*='o']"); //第二个标签 two包含o

                $("选择器:[属性名1][属性名2*='值'][属性名3^='值']") //可以混合使用

        工作状态属性过滤器：
            html标签属性分类
                基本属性:
                    是绝对数标签都拥有的属性
                    
                    id name title rowspan
                
                样式属性：
                    背景，字体，边框

                value属性：
                    只存在于表单域标签中 //input select textares

                工作状态属性：
                    只存在于表单域标签中 //checked disabled selected

                监听事件属性：
                    onclick, onchange....

            使用：
                $("选择器:enabled"); //留下满足条件的并且处于可用状态的DOM对象
                    例子：
                        $(":button:enabled"); //定位所欲处于可用的button

                $("选择器:disabled"); //留下满足条件的并且处于不可用状态的DOM对象

                $("选择器:checked"); //留下满足条件的并且处于选中状态的DOM对象
                    例子：
                        $(":checkbox:checked:first") //页面中第一个被选中的checkbox
                
                $("选择器:selected"); //留下满足条件的并且处于选中状态的DOM对象
                    例子：
                        $("select>option:selected"); //下拉列表中被选中的option

13、jQuery对象中的功能函数
    show() & hide()
        show负责让jQuery对象包含的所有DOM对象关联的标签在浏览上显示 相当于style="display:block"
        hide负责让jQuery对象包含的所有DOM对象关联的标签在浏览上隐藏 相当于style="display:none"

    remove() & empty()
        empty：
            将当前的标签子标签进行相关的清除处理 //断子绝孙

        remove：
            将当前标签以及子标签进行相关的清除处理 //满门抄斩

    append() & appendTo()
        共同点：都是操作标签中innerHTML, 为当前标签添加子标签

        append:
            父标签.append(子标签); //父亲给自己找了一个儿子
        
        appendTo:
            子标签.appendTo(父标签); //儿子给自己找了一个父亲

14、属性操作函数
    val函数：
        $obj.val(); //读取jQuery对象中第一个DOM对象的value属性值

        $obj.val("值"); //为jQuery对象中所有DOM对象value属进行统一赋值

    prop函数：
        针对工作状态属性 checked disabled selected

        $obj.prop("checked", "true"); //为jQuery对象中所有DOM对象的checked属性赋值为true

        $obj.prop("checked"); //读取jQuery对象中第一个DOM对象的checked属性值

    attr函数：
        针对基本属性 id name title rowspan...

        $obj.attr("name", "ck"); //为jQuery对象中所有DOM对象的name属性统一赋值为ck

        $obj.attr("title"); //读jQuery对象中第一个DOM对象的title属性的值

    text函数：
        操作属性innerText,双目标签的文本显示内容 <div>23</div> 

        $obj.text("123"); //为jQuery对象中所有DOM对象的innerText属性赋值为"123"

        $obj.text(); //读取jQuery对象中所有DOM对象的innerText属性内容，拼接为一个字符串返回。

15、jQuery中的事件绑定方式
    JavaScript中事件绑定方式：
        嵌入式绑定：
            <input type="button" onclick="fun1()">

            缺点：一次只能为一个标签绑定监听事件。
        
        基于DOM对象的绑定方式：
            var array = doucument.getElementByName("ck");
            for (var i = 0; i < array.length; i++) {
                var domObj = array[i];
                domObj.onclick = fun1;
            }

            缺点:需要开发人员自行遍历数组，来绑定监听事件。

    jQuery中事件绑定方式：[code04.html]
        $obj.jquery中监听函数(处理函数);
            例子：
                $(":button").click(fun1);
                为页面中所有的button绑定onClick以及对应处理函数fun1

        html                jquery
        onclick             $obj.click(fun1);
        onchange            $obj.change(fun1);
        onmouseover         $obj.mouseover(fun1);
        ......

        $obj.bind("jQuery监听事件函数名", 处理函数); //以这种方式绑定监听事件，可以解除绑定

            $obj.unbind("jQuery监听事件函数名"); //将指定监听事件从DOM对象身上移除。

            $obj.unbind(); //将所有监听事件从DOM对象身上移除。
        
