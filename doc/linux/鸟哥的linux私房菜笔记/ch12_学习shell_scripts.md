# 第十二章, 学习shell scripts
## 什么是shell scripts
   针对shell写的剧本,将一些shell的语法和指令写在里面
### 干嘛学习shell scripts
  - 自动化管理的重要依据
  - 追踪和管理系统的重要工作
  - 简单的入侵探测功能
  - 连续指令单一化
  - 简易的数据处理
  - script处理时速度较慢,调用CPU资源过多,大量运算时不很适用
### 第一支script文件的撰写与执行
  - 有下列注意事项
    1. 指令的执行是从上到下,从左到右
    2. 指令,选项和参数之间的多个空白会被忽略
    3. 空白行被忽略
    4. 读取到回车开始执行命令
    5. #是注释
  - script撰写规范
    1. 开头写#!/bin/bash宣告使用script的shell名称
    2. 程序内容要在注释中说明,包括
       1. 内容和功能
       2. 版本信息
       3. 作者和联系方式
       4. 创建日期
       5. 历史记录
       ```shell
       # Program:
       #      This program shows "Hello World" in the screen
       # History
       # 2015/07/16 VBird   First release
       ```
    3. 主要环境变量宣告:将一些重要的环境变量设置好,如PATH,LANG
    4. 主要程序部分
    5. 执行成果告知, 定义回传值,一般在最后exit 0
## 简单的shell script练习
### script执行方式的差异
 - 利用直接执行的方式执行script
   - 相当于另外开一个子buffer去执行程序,所有的结果不会返回到父buffer
 - 利用source执行指令
   - 直接在当前的buffer中执行脚本,所有的设置还是会生效
## 擅用判断式
### 利用test指令测试,有以下这些测试选项
  有一个很常用的手段
  ```shell
  test -e /dmtsai && echo "exist" ; echo "not exist"
  ```
  | 测试标志                                       | 代表意义                           |
  |----|----|
  | 文件类判断,test -e filename                    |                                    |
  | -e                                             | 该文件名是否存在                   |
  | -f                                             | 该文件名是否存在且为文件           |
  | -d                                             | 该文件是否存在且为目录             |
  | -b                                             | 该文件是否存在且为block device     |
  | -c                                             | 该文件是否存在且为character device |
  | -S                                             | 该文件名是否存在且为一个Socket文件 |
  | -p                                             | 该文件是否存在且为FIFO文件         |
  | -L                                             | 该文件是否存在且为链接文件         |
  | 文件的权限侦测                                 |                                    |
  | -r                                             | 文件是否有可读                     |
  | -w                                             | 文件是否有可写                     |
  | -x                                             | 文件是否可执行                     |
  | -u                                             | 文件是否有SUID属性                 |
  | -g                                             | 文件是否有SGID的属性               |
  | -k                                             | 文件是否有Sticky bit属性           |
  | -s                                             | 文件是否是非空白                   |
  | 两个文件的比较, test file1 -nt file2           |                                    |
  | -nt                                            | 1比2新                             |
  | -ot                                            | 1比2旧                             |
  | -ef                                            | 1和2是不是同一个文件               |
  | 关于两个整数的判定,如test n1 -eq n2            |                                    |
  | -eq                                            | 相等                               |
  | -ne                                            | 不等                               |
  | -gt                                            | 1大于2                             |
  | -lt                                            | 1小于2                             |
  | -ge                                            | 1大于等于2                         |
  | -le                                            | 1小于等于2                         |
  | 判断字串的数据                                 |                                    |
  | test -z string                                 | 字串是否为0或为0                   |
  | test -n string                                 | 字串是否非0或有东西                |
  | test str1==str2                                | 1等于2                             |
  | test str1!=str2                                | 1不等于2                           |
  | 多重条件判定,如test -r filename -a -x filename |                                    |
  | -a                                             | 两个条件同时成立                   |
  | -o                                             | 或                                 |
  | \!                                             | 取反                               |
### 利用判断符号[]
  - 中括号里面的内容可以表示判断,有以下这些需要注意
    - 中括号内部的每个元件都要有空白键分割
    - 中括号内部的变量用双引号括起来
    - 中括号内部的常数用单引号括起来
### shell script的默认变量
  ```shell
  /path/to/scriptname  opt1  opt2  opt3  opt4
  $0                    $1    $2    $3    $4
  ```
  - $# : 代表后面接的参数的个数
  - $@ : 代表"$1""$2""$3""$4"每个变量独立
  - $# : 代表"$1<u>c</u>$2<u>c</u>$3<u>c</u>$4",<u>c</u>是分割符,默认是空白
  - shift : 后面跟数字, 造成参数变量号码偏移相当于直接移动数字,将前面的若干个参数去掉
## 条件判断式
### 利用if...then
  ```shell
  if [ ]; then
  # 成立时执行
  fi

  # if后面可以跟着很多的条件表达式,中间用 && 或 || 隔开
  if []; then
  else
  fi

  if []; then
  elif []; then
  else
  fi
  ```
### 利用case ... esac判断
  ```shell
  case $变量名称 in
    "第一个变量内容")
      程序段
      ;;
    "第二个")
      程序段
      ;;
    #)
      其他的程序段
      ;;
  esac
  ```
### 利用function功能
  ```shell
  function fname() {
      程序段
  }
  ```
  - function一定要在调用的前面
## 循环(loop)
### while do done, until do done(不定循环)
  ```shell
  while [ condition ] 
  do
      程序段
  done
  # 当condition成立执行
  until [ condition ]
  do
      程序段
  done
  # 当condition不成立时执行
  ```
### for...do...done(固定循环)
  ```shell
  for var in con1 con2 con3
  do
      程序段
  done
  ```
  - 上述程序意思是第一次循环, var的值是con1, 第二次是con2等等
### for...do...done的数值处理
  ```shell
  for (( 初始值; 限制值 ;执行步阶 ))
  do
      程序段
  done
  ```
### 搭配乱数与阵列的实验
## shell script的追踪和debug
  ```shell
  sh [-nvx] scripts.sh
  选项和参数:
  -n : 不执行script
  -v : 在执行script之前先将script的内容输出到屏幕上
  -x : 将使用到的script显示到屏幕上
  ```