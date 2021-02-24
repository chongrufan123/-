# shell
命令解释器，将外层应用解释为机械码  
也是一个编程语言，可以直接调用linux系统命令

<!-- vim-markdown-toc Marked -->

* [shell语言的分类](#shell语言的分类)
    * [查看系统支持的shell语言](#查看系统支持的shell语言)
* [shell脚本的执行方法](#shell脚本的执行方法)
    * [echo输出命令](#echo输出命令)
    * [第一个脚本](#第一个脚本)
    * [执行脚本](#执行脚本)
* [Bash的基本功能](#bash的基本功能)
    * [历史命令和补全](#历史命令和补全)
        * [history 选项](#history-选项)
        * [历史命令的调用](#历史命令的调用)
    * [命令别名和常用快捷键](#命令别名和常用快捷键)
        * [alias](#alias)
        * [命令执行循序](#命令执行循序)
        * [常用快捷键](#常用快捷键)

<!-- vim-markdown-toc -->

## shell语言的分类
1. Bourne
- sh
- ksh  
- Bash(linux中用的,和sh兼容)
- psh
- zsh
2. C
- csh
- tcsh

### 查看系统支持的shell语言
```
cat /etc/shells
# /etc/shells: valid login shells
/bin/sh
/bin/bash
/usr/bin/bash
/bin/rbash
/usr/bin/rbash
/bin/dash
/usr/bin/dash
```
直接在交互框中输入shell的名字就可以切换shell 

## shell脚本的执行方法
### echo输出命令
```
echo [选项] [输出内容]
```
选项
- -e    支持反斜线控制的字符转化

|控制字符|作用|
|--:--|:----|
|\\|输出\\|
|\a|输出警告声|
|\b|退格键|
|\c|取消输出行末的换行符|
|\e|ESCAPE键|
|\f|换页键|
|\n|换行|
|\r|回车|
|\t|tab|
|\v|垂直制表符|
|\0nnn|按八进制ascll输出|
|\xhh|按16位ascll输出|

```
echo -e "\e[1;31m abcd \e[0m"   //\e[1;开启颜色输出,31m红色
```

### 第一个脚本
开头必须要由
```
#!/bin/Bash
```
以sh为后缀

### 执行脚本
1. 赋予权限,直接执行(dui)
```
chmod 755 hello.sh
./hello.sh
```
2. 通过Bash调用执行脚本
```
bash hello.sh
```
## Bash的基本功能
### 历史命令和补全
#### history [选项][历史命令保存文件]
history [选项][历史命令保存文件]  
选项  
- -c 清空历史命令  
- -w 把缓存中的历史命令写入文件~/.bash_history

#### 历史命令的调用
- 上下箭头调用之前的历史命令
- !n重复调用第n调命令
- !! 重复调用上一条命令
- !字串 重复调用最后一条该字串开头的命令

### 命令别名和常用快捷键
#### alias
```
alias   //查询别名
alias 别名='原来命令'   //设置别名
unalias 别名    //删除别名
```
在/root/.bashrc中改变可以让别名永久生效
#### 命令执行循序
1. 绝对路径和相对路径执行的命令
2. 执行别名
3. Bash的内部命令
4. $PATH环境变量定义的第一个命令

#### 常用快捷键

