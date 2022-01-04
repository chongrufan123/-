# linux


<!-- vim-markdown-toc Marked -->

- [linux](#linux)
  - [命令](#命令)
    - [vim](#vim)
    - [软件包管理](#软件包管理)

<!-- vim-markdown-toc -->
## 命令

- 文件管理命令
    - ls（list）
        ```
        功能：显示目录文件
        选项： -a(all)	查看所有文件	-l(long)	显示详细信息	-h	人性化显示	-d	查看目录详细信息
        rw-			r--			r--
        u 所有者	g 所属组	o其他人
        r读	w写	x执行
        ```
    - mkdir（make directories）
        ```
        功能：创建目录
        选项：-p	递归创建
        ```
    - cd（change directory）
        ```
        功能：切换目录
        ```
    - pwd
        ```
        功能：显示当前路径
        ```
    - rmdir（remove empty directories）
        ```
        功能：删除空目录
        ```
    - cp（copy）
        ```
        功能：复制文件
        选项：-r 复制目录	-p	保持文件属性
        ```
    - mv（move）
        ```
        功能：剪切/改名
        ```
    - rm（remove）
        ```
        功能：删除文件
        选项：-r删除目录	-f强制执行
        ```
    - touch
        ```
        功能：创建文件
        ```
    - cat
        ```
        功能：显示文件内容
        选项：-n显示行号
        ```
    - tac
        ```
        功能：反向显示
        ```
    - more
        ```
        功能：分页显示文件内容
        空格或f 翻页	enter 换行	q 退出
        ```
    - less
        ```
        功能：分页显示文件内容（可以向上翻，可以查找关键词（加一个/））
        ```
    - head
        ```
        功能：指定显示行数
        选项：-n 指定行数
        ```
    - tail
        ```
        功能：反向指定显示行数
        选项：-n 指定行数   -f 动态显示文件末尾内容
        ```
    - ln（link）
        ```
        功能：生成链接文件
        语法：ln -s 源文件 目标文件 生成软链接
        ln 源文件 目标文件 生成硬链接
        ```
- 权限管理
    - chmod(change the permissions mode of a file)
        ```
        功能：改变文件和目录的权限
        选项：-R 改变该目录下所有子目录的权限
        ```
    - chown(change file ownership)
        ```
        功能：改变文件和目录的所有者
        语法：chown 用户 文件或目录
        只有管理员可以做，前提是存在这个用户
        文件所属组就是创建者的缺省组
        ```

    - umask(the user file-creation mask)
        ```
        功能：显示、设置文件的缺省权限
        选项：-S 以rwx形式显示新建文件缺省权限
        默认缺省执行文件没有执行权限
        ```
- 文件搜索命令
    - find
        功能：搜索文件
        find 搜索范围 匹配条件
        - 选项
            find -name 按照全部名字查找
            -iname    名字查找不区分大小写
            *匹配任意字符*
            ？匹配单个字符
            -size    根据文件大小查找
            +大于多少
            -小于多少
            -user
            -group
            -amin   访问时间查找
            -cmin   属性更改      
            -mmin  内容更改
            -type 根据类型查找
                f 文件   
                d 目录   
                l 软连接
            -inum   根据i节点查找
            -a and         
            -o  or
            -exec/-ok {} \;在搜索之后进行操作
    - locate
        ```
        功能：在文件库中查找文件
        ```
    - updatedb
        ```
        功能：更新文件资源库
        ```
    - which
        ```
        功能：查找命令的路径
        ```
    - whereis
        ```
        功能：查找命令的路径和帮助文档的路径
        ```
    - grep
        ```
        功能：查找文件里面的指定字符串
        选项：-i 不区分大小写
              -v 排除查找
        示例：grep -v ^# 文件路径        查看除了注释之外的文件
        ```
- 帮助命令
    - man（manual）
        ```
        功能：查看命令和配置文件的帮助信息
        man 命令
        1  命令的帮助     
        5  配置文件的帮助
        ```
    - whatis
        ```
        简短的帮助信息
        ```
    - —help
        ```
        命令+—help  查看命令的选项信息
        ```
    - help
        ```
        功能：查看shell内置命令的帮助信息
        ```
- 用户管理命令
    - useradd
        ```
        功能：添加新用户名
        语法：useradd + 名字
        ```
    - passwd
        ```
        功能：给用户设置密码
        语法：passwd + 名字
        ```
    - who
        ```
        功能：查看现在登录的用户
        登录用户名       登录终端      tts本地终端     pts远程终端      登录时间    IP地址
        ```
    - w
        ```
        功能：查看详细的信息
        ```
- 网络命令
    - write
        ```
        功能：给指定用户发消息，以CTRL+D保存结束
        ```
    - wall(write all)
        ```
        功能：给所有人发信息
        wall 信息
        ```
    - ping
        ```
        功能：测试网络是否通畅
        选项：-c 数字 选择ping几次
        ```
    - ifconfig（interface configure）
        ```
        功能：查看和设置网卡信息
        后面直接加类型和ip地址就可以改变该类型的ip地址
        ```
    - mail
        ```
        功能：查看发送电子邮箱
        ```
    - last
        ```
        功能：查询服务器目前和过去的登录信息
        ```
    - lastlog
        ```
        功能：查看所有用户和最后一次登录信息
        选项：-u id信息   只查看这个人的最后一次登录信息
        ```
    - traceroute
        ```
        功能：显示数据包到主机间的路径
        ```
    - netstat
        ```
        功能：显示网络相关信息
        选项：-t TCP协议   
              -u UDP协议    
              -l 监听   
              -r 路由   
              -n 显示IP地址和端口号
        用法：netstat -tlun  查看本机监听的端口    
             netstat -an    查看本机所有的网络连接
             netstat -rn    查看本机路由表
        ```
    - setup
        ```
        功能：设置网络
        ```
    - mount
        ```
        功能：挂载
        mount 设备文件名 挂载点
        ```
- 关机重启命令
    - shutdown
        ```
        功能：关机重启
        选项： -c 取消前一个关机命令   
               -h 关机   
               -r 重启
        语法：shutdown 选项 时间
        ```
        ![系统运行级别](linux%207431be0da77e4c9e9b605705fd6857fd/Untitled.png)
    - runlevel
        ```
        功能：查询当前运行级别
        ```
    - logout
        ```
        功能：退出登录命令
        ```
### vim

命令模式——>输入i a o ——>插入模式——>Esc——>命令模式
命令模式——>输入：——>编辑模式

- 命令
    [定位命令](https://www.notion.so/2799a7245ad9474fa944026043d74bf4)

- 其他命令

    map 快捷键 命令  设置快捷键
    ab mymail chongrufan@nuaa.edu.cn    定义快捷键
    快捷键写到用户根目录的配置文件里面  /home/fan/.vimrc

---

### 软件包管理

- 软件包分类

    源码包
    二进制包（RPM包，系统默认包）
