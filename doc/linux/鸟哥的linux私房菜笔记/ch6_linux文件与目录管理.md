# 第六章, linux文件与目录管理

## 目录与路径

-   一些特殊的目录
    ```shell
    .   此目录
    ..  上一层目录
    -   前一个工作目录
    ~   目前使用者身份所在的主文件夹
    ~account    account使用者的主文件夹    
    ```

-   一些目录的命令  
    ```shell
    cd  跳转
    pwd 打印当前所在目录
    mkdir -p    递回创建目录
    rmdir -p    删除空目录
    ```

## 文件与目录管理

### 取得路径的文件名与目录名称
```shell
basename    取得最后的文件名或目录名
dirname     取得目录名
```

## 文件内容查阅
1.  直接检视文件内容

  -   cat
    ```
        cat [-AbEnTv]
        选项:
        -A:列出特殊字符
        -b:列出非空白行的行号
        -E:将结尾换行符显示
        -n:列出所有行行号
        -T:将tab显示
        -v:列出看不见的特殊字符
    ```
  -   tac
        反向显示
  -   nl:添加行号打印
  -   more:一页一页翻动  
        -   空白键:向下翻一页
        -   Enter:向下翻一行
        -   /str:搜索
        -   :f显示文件名和当前行数
        -   q:离开
        -   b:往回翻
  -   less:一页一页翻动
2.  数据获取

    -   head:取出前面几行
      ```
        head [-n number] 文件
        显示前number行, 默认10行
      ```
    -   tail:取出后面几行
      ```
        tail [-n number] 文件
      ```
3.  非纯文本文件
    -   od
      ```
        od [-t TYPE] 文件
        TYPE:
        a:默认字符输出
        c:ascll输出
        d[size]:十进制输出
        f[size]:浮点数输出
        o[size]:八进制输出
        x[size]:十六进制输出      
      ```

## 文件和目录的默认权限和隐藏权限
-   文件默认权限:umask  

    umask指的是默认剪掉的权限, 后三个数字是user, group, others  

    如0022, 指的就是rwxr-xr-x  

    也可以加-S选项看详细的值  

    如果要设置umask, 直接在后面输入三位数字就好

    ```shell
    umask 002
    ```
-   文件隐藏属性
    -   chattr(设置文件隐藏属性)
      ```shell
        chattr [+-=][ASacdistu] 文件或目录名
        选项和参数:
        +:增加某个特殊参数
        -:移除某个特殊参数
        =:设置一定且仅有后面接的参数

        A:当有存取此文件或目录时, 存取时间atime不会被修改
        S:当进行文件修改时, 会同步写到硬盘中
        a:只能增加数据, 不能删除或修改数据
        c:自动将文件压缩, 当读取时再解压缩
        d:当dump程序执行时, 不会被备份
        i:让一个文件不能被删除, 改名, 设置链接, 不能写入和新增数据
        s:如果被删除, 会被永久移除硬盘
        u:如果被删除, 数据内容还在硬盘      
      ```
    -   lsattr(显示文件隐藏属性)
      ```shell
        lsattr [-adR] 文件或目录
        选项:
        -a:将隐藏文件的属性也列出
        -d:列出目录本身而非下属文件的信息
        -R:连同子目录的数据也一并列出      
      ```
## 观察文件类型:file
   ```
file 文件   //可以告诉这个文件的类型   
   ```
## 指令与文件的搜寻

-   指令文件名的搜寻
    -   which(寻找"可执行文件")
      ```shell
        which [-a] command
        选项:
        -a:将所有再PATH中可以找到的指令列出, 而不是第一个      
      ```
        内置函数没有办法被找到
-   文件文件名的搜寻
    -   whereis
      ```shell
        whereis [-bmsu] 文件或目录名
        选项:
        -l:可以列出whereis会去查询的几个主要目录
        -b:只找binary格式的文件
        -m:只能在说明文档manual路径下的文件
        -s:只找到source来源文件
        -u:搜寻不在上述三个项目当中的其他特殊文件      
      ```
    -   locate/updatedb
      ```
        locate [-ir] keyword
        选项:
        -i:忽略大小写的差异
        -c:不输出文件名, 仅输出找到的文件数量
        -l:仅输出n行
        -S:输出locate所使用的数据库文件的相关信息, 包括数据库记录的文件/目录数目等
        -r:后面可以接正则表达式的显示方式      
      ```
        在数据库中寻找文件, 数据库可能一段时间更新一次, 可以手动更新数据库
        ```shell
        updatedb
        ```

    -   find
      ```
        find [PATH] [option] [action]  
        选项和参数:
        1, 和时间有关的选项:
        -mtime n:n天之前的一天之内被修改过的文件
        -mtime +n:n天的之前被修改过的文件
        -mtime -n:n天之内被修改过的文件
        -newer file:file是一个已经存在的文件, 列出比file新的文件

        2,与使用者和群组名称有关的参数
        -uid n:数字是使用者的ID
        -gid n:群组名称的id
        -user name:使用者账号的名称
        -group name:群组名称
        -nouser:寻找文件的所有者不存在于/etc/passwd的人
        -nogroup:寻找文件的所有者不存在于/etx/group的人

        3, 与文件权限和名称有关的参数
        -name filename:搜寻文件名为filename的文件
        -size [+-]SIZE:搜寻比SIZE大[+]或小[-]的文件
        -type TYPE:搜索文件类型是TYPE的文件
        -perm mode:搜索文件权限刚好等于mode的文件
        -perm -mode:搜索文件权限囊括mode的文件
        -perm /mode:搜索文件权限包含任一mode的权限的文件

        4, 额外可进行的动作
        -exec command:-exec后接其他指令处理搜寻到的结果
        -print:将结果打印到屏幕上      
      ```
