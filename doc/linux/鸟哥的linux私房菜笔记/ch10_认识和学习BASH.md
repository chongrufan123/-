# 第十章, 认识和学习BASH
## 认识BASH这个shell
### 硬件, 核心和shell
-   硬件: 声卡芯片配置
-   核心管理:操作系统的核心可以支持这个芯片组, 提供芯片的驱动程序
-   应用程序:用户和系统交互

用户通过shell和核心进行沟通, 然后核心将用户的需求传递到硬件  

bash是GNU计划中重要的工具软件之一, 也是Linux distributions的标准shell  

他有以下优点
-   命令编修能力(history):能记住之前使用的命令
-   命令与文件补全: tab键
-   命令别名设置功能: alias
-   工作控制, 前景背景控制  
-   程序化脚本(shell script)
-   万用字符(Wildcard)

通过type可以查询指令是否是bash内置指令
```shell
type [-tpa] name
选项和参数:
 :不加选项时, 会显示出是外部指令还是内部指令
-t: 以以下字眼显示出他的含义
    -   file:外部指令
    -   alias:别名
    -   builtin:内置指令
-p: 如果后面的name是外部指令时才会显示完整文件名
-a: 如果由PATH变量定义的路径中, 将所有含有name的指令都列出来
```

## shell的变量功能
变量设置规则
-   等号两边不能接空白字符
-   变量名称只能是英文字母和数字, 开头不能是数字
-   双引号里面可以引用特殊字符, 单引号里面不可以
-   若要变量在其他子程序中执行, 要转化为环境变量
  ```shell
    export PATH  
  ```

-   通常大写字符是系统默认变量, 用户的变量的话就小写就好(非强制)
-   取消变量的方法
  ```shell
    unset myname  
  ```

### 环境变量
-   env
  ```shell
    env     列出目前环境下所有环境变量和内容
    本机执行, 得到如下信息:

    SHELL=/bin/bash                                         :目前使用的是哪个shell
    no_proxy=127.0.0.1,localhost                            
    LANGUAGE=zh_CN.UTF-8                                    :语系编码 
    NO_AT_BRIDGE=1
    PWD=/home/pi/Desktop/study/notes/book                   :目前工作目录
    LOGNAME=pi                                              :登录者的登录账号
    XDG_SESSION_TYPE=tty
    _=/usr/bin/env                                          :上一个使用指令的最后一个参数
    HOME=/home/pi                                           :使用者的主文件夹
    LANG=zh_CN.UTF-8
    LS_COLORS=rs=0:di=01;34:ln=01;36:mh=00:pi=...           :颜色显示
    VIMRUNTIME=/usr/share/vim/vim82                         
    SSH_CONNECTION=192.168.137.1 11524 192.168.137.168 22
    VIM=/usr/share/vim
    XDG_SESSION_CLASS=user
    TERM=xterm                                              :终端使用的环境是什么类型
    USER=pi                                                 :使用者名称
    SHLVL=1
    LC_MESSAGES=zh_CN.UTF-8
    XDG_SESSION_ID=14
    XDG_RUNTIME_DIR=/run/user/1000
    MYVIMRC=/home/pi/.vimrc
    SSH_CLIENT=192.168.137.1 11524 22
    LC_ALL=
    PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/local/games:/usr/games:/home/pi/scrpt
    DBUS_SESSION_BUS_ADDRESS=unix:path=/run/user/1000/bus
    MAIL=/var/mail/pi
    SSH_TTY=/dev/pts/1
    OLDPWD=/home/pi/Desktop/study                           :上一个工作目录
    TEXTDOMAIN=Linux-PAM  
  ```

-   set :观察所有变量  

    几个重要的变量
    -   PS1 : 命令符变量, 有下面一些符号
        [命令符变量的符号](../laungage/shell)
    -   \$  :本shell的PID
    -   ?   :上一个指令的回传值
    -   OSTYPE, HOSTTYPE, MACHTYPR  : 主机硬件和核心等级
-   export  :自定变量成为环境变量, 当只有export时会列出当前所有的环境变量
### 影响显示结果的语系变量
-   locale
  ```shell
    locale -a   查询当前linux支持的编码语言
    locale      显示语系相关的环境变量
    下面是本机locale之后的结果:
    LANG=zh_CN.UTF-8            :主语言环境
    LANGUAGE=zh_CN.UTF-8        
    LC_CTYPE="zh_CN.UTF-8"      :字符辨识编码
    LC_NUMERIC="zh_CN.UTF-8"    :数字讯息显示编码
    LC_TIME="zh_CN.UTF-8"       :时间系统显示数据
    LC_COLLATE="zh_CN.UTF-8"    :字符比较和排序
    LC_MONETARY="zh_CN.UTF-8"
    LC_MESSAGES=zh_CN.UTF-8     :讯息显示内容
    LC_PAPER="zh_CN.UTF-8"
    LC_NAME="zh_CN.UTF-8"
    LC_ADDRESS="zh_CN.UTF-8"
    LC_TELEPHONE="zh_CN.UTF-8"
    LC_MEASUREMENT="zh_CN.UTF-8"
    LC_IDENTIFICATION="zh_CN.UTF-8"
    LC_ALL=                     :整体语系环境  
  ```

### 变量的键盘读取, 阵列与宣告
-   read    读取来自键盘的输入
  ```shell
    read [-pt] variable
    选项和参数:
    -p : 后面接提示字符
    -t : 表示等待的时间  
  ```

-   declare/typeset     宣告变量类型(两个用法没有什么不同)
  ```shell
    declare [-aixr] variable
    选项和参数:
    -a : 将后面变量定义为阵列(array)类型
    -i : 将后面变量定义为整数类型(interger)
    -x : 用法和export一样, 将后面的变量变成环境变量
    -r : 将变量设置为redonly类型, 该变量不可被更改, 也不能unset  
  ```

    变量类型默认是字串, 数值运算默认最多达到整数形态
    -   阵列(array)变量类型

        设置方式
        ```shell
        var[index]=content        
        ```
### 与文件系统及程序的限制关系:ulimit
-   ulimit  设置用户的配额
  ```shell
    ulimit [-SHacdfltu] [配额]
    选项和参数:
    -H:hard limit, 严格的警告, 完全不能超过这个数值
    -S:soft limit, 警告的设置, 超过这个值会有警告
    -a:后面不接任何选项和参数, 可列出所有的限制额度
    -c:限制每个核心文件的最大容量
    -f:此shell可以创建的最大的文件大小, 单位是kb
    -d:程序可使用的最大断裂内存容量
    -l:可用于锁定的内存量
    -t:可使用的最大cpu
    -u:单一使用者可以使用的最大程序数量  
  ```

### 变量内容的删除, 取代和替换
-   删除变量的内容
  ```shell
    ${variable#/#local/bin:}    //$是关键字, 必须存在, variable是操作的变量, #表示从前面开始查找并删除, 后面是字符  
  ```
    -      表示不贪心
    -   #  表示贪心
    -   %   从最后面开始删除, 不贪心
    -   %%  从最后面开始删除, 贪心
-   替代
  ```shell
    ${variable/oldname/newname}     表示最开始的旧字符变成新字符
    ${variable//oldname/newname}     表示所有的的旧字符变成新字符  
  ```

-   测试和内容替换
  ```shell
    new_var=${old_var-content}      用新变量取代旧字符, 如果旧变量不存在就赋值content
    new_var=${old_var:content}      用新变量取代旧字符, 如果旧变量不存在或为空就赋值content  
  ```
  
  下面是一个很复杂的表格

  | 变量设置方式      | str没有设置       | str是空           | str以设置为非空   |
  |-------------------|-------------------|-------------------|-----------------|
  | var=\${str-expr}  | var=expr          | var=              | var=\$str         |
  | var=\${str:-expr} | var=expr          | var=expr          | var=\$str         |
  | var=\${str+expr}  | var=              | var=expr          | var=expr          |
  | var=\${str:+expr} | var=              | str不变 var=      | var=expr          |
  | var=\${str=expr}  | str=expr var=expr | var=              | str不变 var=\$str |
  | var=\${str:=expr} | str=expr var=expr | str不变 var=\$str |                   |
  | var=\${str?expr}  | expr输出至stderr  | var=              | var=\$str         |
  | var=\${str:?expr} | expr输出至stderr  | var=\$str         |                   |

## 命名别名与历史命令

### 命名别名设置
-   alias
  ```shell
    alias 别名='命令'   设置别名
    unalias 别名        拿掉别名  
  ```

### 历史命令:history
-   history
  ```shell
    history [n] [-c] [-raw histfiles]
    选项和参数:
    n : 数字, 列出距离现在最近的n个命令
    -c : 将目前shell的history全部删除
    -a : 将新增的history写入histfiles中, 如果没有加参数, 默认写入到~/.bath_history
    -r : 将histfiles的内容读入到本shell的history中
    -w : 将目前的history写入到histfiles中  
  ```
-   执行命令
  ```shell
    !number     执行第几个命令
    !command    由最近的指令向前搜索执行command开头的指令
    !!          执行上一个指令  
  ```
## Bash Shell的操作环境
### 路径和指令的搜寻顺序
1.  以相对, 绝对路径执行命令
2.  有alias找到该指令执行
3.  由bash内置指令执行
4.  由PATH变量搜寻到的第一个指令执行

### 进站与欢迎讯息
[详细见此处](../shell.md)

### 环境配置
[详细见此处](../shell.md)

### 终端机环境设置
-   stty 查看shell里面默认字符设置功能
  ```shell
    stty [-a]   将目前所有的stty参数列出来  
  ```

    几个重要的代表意义
    | 字符  | 意义                    |
    |-------+-------------------------|
    | intr  | 终端                    |
    | quit  | 给一个退出讯号          |
    | erase | 向后删除字符            |
    | kill  | 删除目前命令行所有文字  |
    | eof   | 结束输入                |
    | start | 某个程序停止后重新启动  |
    | stop  | 停止目前屏幕输出        |
    | susp  | 给一个terminal stop讯号 |

-   set 设置终端机设置值
  ```shell
    set [-uvCHhmBx]
    选项和参数:
    -u:默认不启用, 当启用后, 在使用未设置变量会显示错误信息
    -v:默认不启用, 当启用后当讯息被输出前显示讯息原始内容
    -x:默认不启用, 当启用后在指令执行前, 显示指令内容
    -h:默认启用, 和历史命令有关
    -H:默认启用, 和历史命令有关
    -m:默认启用, 与工作管理有关
    -B:默认启用, 与[]有关
    -C:默认不启用   
  ```

-   万用符号    可以在bash中用
    | 符号  | 意义                           |
    |-------|--------------------------------|
    | #     | 表示0到多个任意字符            |
    | ?     | 一定有一个任意字符             |
    | []    | 一定有一个在括号内的字符       |
    | [ - ] | 一定有一个编码顺序内的任意字符 |
    | [^]   | 取非                           |

## 数据流重导向
[详细见此处](../shell.md)
## 管线命令               
### 撰取命令:cut, grep
- cut
  ```shell
  cut fields
  选项和参数:
  -d: 后面接分割字符
  -f: 后面接取出第几段
  -c: 以后面的字符为单位取出固定字符区间
  ```
- grep
  ```shell
  grep [-acinv] [--color=auto] '搜寻字串' filename
  选项和参数:
  -a : 将binary文件以text的方式搜寻数据
  -c : 计算找到'搜寻字串'的次数
  -i : 忽略大小写
  -n : 输出行号
  -v : 反向选择
  --color : 关键字添加颜色
  ```
### 排序命令:sort, wc, uniq
- sort
  ```shell
  sort [-fbMnrtuk] [file or stdin]
  选项和参数:
  -f : 忽略大小写差异
  -b : 忽略最前面的空白字符
  -M : 用月份名字排序
  -n : 用纯数字排序
  -r : 反向排序
  -u : 相同的数据中仅出现一行代表
  -t : 分割符号,默认采用[tab]分割
  -k : 以这个区间来排序
  ```
- uniq:重复的数据仅仅显示一次
  ```shell
  uniq [-ic]
  选项和参数:
  -i : 忽略大小写的不同
  -c : 进行记数
  ```
- wc:计算输出讯息的整体数据
  ```shell
  wc [-lwm]
  选项和参数:
  -l : 仅列出行
  -w : 仅列出多少字
  -m : 多少字符
  ```
### 双向重导向:tee
tee会同时将数据流分送到文件和屏幕上
```shell
tee [-a] file
选项和参数
-a : 以追加的方式将数据加入file
```
### 字符转换命令:tr, col, join, paste, expand
- tr:用来删除一段讯息中的文字或进行替换
  ```shell
  tr [-ds] SET1 [SET2]
  选项和参数:
  -d : 删除讯息中的SET1
  -s : 取代掉重复的字符
  ```
- col:将tab转换为空白键
  ```shell
  col [-xb]
  选项和参数:
  -x : 将tab转换为对应的空白键
  ```
- join:将两个相同的数据结合为一个
  ```shell
  join [-ti12] file1 file2
  选项和参数:
  -t : 分割符,默认是空白字符
  -i : 忽略大小写
  -1 : 代表'第一个字段要用那个字段来分析'
  -2 : 代表'第二个字段要用那个字段来分析'
  ```
- paste:将两行粘到一起,中间用tab隔开
  ```shell
  paste [-d] file1 file2
  选项和参数:
  -d : 后面接分割字符,默认是tab
  -  : file处如果是-,表示来自之前输出的数据
  ```
- expand: 将tab转换为空格
  ```shell
  expand [-t] file
  选项和参数:
  -t : 设置一个tab是多少字符
  ```
### 分区命令:split
将一个大文件通过文件大小或行数进行分区
```shell
split [-bl] file PREFIX
选项和参数:
-b : 后面可接欲分区成的大小,单位b, k, m
-l : 行数来进行分区
```
### 参数代换:xargs
产生某个指令的参数
```shell
xargs [-0epn] command
选项和参数:
-0 : 可以将特殊字符还原为一般字符
-e : 后面接一个字串,分析到该字串自动停止工作
-p : 执行每个指令的argument之前,询问使用者
-n : 后面接次数,每次command执行时要用几个参数
```
### 关于减号的用途
减号可以替代前一个指令的stdout
