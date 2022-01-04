// git的一些基本操作
# git
[参考链接](https://mp.weixin.qq.com/s/F9cwVga7r5Z0cuzKht-Emw)


<!-- vim-markdown-toc Marked -->

- [git](#git)
  - [基础](#基础)
    - [常用操作](#常用操作)
    - [git clone](#git-clone)
    - [git config](#git-config)
    - [git branch](#git-branch)
    - [git checkout](#git-checkout)
    - [git status](#git-status)
    - [git add](#git-add)
    - [git commit](#git-commit)
    - [git push](#git-push)
    - [git pull](#git-pull)
    - [git log](#git-log)
    - [git tag](#git-tag)
    - [.gitignore](#gitignore)
  - [进阶](#进阶)
    - [git add](#git-add-1)
    - [git commit](#git-commit-1)
    - [git mv](#git-mv)
    - [git rm](#git-rm)
    - [git status](#git-status-1)
  - [操作分支](#操作分支)
    - [git branch](#git-branch-1)
    - [git merge](#git-merge)
    - [git checkout](#git-checkout-1)
    - [git stash](#git-stash)
  - [操作历史](#操作历史)
    - [git log](#git-log-1)
  - [操作历史](#操作历史-1)
    - [git log](#git-log-2)
    - [git cherry-pick](#git-cherry-pick)
    - [git reset](#git-reset)
    - [git revert](#git-revert)
    - [git diff](#git-diff)
    - [git reflog](#git-reflog)
  - [远程版本库连接](#远程版本库连接)
    - [git init](#git-init)
    - [git remote](#git-remote)
    - [git fetch](#git-fetch)
  - [问题排查](#问题排查)
    - [git blame](#git-blame)
  - [更多操作](#更多操作)
  - [备注](#备注)

<!-- vim-markdown-toc -->

## 基础

### 常用操作
- git clone
- git config
- git branch
- git checkout
- git status
- git add
- git commit
- git push
- git pull
- git log
- git tag

### git clone
下载代码

### git config
配置开发者用户的用户名和邮箱
```
git config user.name ****
git config user.email ****
```

### git branch
创建,重命名,查看,删除项目分支
```
git branch daily    //创建一个daily的分支
git branch -m oldname newname   //重命名分支名
git branch  //查看当前分支列表
git branch -d daily     //删除daily的分支
```

### git checkout
切换分支
```
git checkout daily  //切换到daily分支
```

### git status
查看文件的状态

### git add
```
git add README.md   //添加README.md文件
git add .   //添加所有更新的文件
```

### git commit
提交到版本库
```
git commit -m "更新内容"
```

### git push
将本地代码改动推送到服务器
```
git push origin daily   //origin指的是当前服务器地址,daily是分支
```

### git pull
服务器上的代码拉取到本地
```
git pull origin daily   //将daily分支拉取到本地
```

### git log
查看版本提交记录

### git tag
为项目标记里程碑
```
git tag publish //添加一个publish的标签
```

### .gitignore
一个配置文件,设置哪些内容不要推送到服务器
```
demo.py
huild/
```
上述配置文件里的内容指的是忽略demo.py和build

## 进阶
### git add
```
git add -i  //查看交互式子命令系统
得到
*** Commands ***
  1: [s]tatus	  2: [u]pdate	  3: [r]evert	  4: [a]dd untracked
  5: [p]atch	  6: [d]iff	  7: [q]uit	  8: [h]elp
What now> 
```
- status 没鸟用
- update 进入update模式,列出工作区修改和删除的文件列表,新增的文件不会显示
- revert 把已经存到暂存区的文件从暂存区剔除
- add untracked 把新增文件添加到暂存区
- patch 显示当前版本和本地版本库的差异,决定是否添加这些修改到暂存区
- diff  比较本地版本库和暂存区的区别

```
git add -p  //进入patch模式
git add -u  //进入update模式
```

### git commit
```
git commit -C HEAD  修改最新一条提交记录的提交原因
同样可以把HEAD换成提交ID号
```

### git mv 
移动或重命名文件和目录
```
git mv a.md b.md    //a.md重命名为b.md,加上-f可以强制重命名,并保存到暂存区
```

### git rm
从本地和暂存区移除文件或目录,目录需要-r

### git status
```
git status -s   //简短方式查看工作区和暂存区的文件状态
```

## 操作分支
### git branch
```
git branch -a   //查看本地版本库和远程版本库的分支列表
git branch -r   //查看远程版本库的分支列表,加上-d可以删除之
git branch -D branch_name   //分支未提交到本地版本库前强制删除
git branch -vv  //查看带有最后提交ID, 最近提交原因等的本地版本库分支列表
```

### git merge
将其他分支合并到当前分支
```
git merge branch_name
```

### git checkout
切换分支
```
git checkout -b daily   //创建并切换分支
git checkout HEAD demo.md   //从本地版本库的HEAD中检出demo.md并覆盖工作区,没有HEAD的话就是从暂存区
git checkout -p other_branch    //比较两个分支的差异内容
```

### git stash
在git栈中保存当前修改和删除的工作进度
```
git stash   //把未提交的文件保存到git栈
git stash list  //查看栈中的列表
git stash show stash@{0}    //查看栈中的一条记录
git stash rm stash@{0}  //移除一条记录
git stash pop   //pop一条记录
git stash branch new_branch //检出最近的一条记录并创建一个分支
git stash clear //清空栈
git stash create    //为当前删除或修改的文件创建一个自定义的栈并返回一个ID,不算真正的栈
```

## 操作历史
### git log
```
git log -p  //git stash create  //为当前删除或修改的文件创建一个自定义的栈并返回一个ID,不算真正的栈
```

## 操作历史
### git log
```
git log -p  //显示带提交差异对比的历史记录
git log README.md   //显示README.md文件的提交的历史记录
git log --since="2 weeks ago"   //显示到两周前的历史记录
git log --before="2 weeks ago"  //显示截至到两周前的历史记录
git log --pretty=oneline    //一行输出简短的历史记录
```

### git cherry-pick
合并分支的一条或几条提交记录到当前分支末梢
```
git cherry-pick ID  //合并ID的历史提交
```

### git reset
将当前分支重设到指定的commit
```
git reset ID    //保留文件内容,回退提交历史
git reset --soft ID //暂存区和工作区不变
git reset --hard ID //任何改变都丢弃
```

### git revert
撤销某次操作,并把这次撤销当作一个提交提交
```
git revert HEAD //撤销前一次提交操作
git revert -n HEAD  //等所有撤销完成后一起提交
```

### git diff
查看工作区,暂存区,本地版本库之间的文件差异
[示意图](https://mmbiz.qpic.cn/mmbiz_png/kChlCQZAfH5eBrzeP4kHVbwcqAicZkgowbTtpHas5ZBpKFGFU8FxcaR8cCeANrcGmBwtpiaHkib8SQxJBLhOxEbOA/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

### git reflog
查看所有分支的操作记录,包括已经删除的分支

## 远程版本库连接
### git init
### git remote
```
git remote -v   //列出已经存在的远程分支的详细信息
```

### git fetch
将远程版本库更新取回到本地版本库

## 问题排查
### git blame
查看文件每行代码的历史信息
```
git blame -L 1,10 demo.md   //查看文件1~10行的历史信息
```

## 更多操作

## 备注
1. [y, n, q, a, d, /, ?]的解释  
- y : 接收修改
- n : 忽略修改
- q : 退出当前命令
- a : 添加修改
- d : 放弃修改
- / : 通过正则表达式匹配修改内容
- ? : 查看帮助信息
