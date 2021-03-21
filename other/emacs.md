
# Table of Contents

1.  [一些基本操作](#orgff89bac)
    1.  [markdown-mode](#orgcb71677)
    2.  [org mode相关内容](#orgebae06c)
        1.  [capture相关的内容 **\***](#orgf6a5bab)
        2.  [agenda](#orgb4987e8)
    3.  [文件管理](#org84bf8e8)
    4.  [eaf](#orgff78ffa)
2.  [常用的命令](#org8b97ea5)



<a id="orgff89bac"></a>

# 一些基本操作

<table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">


<colgroup>
<col  class="org-left" />

<col  class="org-left" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-left">操作</th>
<th scope="col" class="org-left">作用</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-left">c-n</td>
<td class="org-left">下一行</td>
</tr>


<tr>
<td class="org-left">c-p</td>
<td class="org-left">前一行</td>
</tr>


<tr>
<td class="org-left">c-f</td>
<td class="org-left">前一个字符</td>
</tr>


<tr>
<td class="org-left">c-b</td>
<td class="org-left">后一个字符</td>
</tr>


<tr>
<td class="org-left">c-k</td>
<td class="org-left">从光标位置到末尾删掉</td>
</tr>


<tr>
<td class="org-left">c-a</td>
<td class="org-left">回到行首</td>
</tr>


<tr>
<td class="org-left">c-e</td>
<td class="org-left">去到行尾</td>
</tr>


<tr>
<td class="org-left">m-<</td>
<td class="org-left">回到编辑区域最开始的位置</td>
</tr>


<tr>
<td class="org-left">m-></td>
<td class="org-left">去到编辑区域最后的位置</td>
</tr>


<tr>
<td class="org-left">c-v</td>
<td class="org-left">向下翻一屏</td>
</tr>


<tr>
<td class="org-left">m-v</td>
<td class="org-left">向上翻一屏</td>
</tr>


<tr>
<td class="org-left">m-f</td>
<td class="org-left">后一个单词</td>
</tr>


<tr>
<td class="org-left">m-b</td>
<td class="org-left">前一个单词</td>
</tr>


<tr>
<td class="org-left">m-a</td>
<td class="org-left">句子的最前面</td>
</tr>


<tr>
<td class="org-left">m-e</td>
<td class="org-left">句子的最后面</td>
</tr>


<tr>
<td class="org-left">c-l</td>
<td class="org-left">将光标显示到屏幕中央</td>
</tr>


<tr>
<td class="org-left">c-l c-l</td>
<td class="org-left">光标显示到屏幕上方</td>
</tr>


<tr>
<td class="org-left">c-u</td>
<td class="org-left">之后加数字</td>
</tr>


<tr>
<td class="org-left">c-g</td>
<td class="org-left">终止emacs命令</td>
</tr>


<tr>
<td class="org-left">c-x 1</td>
<td class="org-left">只保留当前窗格</td>
</tr>


<tr>
<td class="org-left">c-x 2</td>
<td class="org-left">上下分屏</td>
</tr>


<tr>
<td class="org-left">c-x 3</td>
<td class="org-left">左右分屏</td>
</tr>


<tr>
<td class="org-left">c-d</td>
<td class="org-left">删除前一个字符</td>
</tr>


<tr>
<td class="org-left">m-k</td>
<td class="org-left">删除到句尾的字符</td>
</tr>


<tr>
<td class="org-left">c-@</td>
<td class="org-left">高亮显示</td>
</tr>


<tr>
<td class="org-left">c-y</td>
<td class="org-left">修改召回</td>
</tr>


<tr>
<td class="org-left">m-y</td>
<td class="org-left">跟在c-y之后,可以召回历史</td>
</tr>


<tr>
<td class="org-left">c-/</td>
<td class="org-left">撤销</td>
</tr>


<tr>
<td class="org-left">c-x c-f</td>
<td class="org-left">寻找一个文件</td>
</tr>


<tr>
<td class="org-left">c-x c-s</td>
<td class="org-left">保存</td>
</tr>


<tr>
<td class="org-left">c-x c-b</td>
<td class="org-left">列出缓存区</td>
</tr>


<tr>
<td class="org-left">c-x b 缓存区文件名字</td>
<td class="org-left">去缓存区的文件</td>
</tr>


<tr>
<td class="org-left">c-x s</td>
<td class="org-left">保存多个缓存区</td>
</tr>


<tr>
<td class="org-left">m-x</td>
<td class="org-left">命令名拓展</td>
</tr>


<tr>
<td class="org-left">c-z</td>
<td class="org-left">挂起</td>
</tr>


<tr>
<td class="org-left">fg/%emacs</td>
<td class="org-left">回到emacs</td>
</tr>


<tr>
<td class="org-left">c-x f</td>
<td class="org-left">设置最长一行的字符数</td>
</tr>


<tr>
<td class="org-left">c-s</td>
<td class="org-left">向前搜索</td>
</tr>


<tr>
<td class="org-left">c-r</td>
<td class="org-left">向后搜索</td>
</tr>


<tr>
<td class="org-left">c-m-v</td>
<td class="org-left">另一个窗口向下切屏</td>
</tr>


<tr>
<td class="org-left">c-m-s-v</td>
<td class="org-left">另一个窗口向上切屏</td>
</tr>


<tr>
<td class="org-left">c-x o</td>
<td class="org-left">切换窗口</td>
</tr>


<tr>
<td class="org-left">m-w</td>
<td class="org-left">复制</td>
</tr>


<tr>
<td class="org-left">左shift-w</td>
<td class="org-left">剪切</td>
</tr>


<tr>
<td class="org-left">c-y</td>
<td class="org-left">粘贴</td>
</tr>


<tr>
<td class="org-left">c-x 左shift-e</td>
<td class="org-left">执行</td>
</tr>


<tr>
<td class="org-left">M-%</td>
<td class="org-left">替换</td>
</tr>


<tr>
<td class="org-left">c-t</td>
<td class="org-left">光标前和光标所在两个字符替换</td>
</tr>


<tr>
<td class="org-left">m-t</td>
<td class="org-left">将光标前的单词和光标所在的单词替换</td>
</tr>


<tr>
<td class="org-left">m-=</td>
<td class="org-left">字符统计</td>
</tr>


<tr>
<td class="org-left">c-x k</td>
<td class="org-left">杀死当前buffer</td>
</tr>


<tr>
<td class="org-left">在buffer选择界面中</td>
<td class="org-left">&#xa0;</td>
</tr>


<tr>
<td class="org-left">d</td>
<td class="org-left">标记删除</td>
</tr>


<tr>
<td class="org-left">u</td>
<td class="org-left">取消当前行标记</td>
</tr>


<tr>
<td class="org-left">U</td>
<td class="org-left">取消全部标记</td>
</tr>


<tr>
<td class="org-left">x</td>
<td class="org-left">执行操作</td>
</tr>


<tr>
<td class="org-left">?</td>
<td class="org-left">查看帮助</td>
</tr>


<tr>
<td class="org-left">c-x 0</td>
<td class="org-left">关闭当前分屏</td>
</tr>


<tr>
<td class="org-left">c-x ^</td>
<td class="org-left">增加高度</td>
</tr>


<tr>
<td class="org-left">c-x {</td>
<td class="org-left">减少宽度</td>
</tr>


<tr>
<td class="org-left">c-x }</td>
<td class="org-left">增加宽度</td>
</tr>


<tr>
<td class="org-left">m-o</td>
<td class="org-left">切换屏幕</td>
</tr>


<tr>
<td class="org-left">在切换屏幕中的一些功能</td>
<td class="org-left">&#xa0;</td>
</tr>


<tr>
<td class="org-left">x</td>
<td class="org-left">删除窗口</td>
</tr>


<tr>
<td class="org-left">m</td>
<td class="org-left">移动窗口</td>
</tr>
</tbody>
</table>


<a id="orgcb71677"></a>

## markdown-mode

<table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">


<colgroup>
<col  class="org-left" />

<col  class="org-left" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-left">命令</th>
<th scope="col" class="org-left">作用</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-left">c-c c-a</td>
<td class="org-left">插入超链接,打开插入链接界面</td>
</tr>


<tr>
<td class="org-left">下面是这些链接的后面的字母的意义</td>
<td class="org-left">&#xa0;</td>
</tr>


<tr>
<td class="org-left">l</td>
<td class="org-left">插入链接,分别输入url,名称和标题</td>
</tr>


<tr>
<td class="org-left">u</td>
<td class="org-left">插入一个纯url链接,只显示链接</td>
</tr>


<tr>
<td class="org-left">f</td>
<td class="org-left">插入一个脚注,并在下方插入脚注文本,就是类似注释一样</td>
</tr>


<tr>
<td class="org-left">w</td>
<td class="org-left">插入一个wiki链接</td>
</tr>


<tr>
<td class="org-left">&#xa0;</td>
<td class="org-left">&#xa0;</td>
</tr>


<tr>
<td class="org-left">c-c c-i</td>
<td class="org-left">插入图片</td>
</tr>


<tr>
<td class="org-left">c-c c-s</td>
<td class="org-left">插入样式</td>
</tr>


<tr>
<td class="org-left">下面是这些链接的后面的字母的意义</td>
<td class="org-left">&#xa0;</td>
</tr>


<tr>
<td class="org-left">e</td>
<td class="org-left">插入斜体</td>
</tr>


<tr>
<td class="org-left">s</td>
<td class="org-left">插入删除线</td>
</tr>


<tr>
<td class="org-left">c</td>
<td class="org-left">标记代码标签</td>
</tr>


<tr>
<td class="org-left">k</td>
<td class="org-left">加入kbd标记,表示是从键盘输入的</td>
</tr>


<tr>
<td class="org-left">b</td>
<td class="org-left">加一个块引用</td>
</tr>


<tr>
<td class="org-left">p</td>
<td class="org-left">缩进</td>
</tr>


<tr>
<td class="org-left">l</td>
<td class="org-left">插入链接</td>
</tr>


<tr>
<td class="org-left">t</td>
<td class="org-left">插入表格</td>
</tr>


<tr>
<td class="org-left">h</td>
<td class="org-left">加入二级目录和分割线</td>
</tr>


<tr>
<td class="org-left">F</td>
<td class="org-left">加入可以收缩的东西</td>
</tr>


<tr>
<td class="org-left">C</td>
<td class="org-left">插入大块的编程语言,可以自己选择语言</td>
</tr>


<tr>
<td class="org-left">q</td>
<td class="org-left">加入引用</td>
</tr>


<tr>
<td class="org-left">数字</td>
<td class="org-left">加入几级标题</td>
</tr>


<tr>
<td class="org-left">c-c -</td>
<td class="org-left">插入分割线,前面可以跟数字</td>
</tr>


<tr>
<td class="org-left">\\!</td>
<td class="org-left">插入一级标题和分隔符</td>
</tr>


<tr>
<td class="org-left">c-c c-o</td>
<td class="org-left">打开光标所在链接</td>
</tr>
</tbody>
</table>


<a id="orgebae06c"></a>

## org mode相关内容

-   基本
    -   \\\*后面可以跟一个清单,\\\*后面可以跟很多个\\\*\\\*
    -   s+右 加一个todo或done标签
    -   c-c . 激活的标签
    -   c-c ! 非激活的标签
    -   \&#x00ad;\&#x00ad; 时间区间
-   三个状态
    -   c-c c-s schedule
    -   c-c c-d deadline
    -   closed 要在开头加\*+STARTUP: logdone
    -   c-c c-c 添加tag 可以在文件开头添加\*+TAGS: 小王(w)
-   不同的显示样式
    有三种大纲显示模式模式,又分为两种不同的状态
    -   子项
        
        -   FOLDED 折叠,全部折叠进来
        -   CHILDREN 只是释放一级
        -   SUBTREE 全部释放
        
        TAB可以切换,S-TAB可以调用全局显示状态
    -   全局
        
        -   overview 概览
        -   CONTENTS 目次
        -   SHOW ALL 全部显示
        
        可以在键入S-TAB在这三种模式切换,C-u C-u C-u TAB直接切换到全局  
        org-startup-folded 是设置打开org之后默认显示状态,默认是概览  
        如果针对单独文件设置,在最开始加
        
            *+STAARTUP: overview
            可选有
            content
            overview
            shwoall
-   移动相关
    
    <table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
    
    
    <colgroup>
    <col  class="org-left" />
    
    <col  class="org-left" />
    </colgroup>
    <thead>
    <tr>
    <th scope="col" class="org-left">命令</th>
    <th scope="col" class="org-left">作用</th>
    </tr>
    </thead>
    
    <tbody>
    <tr>
    <td class="org-left">C-c C-n</td>
    <td class="org-left">下一个标题</td>
    </tr>
    
    
    <tr>
    <td class="org-left">C-c C-p</td>
    <td class="org-left">上一个标题</td>
    </tr>
    
    
    <tr>
    <td class="org-left">C-c C-f</td>
    <td class="org-left">下一个同级标题</td>
    </tr>
    
    
    <tr>
    <td class="org-left">C-c C-b</td>
    <td class="org-left">上一个同级标题</td>
    </tr>
    
    
    <tr>
    <td class="org-left">C-c C-u</td>
    <td class="org-left">跳转到父级目录</td>
    </tr>
    </tbody>
    </table>
-   结构编辑  
    
    <table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
    
    
    <colgroup>
    <col  class="org-left" />
    
    <col  class="org-left" />
    </colgroup>
    <thead>
    <tr>
    <th scope="col" class="org-left">命令</th>
    <th scope="col" class="org-left">作用</th>
    </tr>
    </thead>
    
    <tbody>
    <tr>
    <td class="org-left">M-RET</td>
    <td class="org-left">创建同级别标题</td>
    </tr>
    
    
    <tr>
    <td class="org-left">M-S-RET</td>
    <td class="org-left">创建同级别todo条目</td>
    </tr>
    
    
    <tr>
    <td class="org-left">TAB</td>
    <td class="org-left">循环改变未指定标题名的标题等级</td>
    </tr>
    
    
    <tr>
    <td class="org-left">M-LEFT/RIGHT</td>
    <td class="org-left">将当前标题升级或降级</td>
    </tr>
    
    
    <tr>
    <td class="org-left">M-UP/DOWN</td>
    <td class="org-left">上下交换同级别</td>
    </tr>
    
    
    <tr>
    <td class="org-left">C-c C-w</td>
    <td class="org-left">将当前条目放置到指定条目</td>
    </tr>
    
    
    <tr>
    <td class="org-left">C-x n s/w</td>
    <td class="org-left">将当前子项为单位变宽或变窄</td>
    </tr>
    </tbody>
    </table>
-   清单列表
    -   ::指定列表的说明,将条目和说明隔开  
        
        <table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
        
        
        <colgroup>
        <col  class="org-left" />
        
        <col  class="org-left" />
        </colgroup>
        <thead>
        <tr>
        <th scope="col" class="org-left">命令</th>
        <th scope="col" class="org-left">作用</th>
        </tr>
        </thead>
        
        <tbody>
        <tr>
        <td class="org-left">TAB</td>
        <td class="org-left">类似与标题的折叠</td>
        </tr>
        
        
        <tr>
        <td class="org-left">M-RET</td>
        <td class="org-left">创建同级项目</td>
        </tr>
        
        
        <tr>
        <td class="org-left">M-S-RET</td>
        <td class="org-left">新建带有复选框的同级项</td>
        </tr>
        
        
        <tr>
        <td class="org-left">M-S-UP/DOWN</td>
        <td class="org-left">上下移动当前项</td>
        </tr>
        
        
        <tr>
        <td class="org-left">C-c C-c</td>
        <td class="org-left">勾选复选框</td>
        </tr>
        
        
        <tr>
        <td class="org-left">C-c \_</td>
        <td class="org-left">循环修改当前项目条目</td>
        </tr>
        </tbody>
        </table>
-   表格
    
    <table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
    
    
    <colgroup>
    <col  class="org-left" />
    
    <col  class="org-left" />
    
    <col  class="org-left" />
    </colgroup>
    <thead>
    <tr>
    <th scope="col" class="org-left">命令</th>
    <th scope="col" class="org-left">作用</th>
    <th scope="col" class="org-left">&#xa0;</th>
    </tr>
    </thead>
    
    <tbody>
    <tr>
    <td class="org-left">\\</td>
    <td class="org-left">- TAB</td>
    <td class="org-left">创建分割符</td>
    </tr>
    
    
    <tr>
    <td class="org-left">创建第一行之后按TAB</td>
    <td class="org-left">创建表格</td>
    <td class="org-left">&#xa0;</td>
    </tr>
    
    
    <tr>
    <td class="org-left">C-c C-c</td>
    <td class="org-left">重新对齐表格</td>
    <td class="org-left">&#xa0;</td>
    </tr>
    
    
    <tr>
    <td class="org-left">TAB</td>
    <td class="org-left">移动到下一个单元格</td>
    <td class="org-left">&#xa0;</td>
    </tr>
    
    
    <tr>
    <td class="org-left">S-TAB</td>
    <td class="org-left">移动到上一个单元格</td>
    <td class="org-left">&#xa0;</td>
    </tr>
    
    
    <tr>
    <td class="org-left">S-UP/DOWN/LEFT/RIGHT</td>
    <td class="org-left">交换单元格为上下左右的单元格</td>
    <td class="org-left">&#xa0;</td>
    </tr>
    
    
    <tr>
    <td class="org-left">M-LEFT/RIGHT</td>
    <td class="org-left">交换左右的列</td>
    <td class="org-left">&#xa0;</td>
    </tr>
    
    
    <tr>
    <td class="org-left">M-S-LEFT</td>
    <td class="org-left">删除当前列</td>
    <td class="org-left">&#xa0;</td>
    </tr>
    
    
    <tr>
    <td class="org-left">M-S-RIGHT</td>
    <td class="org-left">向右插入新列</td>
    <td class="org-left">&#xa0;</td>
    </tr>
    
    
    <tr>
    <td class="org-left">M-UP/DOWN</td>
    <td class="org-left">上下移动当前列</td>
    <td class="org-left">&#xa0;</td>
    </tr>
    
    
    <tr>
    <td class="org-left">M-S-UP</td>
    <td class="org-left">删除当前行</td>
    <td class="org-left">&#xa0;</td>
    </tr>
    
    
    <tr>
    <td class="org-left">M-S-DOWN</td>
    <td class="org-left">在当前行上方插入新行</td>
    <td class="org-left">&#xa0;</td>
    </tr>
    
    
    <tr>
    <td class="org-left">C-c -</td>
    <td class="org-left">在当前行上加入分割线</td>
    <td class="org-left">&#xa0;</td>
    </tr>
    
    
    <tr>
    <td class="org-left">C-c RET</td>
    <td class="org-left">在当前行下方加入分割线</td>
    <td class="org-left">&#xa0;</td>
    </tr>
    
    
    <tr>
    <td class="org-left">C-x ^</td>
    <td class="org-left">根据当前列给表格排序</td>
    <td class="org-left">&#xa0;</td>
    </tr>
    </tbody>
    </table>
-   超链接
    
        两种定义方式
          带说明的超链接
          [[https://www.baidu.com][百度]]
          不带说明的超链接
          [[https://www.baidu.com]]
        链接方式
          内部链接  
          可以链接到当前文章某处  
          [[MY Target][目标]]  
          被链接处加上符号  
          <<MY Target>>
          外部链接
          可以指定行号
          [[file:~/.emacs.d/init.el::15][打开init.el的第15行]]
          指定特殊目标
          [[file:~/.emacs.d/test.el::Teat Target][打开test.el的Test Target标记]]
    
    -   处理超链接
        
        <table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
        
        
        <colgroup>
        <col  class="org-left" />
        
        <col  class="org-left" />
        </colgroup>
        <thead>
        <tr>
        <th scope="col" class="org-left">命令</th>
        <th scope="col" class="org-left">作用</th>
        </tr>
        </thead>
        
        <tbody>
        <tr>
        <td class="org-left">C-c C-l</td>
        <td class="org-left">插入链接</td>
        </tr>
        
        
        <tr>
        <td class="org-left">C-c C-l</td>
        <td class="org-left">当光标在一个超链接上面时编辑超链接</td>
        </tr>
        
        
        <tr>
        <td class="org-left">C-c C-o</td>
        <td class="org-left">打开超链接</td>
        </tr>
        
        
        <tr>
        <td class="org-left">C-c l</td>
        <td class="org-left">储存当前位置是超链接</td>
        </tr>
        </tbody>
        </table>
-   角注标记
    -   添加角注链接

-   图片
    -   创建图片
        
            [[file:~/a.png]]
    -   用C-c C-x C-v 的方式让图片显示出来
        
        [图片](file:///home/fan/a.png)

-   字体
    
    <table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
    
    
    <colgroup>
    <col  class="org-left" />
    
    <col  class="org-left" />
    
    <col  class="org-left" />
    </colgroup>
    <thead>
    <tr>
    <th scope="col" class="org-left">符号</th>
    <th scope="col" class="org-left">描述</th>
    <th scope="col" class="org-left">展示</th>
    </tr>
    </thead>
    
    <tbody>
    <tr>
    <td class="org-left">两边\*</td>
    <td class="org-left">粗体</td>
    <td class="org-left">**粗体**</td>
    </tr>
    
    
    <tr>
    <td class="org-left">两边/</td>
    <td class="org-left">斜体</td>
    <td class="org-left">*斜体*</td>
    </tr>
    
    
    <tr>
    <td class="org-left">两边+</td>
    <td class="org-left">删除线</td>
    <td class="org-left"><del>删除线</del></td>
    </tr>
    
    
    <tr>
    <td class="org-left">两边\_</td>
    <td class="org-left">下划线</td>
    <td class="org-left"><span class="underline">下划线</span></td>
    </tr>
    </tbody>
    </table>

-   导出和发布
    -   自带导出功能
        
        导出时数据设置
        
            #+TITLE:
            #+AUTHOR:
            #+EMAIL:
            #+KEYWORDS:
    -   导出为markdown
        
        M-x org-md-export-as-markdown
-   代办事项
    -   基础
        
        当标题开头是todo时,该标题就会成为一个代办事项

-   按键

<table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">


<colgroup>
<col  class="org-left" />

<col  class="org-left" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-left">按键</th>
<th scope="col" class="org-left">作用</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-left">C-c C-t</td>
<td class="org-left">选择代办状态</td>
</tr>


<tr>
<td class="org-left">C-c ,</td>
<td class="org-left">选择优先级</td>
</tr>


<tr>
<td class="org-left">S-UP/DOWN</td>
<td class="org-left">提升降低优先级</td>
</tr>


<tr>
<td class="org-left">[/]或[%]</td>
<td class="org-left">显示进度</td>
</tr>


<tr>
<td class="org-left">C-c C-c</td>
<td class="org-left">刷新进度</td>
</tr>
</tbody>
</table>

-   标签 
    
    在标题后由两个冒号包住的单词  
    
    子标题的标签可以继承父标题的标签  
    
    也可以在文件开头写下面这段话,让当前文件的所有标签继承与他
    
        *+FILETAGS: :EvanMeek:
    
    在文件开头指定该文件的标签
    
        *+TAGS: @work(w) @home(h)
    
    -   标签组
    
    用[]之间的就是多选的标签
    
    在{}之间的就是单选的标签

-   按键

<table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">


<colgroup>
<col  class="org-left" />

<col  class="org-left" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-left">按键</th>
<th scope="col" class="org-left">作用</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-left">C-c C-q</td>
<td class="org-left">为当前标题创建新的标签</td>
</tr>


<tr>
<td class="org-left">C-c C-c</td>
<td class="org-left">同上,不过只有光标在标签上面才有效</td>
</tr>
</tbody>
</table>

-   属性
    属性是包含在
    
        :PROPERTIES:...
    
    之间的
    
    -   按键

<table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">


<colgroup>
<col  class="org-left" />

<col  class="org-left" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-left">按键</th>
<th scope="col" class="org-left">作用</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-left">C-c C-x p</td>
<td class="org-left">设置属性</td>
</tr>


<tr>
<td class="org-left">C-c C-c d</td>
<td class="org-left">删除当前属性</td>
</tr>
</tbody>
</table>

-   时间和日期
    -   时间缀
        
        -   基本时间缀
            
                <2020-05-19 一>
        
        -   有规律的时间缀
            
                <2020-05-19 一 +1y>
            
            每年都会提醒
        
        -   日记样式的时间厝
        
        -   时间日期范围
            
            两个时间厝之间用&#x2013;连接
        
        -   非活动时间错
            
                [2020-05-18 一]
        
        不会被agenda管理
    
    -   创建时间错
        -   键位

<table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">


<colgroup>
<col  class="org-left" />

<col  class="org-left" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-left">键位</th>
<th scope="col" class="org-left">作用</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-left">C-c .</td>
<td class="org-left">插入时间厝</td>
</tr>


<tr>
<td class="org-left">C-c !</td>
<td class="org-left">插入非活动时间厝</td>
</tr>


<tr>
<td class="org-left">S-LEFT/RIGHT</td>
<td class="org-left">将时间厝提前或后退一天</td>
</tr>


<tr>
<td class="org-left">S-UP/DOWN</td>
<td class="org-left">支持对年月日周等变换</td>
</tr>


<tr>
<td class="org-left">C-c C-d</td>
<td class="org-left">插入截止时间错</td>
</tr>


<tr>
<td class="org-left">C-c C-s</td>
<td class="org-left">插入开始时间厝</td>
</tr>


<tr>
<td class="org-left">C-c C-x C-i</td>
<td class="org-left">开始为当前代办计时</td>
</tr>


<tr>
<td class="org-left">C-c C-x C-o</td>
<td class="org-left">停止计时</td>
</tr>


<tr>
<td class="org-left">C-c C-x C-e</td>
<td class="org-left">更新计时任务进度</td>
</tr>


<tr>
<td class="org-left">C-c C-x C-q</td>
<td class="org-left">取消计时</td>
</tr>


<tr>
<td class="org-left">C-c C-x C-j</td>
<td class="org-left">跳转到计时任务</td>
</tr>
</tbody>
</table>

-   截止日期和计划安排


<a id="orgf6a5bab"></a>

### capture相关的内容 **\***

[参考资料](https://www.zmonster.me/2018/02/28/org-mode-capture.html)

一个模板主要有5个部分构成

<table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">


<colgroup>
<col  class="org-left" />

<col  class="org-left" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-left">模板组成</th>
<th scope="col" class="org-left">描述</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-left">key</td>
<td class="org-left">选择模板的字符</td>
</tr>


<tr>
<td class="org-left">description</td>
<td class="org-left">展示模板的描述</td>
</tr>


<tr>
<td class="org-left">type</td>
<td class="org-left">新增内容的类型</td>
</tr>


<tr>
<td class="org-left">target</td>
<td class="org-left">新增内容的存储位置</td>
</tr>


<tr>
<td class="org-left">template</td>
<td class="org-left">新增内容的模板</td>
</tr>
</tbody>
</table>

    例子:
    '("t" "Task" entry (file+headline "" "Tasks") "* TODO %?\n  %u\n  %a")

-   新增内容类型type

<table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">


<colgroup>
<col  class="org-left" />

<col  class="org-left" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-left">type</th>
<th scope="col" class="org-left">description</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-left">entry</td>
<td class="org-left">带有headline的一个节点</td>
</tr>


<tr>
<td class="org-left">item</td>
<td class="org-left">一个列表项</td>
</tr>


<tr>
<td class="org-left">checkitem</td>
<td class="org-left">一个checkbox列表项</td>
</tr>


<tr>
<td class="org-left">plain</td>
<td class="org-left">普通文本</td>
</tr>
</tbody>
</table>


<a id="orgb4987e8"></a>

### agenda

[org使用手册](https://grass.show/omegat/target/Org%E4%BD%BF%E7%94%A8%E6%89%8B%E5%86%8C(%E5%AE%8C%E6%95%B4%E7%89%88).html)


<a id="org84bf8e8"></a>

## 文件管理


<a id="orgff78ffa"></a>

## eaf

-   浏览器

<table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">


<colgroup>
<col  class="org-left" />

<col  class="org-left" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-left">命令</th>
<th scope="col" class="org-left">作用</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-left">m</td>
<td class="org-left">设置书签</td>
</tr>


<tr>
<td class="org-left">f</td>
<td class="org-left">跳转</td>
</tr>
</tbody>
</table>


<a id="org8b97ea5"></a>

# 常用的命令

<table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">


<colgroup>
<col  class="org-left" />

<col  class="org-left" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-left">命令</th>
<th scope="col" class="org-left">作用</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-left">replace-string</td>
<td class="org-left">替换字符串</td>
</tr>


<tr>
<td class="org-left">recover file</td>
<td class="org-left">恢复自动保存文件</td>
</tr>


<tr>
<td class="org-left">fundamental-mode</td>
<td class="org-left">切换模式</td>
</tr>


<tr>
<td class="org-left">text-mode</td>
<td class="org-left">切换文本编辑模式</td>
</tr>


<tr>
<td class="org-left">auto-fill-mode</td>
<td class="org-left">自动折行开启(关闭)</td>
</tr>


<tr>
<td class="org-left">benchmark-init/show-durations-tree</td>
<td class="org-left">树状图展示启动耗时</td>
</tr>


<tr>
<td class="org-left">benchmark-init/show-durations-tabulated</td>
<td class="org-left">表格展示启动耗时</td>
</tr>


<tr>
<td class="org-left">sort-lines</td>
<td class="org-left">行排序</td>
</tr>


<tr>
<td class="org-left">count words</td>
<td class="org-left">字符统计</td>
</tr>


<tr>
<td class="org-left">eaf-open-bookmark</td>
<td class="org-left">展示当前书签</td>
</tr>
</tbody>
</table>

