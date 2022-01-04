# 第七章, linux磁盘与文件系统管理
## 认识linux文件系统
### 磁盘组成和分区
- 磁盘组成
  - 圆形的盘片(记录数据)
  - 机械手臂, 和在机械手臂上的磁头(读写盘片)
  - 主轴马达, 可以转动盘片, 让机械手臂读写数据

- 盘片的物理组成
  - 扇区, 最小的物理储存单位, 目前主要有521Bytes和4K两个格式
  - 柱面, 扇区组成一个圆
  - 扇区作为最小的分区单位
  - 磁盘分区的格式
    - MBR分区:第一个扇区最重要, 限制比较多
    - GPT分区:较新, 限制较少, 分区数量扩充较多
  - /dev/sd[a-p][1-128] 实体磁盘的磁盘文件名
  - /dev/vd[a-d][1-128] 虚拟磁盘的磁盘文件名
  - 索引式文件系统(indexed allocation)   

        一个文件系统的一些属性会存放在不同的区块
    - superblock:记录整体信息, 包括inode/block的总量, 使用量, 剩余量以及文件系统格式与相关信息等
    - inode:记录文件的属性, 一个文件占用一个inode, 同时记录此文件的数据所在的block的号码
    - block:实际记录文件内容, 太大会占据多个block  
    文件找到他的inode, 然后就可以找到他的所有的block, 就可以都读取出来

  - FAT格式

        每个block号码记录在前一个block中, 然后依次读取, 类似于链条

- inode table  

  - inode table记录的文件数据有以下这些
    -   文件的存取模式(read/write/excute)
    -   该文件的拥有者与群组(owner/group)
    -   该文件的容量
    -   改文件创建或状态改变的时间(ctime)
    -   最近一次读取时间(atime)
    -   最近修改的时间(mtime)
    -   定义文件特性的旗帜(flag)
    -   该文件真正的指向(pointer)  
  - inode的特点有这些
    -   每个inode大小固定是128Bytes
    -   每个文件仅仅占用一个inode
    -   文件系统能够创建的文件数量和inode有关
    -   读取文件要先找到inode
- superblock  

  - 记录整个filesystem相关信息的地方, 记录的信息有
    -   block和inode的总量
    -   未使用与已使用的inode/block数量
    -   block和inode的大小(block:1, 2, 4k, inode:128Bytes或256Bytes)
    -   filesystem的挂载时间, 最近一次写入数据的时间, 最近一次检验硬盘的时间等
    -   一个valid bit数值, 若文件挂载, 则valid bit为0, 否则为1
      ```shell
    dumpe2fs [-bh] 设备文件名
    选项和参数:
    -b: 列出保留为坏轨的部分
    -h: 仅列出superblock的数据, 不会列出其他区段内容

    列出来的信息:
    Filesystem volume name: //文件系统的名称
    Last monted on:         //上一次挂载的目录位置
    Filesystem UUID:        //linux对设备的定义码
    Filesystem features     //文件系统的特征数据
    Defaule mount options   //默认挂载时主动加上挂载参数
    Filesystem state:       //文件系统的状态
    Inode count:            //inode的总数
    Block count:            //block的总数
    Reserved block count:   //保留的block总数
    Free block              //剩余的block数量
    Free inode              //inode可用数量
    Block size              //单个Block容量大小
    Inode size              //Inode的容量大小
    Journal size            //日志式数据可供记录的总容量
    Group0:                 //第一个group group的位置
    Primary .               //主要superblock的所在
    Inode table at          //inode table所在
    free blocks             //剩余的容量      
      ```

### linux文件系统的运行
linux使用非同步处理(asynchronously), 即当系统载入一个文件到内存后, 如果文件没有变动, 则内存区段文件数据被认为是clean,
否则被认为是Dirty的, 系统会不时的将Dirty的数据写入磁盘

### 挂载点的意义(mount point)
每一个filesystem都有自己独立的inode/block/superblock, 并且他要链接到目录树才能被我们使用,
将文件系统和目录数的结合被称为挂载

### XFS文件系统简介
默认的文件系统由EXT4变为XFS, EXT家族虽然支持度最广, 但是格式化非常慢

- XFS文件系统的配置  

  - 是一个日志式文件系统, 有以下三个规划的部分
    - 数据区
    - 文件系统活动登录区
    - 实时运行区

## 文件系统的简单操作
### 磁盘和目录的容量
-   df  

    列出文件系统的整体磁盘使用量
    ```shell
    df [-ahikHTm] [目录或文件名]
    选项和参数:
    -a:列出所有的文件系统
    -k:以KB显示各文件系统
    -m:以MB显示文件系统
    -h:自行决定格式显示
    -H:以M=1000K来代替M=1024K
    -T:连同partition的filesystem也列出
    -i:不用磁盘容量, 用inode数量来显示
    ```

-   du  
    评估文件系统的磁盘使用量(常用在推估目录所占容量)
    ```shell
    du [-ahskm] 文件或目录名称
    选项和参数:
    -a:列出所有文件和目录容量
    -h:自由决定size单位
    -s:列出总量, 不必列出各个类别的占用量
    -S:不包括子目录下的总计
    -k:单位KB
    -m:单位MB    
    ```
### 实体链接与符号链接
两种链接
-   Hard Link(硬链接)  

    将某个文件硬链接到另一个文件, 他们的文件名可以不同, 且不占额外的block, 当其中一个文件的内容改变,
    硬链接的另一个内容跟着改变, 当其中一个文件删除, 另一个不会有改变
-   Symbolic Link(符号链接)  

    创建一个指向目标文件inode的inode, 基本不占block, 当实际的文件删除, 创建的符号链接也会不可以使用
-   ln
  ```shell
    ln [-sf] 来源文件 目标文件
    选项和参数:
    -s:默认硬链接, 加上-s是符号链接
    -f:强制执行  
  ```
## 磁盘的分区, 格式化, 检验与挂载
### 观察磁盘分区状态
-   lsblk(lisk block device)  

    列出系统上的所有的磁盘列表
    ```shell
    lsblk [-dfimpt] [device]
    选项与参数:
    -d:仅列出磁盘本身, 并不会列出磁盘的分区数据
    -f:同时列出该磁盘内的文件系统的名称
    -i:使用ascii编码输出
    -m:同时输出该设备在/dev下面的权限数据
    -p:列出该设备的完整文件名, 默认只列出最后的名字
    -t:列出该磁盘设备的详细数据, 包括磁盘伫列机制, 预读写的数据量大小
    其中列出的数据:
    MAJ:MIN 主要:次要设备代码
    RM:     是否是可卸载设备
    RO      是否是只读设备
    TYPE    是磁盘(disk), 分区(partition)还是只读存储器(ROM)    
    ```

-   blkid  
    找出设备的UUID(全域单一识别码, 所有设备独一无二)
    ```shell
    blkid    
    ```

-   parted  
    列出磁盘的分区表类型与分区信息
    ```shell
    parted device_name print
    得到:
    model   //磁盘的模块名称
    Disk    //磁盘的总容量
    Sector size     //磁盘的每个逻辑/物理扇区容量
    Partition       //分区表格式    
    ```
### 磁盘分区
-   gdisk  

    GPT分区方法
    ```shell
    gdisk 设备名称    
    ```

-   fdisk  

    MBR分区方法
    ```
    fdisk 设备名称    
    ```

## 设置开机挂载
挂载的一些限制:
-   根目录必须挂载, 且要先于其他的mount point
-   其他mount point必须为已创建的目录
-   所有的mount point在同一时间内只能挂载一次
-   所有的partition在同一时间内只能挂载一次
-   如要卸载, 要先将工作目录转移到mount point之外

## 内存交换空间(swap)之创建

## 文件系统的特殊观察与操作
