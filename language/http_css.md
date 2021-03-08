---------------------------------------------------------------------------
File Name: httpcss.md
	 Author: Fan Chongru
	 Mail: chongrufan123@gmail.com
	 Created Time: 2021年03月07日 星期日 14时05分08秒
	 notes: do not repeat yourself DRY
 --------------------------------------------------------------------------

# http_css

<!-- vim-markdown-toc Marked -->

* [http](#http)
    * [标签](#标签)
        * [一些常见的标签](#一些常见的标签)
    * [标签里面有这些常见的属性](#标签里面有这些常见的属性)
* [css](#css)
    * [响应式设置](#响应式设置)
    * [选择器](#选择器)
    * [一些常用的属性](#一些常用的属性)
    * [创建css文件](#创建css文件)
* [javascript](#javascript)
    * [一些内置函数](#一些内置函数)
        * [数据类型](#数据类型)
    * [function](#function)
    * [数组](#数组)
    * [dom](#dom)
    * [事件监听](#事件监听)
    * [jQuery](#jquery)
        * [jQuery导入](#jquery导入)
        * [jq的方法](#jq的方法)
* [emmet](#emmet)
* [参考资料](#参考资料)

<!-- vim-markdown-toc -->
## http
用下面操作可以自动补全
```
!<tab>
```
```
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="cierport" content="width=device-width, initial-scal=1.0">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <title>Document</title>
</head>
<body>
    hi i'm FAN
</body>
</html>
```
### 标签
被\<\>括起来的第一个字符就是标签, 每一个标签里面可以再嵌套标签, 标签里面还可以有属性
#### 一些常见的标签
-   html
    -   header
        -   title
        -   style   //加载样式表
        -   link    //加载外部样式表
            其中有一个rel属性, 用来声明文档类型, 还有一个href属性, 用来放css的链接
    -   body
        -   div //分割区块独占一行  
        -   img     //图片块
            他有如下的几个语义化标签
            -   header  //标题
            -   nav     //导航
            -   section //部分
            -   footer  //页脚
            -   nav     //导航栏, 通常放到header
            -   figure      //用来放图片和描述语言的div
                -   img     //存放图片
                -   figcaption      //图片的语义说明
            -   picture     //在不同设备上加载不同形状的图片
        -   h1  //主标题
        -   h2  //副标题
        -   h6
        -   p   //段落
            -   br/ //换行
            -   strong  //加粗
            -   em      //斜体
            -   button  //按钮
            -   a       //标签中的内容会变成链接显示的内容  
            -   span        //组合行内元素, 经常在input前面
            -   input       //没有结束标记, 可以生成一个文本框
                ```
                <input value="Apple" />
                ```
                里面要添加这个属性
                -   href        //选择要跳转的链接, 系统会自动搜索当前目录, 如果要跳转到其他目录要加上路径
        -   ul  //无序列表
            -   li  //列表
        -   ol  //有序列表
            -   li  //列表
        -   script      //里面可以加载js, 最好放到body的最后, 因为这样可以最后加载交互
### 标签里面有这些常见的属性
-   href    //选择要跳转的链接, 系统会自动搜索当前目录, 如果要跳转到其他目录要加上路径  
    如果是'\#'的话表示跳转到当前页面
-   rel     //声明文档类型
-   class   //设定类名, 中间不可以有空格, 一个标签可以有多个类
-   id
    ```
    id="flank"
    ```
    id在整个html中只能有一个
-   scr     //表示此处的服务器里面的图片链接, 一般用到img标签中, 也可以放到script中用来加载js
-   alt     //在img中, 为图片添加描述信息
-   srcset      //用在要加载不同尺寸但是同一张图
-   data        //后面可以跟-+任意值, 表示对应的东西
    -   data-img        //本标签对应的img

## css
css由选择器, 属性和值构成  
选择器用一对大括号括住属性和值
属性和值由':'分割, 不同的属性由';'分割
### 响应式设置
以@media screen and ( 属性 ){选择器, 属性和值}
```
@media screen and (max-width:400px){
    .feature{
        background:red
    }
}
```
media的设置要从大到小  
media可以放到最后大块的去写, 也可以分开小块小块去写
括号内部的一些属性:
-   max-width       //最大宽度
-   min-width       //最小宽度
### 选择器
可以在其中写一些属性和值, 选择器可以是http里面的标签的选择
```
section div div ul li a{
}
```
其中选择器中有空格, 代表左边标签里面的右边标签, 一层一层嵌套  
也可以有逗号, 表示多个选择器  
```
section.feature-box{}
or
.feature_box{}
```
有点的话表示点后面的类(class)  
有多个点表示选择有这些类都有的标签  
```
li:first-child{}
```
伪类操作, 表示li的第一个子节点, 中间用:隔开, 如果表示最后一个子节点的话是li:last-child  
```
a:hover{}
```
当鼠标移动上去后生效  
```
a:active()
```
当鼠标点击后会生效
### 一些常用的属性
-   color:  颜色
-   opacity:    透明度
-   background  背景
-   font-family 字体
-   font-size   字体大小
-   border      边框(按钮)
-   margin      外间距  (单位:px或%)   
    可以设定一个值是四边, 两个值, 第一个是上下边, 第二个是左右边, 四个值分别是上右下左
-   padding     内间距  
    可以设定一个值是四边, 两个值, 第一个是上下边, 第二个是左右边, 四个值分别是上右下左
-   display     表示div的分布方式  
    他有以下这些值
    -   block   从左到右一行的盒式布局, 也是默认布局
    -   inline  全部跑到一行中, 宽度由其内容决定, 无法人工设置
    -   inline-block    全部跑到一行中, 宽度都一样, 可以人工设置
    -   flex    弹性布局, ***要在div的上级标签中添加***
    -   none    不显示
-   flex_direction  弹性布局方向(此时margin可以设置为auto)(同样在div的上级标签布局)
    他有以下这些值
    -   row 行布局
    -   row-reverse 倒着行布局
    -   column  竖直布局
    -   column-reverse  倒着竖直布局
-   list-style-type     //设置序列前面的标签  
    有以下这些值
    -   none    隐藏前面的标记
-   text-decoration     //下划线  
    -   none    隐藏下划线
    -   undeline    展示下划线
-   text-indent     //表示文字的位置
    当其中尺寸是999999999px时所以人都看不到文字, 也就是文字隐藏
-   background-image        //添加一个背景图片
    -   url("  ")       双引号里面可以放一些保存的图片的链接
-   background-repeat       //是否循环显示图片
    -   no-repeat       //不循环显示图片
-   background-size     //背景图片尺寸, 设置的是宽度
-   pasition        //位置
    -   relative    //可以自动调整图片位置
-   top         //上方的位置, 后面加尺寸数字
-   text-align      //设置页面块排列对其方式
    -   center      //居中对齐
-   background-position     //背景的对齐方式
    -   center      //居中对齐
    - 数字 数字     //第一个数字代表左右位置, 第二个是上下位置
-   border-radius       //设置外边框的形状
    -   50%的话就是圆了
-   text-align      //文字的位置
    -   center      //文字居中显示
-   box-shadow 颜色 水平位置 竖直位置 模糊距离      //显示阴影
    -   box-shadow gray 0 0 10px        //一丝淡淡的阴影
-   border 边框宽度 样式 颜色       //添加边框
    -   border 1px solid white      //添加白色实线1px边框
-   text-transform      //文本的样式
    -   uppercase       //全部大写
-   flex-wrap       //是否自动换行显示  
    -   wrap        //自动换行显示
-   opacity         //透明度, 数字从0-1
### 创建css文件
创建.css文件, 作为外部样式表

## javascript
### 一些内置函数
var 创建变量
alert   发出警告弹窗
prompt  弹出输入框, 里面可以输入提示信息, 类似于input
console.log()       在控制台输出
parseFloat(str)     将字符串转化为数字
this                当前被点击的元素
#### 数据类型
1.  number
2.  string
3.  undefined
### function
```
function go(){
    alert('hi');
}
```
### 数组
mylist.shift()      //将数组的第一项从数组中删除
mylist.pop()        //删除和返回数组最后一项
```
mylist.forEach(function(value, index){
    alert(value);
    )};
```
forEach     //遍历数组的值, 并且可以出来函数
for(setup, comparison, change){}
mylist.lenth        //返回数组的数量

### dom
-   document    //指的是这个网页的http文档
    -   document.getElementsByTagName('p')      //返回一个数组, 其中是网页中的所有p标签的内容
    -   document.getElementsByClassName('classname')    //返回一个数组, 其中是class=classname的所有的标签
    -   document.getElementsById('Idname')    //返回一个值, 其中是Id=Idname的标签
    -   document.querySelector('.done') //返回class是done的第一个标签
    -   document.querySelector('#check') //返回Id是check的第一个标签
    -   document.querySelectorAll('.done') //返回class是done的所有标签
    -   document.querySelectorAll('p') //返回所有p标签
-   firstPtag       //第一个p标签
    -   firstPtag.innerHTML = 'pname'       //改变第一个p标签的值为pname
-   li.className = 'classname'      //将li的类名改为classname
    -   li.className.replace(oldname, newname)      //改变li的类名
    -   li.classList        //返回li的类的数组
    -   li.parentElement        //返回li的父节点
    -   li.chuldren         //返回li的子节点
    -   li.focus        //聚焦到li
-   this        //当前点击的标签
    -   this.attributes['属性']     //抓取this的属性和值
-   input
    -   input.setSelectionRange(num1, num2)     //设置改变的范围num1到num2
-   updateItem.call(this)       //更新这个值
```
//当按下回车之后更新数据
function itemKeypress(event) {
    if(event.which === 13){
        updateItem.call(this);
    }
}
```


### 事件监听
```
numOne.addEventListener("事件", function(){
    程序
});
or
numOne.addEventListener("事件", add) 
function add(){

}
```
事件中有以下这些时间
-   click           当点击时触发
-   mouseenter      当鼠标移入时触发
-   mouseleave      当鼠标移出时触发
-   focus           当光标聚焦时触发
-   blur            当光标失去焦点时触发
-   mousedown       当鼠标按下时触发
-   mouseup         当鼠标松开时触发
-   keydown         当键盘按下时触发
-   keyup           当键盘抬起时触发
-   keypress        当按下回车键触发事件
-   mousemove       当鼠标移入元素时把位置发给鼠标
-   input           当输入时触发事件

-   event       表示监听到的事件  
    -   event.which     表示监听到的键盘上的输入

### jQuery
#### jQuery导入
```
<script scr="导入的JQ的路径"></script>
```
先导入jq库, 然后写下面这一个部分, 表示所有的内容都加载完成之后再加载jq
```
$(document).ready(function() {
    程序
});
or
$(function(){
    程序
});
```
所有的jq的内容都要在前面加\$

#### jq的方法
引入jq的方法如下
```
$("#panel1").hide(300).slideUp(1000);
```
有以下这些方法  
以下的括号里面都表示的是时间
-   hide(time)      隐藏
-   show()          显示
-   slideUp()         上滑隐藏
-   slideDown()       下滑显示
-   delay()         推迟
-   fadeOut()       淡出
-   fadeToggle()    淡化出现或消失(根据现在的状态)  

以下这些括号里面的不是时间
-   css({})         在其中加载css样式  
    里面可以加一些css的属性, 属性之间用逗号隔开
    ```
    $("#panel1").css({
        color:'red', 
        fontWeight:'bold'
    });
    ```
-   html()      改变对象的内容
    ```
    $('#btn1').html('my button')
    ```
-   on(事件, func)      监听事件, 发生函数  
    具体的事件有哪些查看[监听事件](#事件监听)
-   attr(属性名)        返回相应属性的值
-   remove()            移除掉, 不仅仅是隐藏
-   removeClass         移除属性
-   addClass            添加属性
-   is()                判断前面的标签的属性或id是不是括号里面的
-   not()                判断前面的标签的属性或id是不是括号里面的

以下是dom里面的使用
-   \$('li') 返回所有li标签
-   first       第一个标签
-   last        最后一个标签
-   eq()        索引, 括号里面可以加数字0-len
-   children()    返回所有子元素
-   sibling()       兄弟元素
-   parent()        父元素
-   prev()      紧邻的前一个元素
-   next()      紧邻的后一个元素
-   closest()   一直往外找, 知道找到括号里面的属性或id
-   find()      找到所有括号里面的属性或方法
-   filter()    过滤出来括号里面的属性或方法

## emmet
用<c-z>激活插件
-   基本操作
    -   \>  生成元素子节点
    -   +   生成元素兄弟节点
    -   ^   在父级上生成节点
    -   *   生成多个相同的节点
-   属性操作
    -   #   添加id属性的值
    -   .   添加class的值
    -   []  在中括号中可以自定义属性和值
        ```
        <!--td[title="hello" colspan=3]-->
        ```
    -   \$  对重复的元素的属性进行有序编号
    -   \$\$\$  对重复的元素的属性进行有序编号(三位数)
    -   @-  跟在\$后面, 倒序排列
    -   @n  以n为开头进行排序
    -   @-n     以n为开头进行倒叙排序
-   文本操作
    -   {}  可以给元素添加文本内容, 在文本内容在大括号中
-   快捷键
    -   ,   简写式
    -   d   选中被包围的标签
    -   D   选中外部的标签
    -   n   进入下一个编辑点
    -   N   进入上一个编辑点
    -   i   更新img尺寸
    -   m   合并文本行
    -   k   删除标签
    -   j   分解展开空标签
    -   /   注释开关
    -   a   从url生成anchor标签
    -   A   从url引用文本

## 参考资料
1.  [油管最火的web前端教程(小甲鱼翻译)](https://www.bilibili.com/video/BV17b41137yx?from=search&seid=15720733800651476006)
2.  [w3school实战练习](https://www.w3school.com.cn/index.html)
