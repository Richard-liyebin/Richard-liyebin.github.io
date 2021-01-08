---
layout:     post
title:      "Git 笔记"
subtitle:   "git基本指令"
date:       2020-11-8
author:     "Lyb"
header-img: "img/post-bg-unix-linux.jpg"
tags:
    - 前端开发
    - Git
---
git 笔记
----
## 1.简介
git commit提交规范

init: 初始化

feat: 新特性

fix: 修改问题

refactor: 代码重构

docs: 文档修改

style: 代码格式修改, 注意不是 css 修改

test: 测试用例修改

build: 构建项目

chore: 其他修改, 比如依赖管理

scope: commit 影响的范围, 比如: route, component, utils, build...

subject: commit 的概述



功能：项目中存储 共享 合并 历史回退 代码追踪等功能

常用的VSC系统软件

CVS：2000以前
SVN：2010之前
Git：2010之后

Ctrl+ins  复制

Shift+ins 粘贴

## 2.使用

  ### a.本地命令

  + 1 设置用户名和邮箱，也就是告诉git，你是谁  
    > git config --global user.name  
    > git config --global user.email

  + 2 查看配置信息列表  
    > git config --list  

  + 3 初始化一个git仓库  
    > git init

  + 4 查看当前工作区和暂存区状态  
    > git status

  + 5 把文件添加到暂存区  
    > git add filename  或者 git add .(全部添加)

  + 6 把某个文件从暂存区中撤销  
    > git checkout filename

  + 7 把文件提交到本地git仓库  
    > git commit -m "提交描述"

  + 8 查看提交的版本信息 （里面的信息包括提交说明，和每个提交版本的id）  
    > git log

  + 9 查看所有版本的信息，包括删除，回退了以后的版本  
    > git reflog  
    相比git log而言，git reflog可以查看被删除或者回退之前的版本，可以后悔。

  + 10 版本回退  
    > git reset --hard 版本id

  + 11 查看所有分支
    > git branch

  + 12 创建分支和切换分支
    > git branch 分支名    git checkout 分支名（注意和暂存区移除文件一样）  
    > git checkout -b 分支名  同样的效果，是上面的结合

  + 13 合并分支  （一般github上去做）
    > git merge 分支名 （只有定位到当前主分支，才可以去合并我们需要合并的分支）

  + 14 删除分支  
    > git branch -D 分支名 强制删除分支  
    > git branch -d 分支名 删除合并了的分支

  + 15 删除文件（提交到远程，远程也会更新）
    > git rm 文件名

  ### b.连接远程仓库
  + 1 连接到远程仓库
    > git remote add 仓库名（默认origin）仓库地址 git.xxx

  + 2 克隆远程仓库  
    > git clone 仓库地址

  + 3 实时更新本地仓库（重要，避免覆盖其他人的更新）  
    > git pull 仓库名（默认origin） 分支名

  + 4 提交到远程仓库  
    > git push 仓库名（默认origin） 分支名

  + 5 文件提交忽略 (文件中添加忽略的文件即可)
    > .gitignore