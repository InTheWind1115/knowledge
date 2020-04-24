1、HTML语法规范
    所有的标签必须在<>中，大部分<>成对出现。
        例如:<html></html>
    
    也有单标签：<br />

2、标签关系
    包含关系和并列关系.

3、HTML基本结构标签 [code01.html]

4、文档类型声明标签
    <!DOCTYPE html> 当前页面采用的是html5版本来显示网页

5、<html lang="en">
    表示是英文网站还是什么类型的网站

6、<meta charset="UTF-8"> 编码方式

7、常用标签
    标题标签：[code02.html]
        <h1> - <h6> 字体一次缩小

        <h1>我是一级标签</h1>

        head的缩写

        独占一行

    段落标签：paragraph的缩写
        <p>我是一个段落标签<\p>

        会根据浏览器大小自动调整

        段落之间会有一个表较大的空行

    换行标签：break的缩写
        <br />

        强制换行

        但标签

        另起一行显示，和段落显示不同

    文本格式化标签：例如粗体、斜体、下划线等 
        加粗：
            <strong>加粗1</strong> //推荐使用strong 语义更强烈
            <b>加粗2</b>

        倾斜：
            <em>倾斜1</em> //推荐使用em
            <i>倾斜2</i>

        删除：
            <del>删除线1</del> //推荐使用del
            <s>删除线2</s>

        下划线：
            <ins>下划线</ins> //推荐使用ins
            <u>下划线</u>

    盒子标签：没有语义
        <div></div>
            division的缩写，表示分割分区。

            单独占一行

        <span></span>
            意思为跨距
            
            一行可以放多个span,可以理解为小盒子

8、图像标签
    语法格式：
        单标签
        
        <img src="图像URL" />
            属性:
                src:图像的位置
                alt:替换文本, 当图片显示不出来时显示文本
                title:鼠标放到图片上，提示的文字
                width：像素，用来设置图像的宽度 //例如 width="500"
                height：像素，用来设置图像的高度 //例如 height="100"
                    技巧：
                        只设置width和height中的一个，图片会等比例缩放。
                border：设置多少像素的边框 //例如 border="15"
    
    注意点：
        属性写在img标签名的后面

        属性之间是不分先后顺序的

        属性和属性之间必须用空格分开

        属性采用键值对的方式

9、路径：
    目录文件夹
        就是一个普通的文件夹，只不过里面放了一些网页相关的素材

    根目录
        打开目录文件夹的第一层就是根目录

    相对路径：
        以引用文件为所在位置为参考基础。简单来说就是图片相对于HTML页面的位置。

        同一级路径：
            处于同一个目录下。

            <img src="img.jpg" />

        下一级路径：
            <img src="images/img.jpg" />

        上一级路径：
            <img src="../html/img.jpg" />

    绝对路径：
        电脑地址：
            在我们的电脑中的哪个位置，直接在那个地址栏中复制粘贴过来。 //实际开发中不常用

        网络绝对地址：
            <img src="http://wwww.baidu.com /> //使用的也较少

10、超链接标签
    语法格式：anchor的缩写
        <a href="跳转目标" target="目标窗口的弹出方式">文本或图像</a>

            href:
                填写要跳转的URL地址

            target:
                _self //默认值 在当前窗口打开
                _blank //在新的窗口中打开链接


    连接分类：
        外部链接

        内部链接

        空链接
            <a href="#"></a>

        下载链接
            <a href="img.zip">地址链接时文件.exe或者是.zip等压缩包等形式</a>

        锚点链接：
            当我们点击链接，可以快速定位到页面中的某个位置。

            <a href="#life">个人生活</a>
            <h3 id="life">是个文化人</h3>

11、注释
    <!--我是一个注释-->

12、特殊字符
    空格
        &nbsp;
    
    小于号
        &lt;

    大于号
        &gt;

13、表格标签 [code03.html]
    主要作用：
        用来显示，展示数据。

        td: table data
        tr: table row

    表头单元格标签：
        <th>表头标签</th> //table head的缩写

        和td不同的地方在于会居中 加粗

    表格属性：
        align: 设置居中 //align="center"
        boder: 设置边框 //border="1"
        cellpadding: 设置文字距离单元格距离
        cellspacing: 设置单元格单元格之间的距离
        width: 设置宽度
        height: 设置高度

    表格的结构标签：
        将表格划分为头部和表格两大部分
        <thead></thead>
            注意thead标签里面必须有tr标签

        <tbody></tbody>

    合并单元格：
        合并单元格方式：
            跨行合并
                rowspan="数量"

                跨行：最上侧单元格为目标单元格，写合并代码

            跨列合并
                colspan="数量"

                跨列：最左侧单元格为目标单元格，写合并代码

14、列表标签[code05.html]
    作用：
        表格是用来显示数据的，那么列表就是用来布局的。

    无序列表：
        基本语法格式
            <ul>
                <li>榴莲</li>
                <li>臭豆腐</li>
                <li>鲱鱼罐头</li>
            </ul>

        ul标签里面只能放li标签，但是li标签里面能放任何标签

        无序列表的各个列表项之间没有顺序级别之分，是并列的

    有序列表：
        基本语法格式
            <ol>
                <li>刘德华 10000</li>
                <li>刘若英 1000</li>
                <li>pink老师 1</li>
            </ol>

        ol标签里面只能放li标签，但是li标签里面能放任何标签

    自定义列表:
        基本语法格式：
            <dl>
                <dt>关注我们</dt>
                <dd>新浪微博</dd>
                <dd>官方微信</dd>
                <dd>联系我们</dd>
            </dl>

        dl标签里面只能放dt dd标签，但是dt dd标签里面能放任何标签

15、表单标签[code06.html]
    作用:
        收集用户数据

    组成：
        表单域

        表单控件

        提示信息

    表单域
        表单域是一个包含表单元素的区域

        <form></form>

        属性：
            action

            method

            name

    表单控件
        <input>表单元素
            语法格式：
                <input type="值" />

                单标签

                值：
                    text 文本框

                    password 密码框

                    radio 单选按钮

                    checkbox 复选框

                    submit 提交按钮

                    reset 重置按钮

                    button 按钮

                    file 上传文件

                属性：
                    name 给表单元素起名字，radio多选一由name属性实现 单选按钮和复选框要有相同的name值

                    value 设置表单元素的属性值

                    checked 是否选中

                    maxlength 最大输入文本长度
        
            <label>标签
                为input元素定义标注

                用于绑定一个表单元素，当点击<lable>标签内的文本时，浏览器就会自动将焦点(光标)转到或者选择对应的表单元素上，用来增加用户体验

                核心：<lable>标签的for属性应当与相关元素的id属性相同

                <lable for="text">用户名:</lable> 
                <input type="text" id="text" />

        <select>下拉表单元素
            语法：
                <select>
                    <option>山东</option>
                    <option>北京</option>
                    <option>天津</option>
                </select>

            至少包含一对<option>

            有一个selected属性，当值为"selected"时，当前选项默认选中

        <textarea>文本域表单元素
            语法：
                今日反馈:<textarea>请输入内容</textarea>

            属性：
                cols 每行显示多少字符
                rows 显示多少行
        


        










