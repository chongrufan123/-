---------------------------------------------------------------------------
	 File Name: httpcss.md
	 Author: Fan Chongru
	 Mail: chongrufan123@gmail.com
	 Created Time: 2021年03月07日 星期日 14时05分08秒
	 notes: 
 --------------------------------------------------------------------------

# http_css

<!-- vim-markdown-toc Marked -->

* [http](#http)
    * [标签](#标签)
        * [一些常见的标签](#一些常见的标签)
    * [标签里面有这些常见的属性](#标签里面有这些常见的属性)
* [css](#css)
    * [选择器](#选择器)
    * [一些常用的属性](#一些常用的属性)
    * [创建css文件](#创建css文件)
* [emmet](#emmet)

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
            他有如下的几个语义化标签
            -   header  //标题
            -   nav     //导航
            -   section //部分
            -   footer  //页脚
            -   nav     //导航栏, 通常放到header
        -   h1  //主标题
        -   h2  //副标题
        -   h6
        -   p   //段落
            -   br/ //换行
            -   strong  //加粗
            -   em      //斜体
            -   button  //按钮
            -   a       //标签中的内容会变成链接显示的内容  
                里面要添加这个属性
                -   href        //选择要跳转的链接, 系统会自动搜索当前目录, 如果要跳转到其他目录要加上路径
        -   ul  //无序列表
            -   li  //列表
        -   ol  //有序列表
            -   li  //列表
### 标签里面有这些常见的属性
-   href    //选择要跳转的链接, 系统会自动搜索当前目录, 如果要跳转到其他目录要加上路径
-   rel     //声明文档类型
-   class   //设定类名, 中间不可以有空格, 一个标签可以有多个类
-   id
    ```
    id="flank"
    ```
    id在整个html中只能有一个

## css
css由选择器, 属性和值构成  
选择器用一对大括号括住属性和值
属性和值由':'分割, 不同的属性由';'分割
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

### 创建css文件
创建.css文件, 作为外部样式表

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
