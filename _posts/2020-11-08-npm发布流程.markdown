---
layout:     post
title:      "NPM 发布流程"
subtitle:   "nmp发布"
date:       2020-11-08
author:     "Lyb"
header-img: "img/post-bg-unix-linux.jpg"
tags:
    - 前端开发
    - NPM
---

 
 npm注册发布
 ====
 一.注册npm账号
 ----
### 发布包之前必须先注册一个npm账号

### 注册方式

#####  1.官网直接注册，需要验证邮箱
#####  2.通过命令行进行注册
>npm adduser

>Username:你的用户名

>Password:你的密码  

>Email:你的邮箱 （填完后需要去邮箱验证，验证成功后创建完毕）

二.初始化一个项目
----
### 1.创建文件夹
##### a.在本地创建或者使用命令行mdr动态创建
##### b.初始化一个项目
> npm init  项目名，版本号，主文件等，可自行设置

```json
{
  "name": "richard_firstnpm",
  "version": "1.0.0",
  "description": "this is richard's first npm ",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "repository": {
    "type": "git",
    "url": "git+https://github.com/Richard-liyebin/npm-admin.git"
  },
  "author": "",
  "license": "ISC",
  "bugs": {
    "url": "https://github.com/Richard-liyebin/npm-admin/issues"
  },
  "homepage": "https://github.com/Richard-liyebin/npm-admin#readme"
}

```

默认字段简介：
+ name：发布的包名，默认是上级文件夹名。不得与现在npm中的包名重复。包名不能有大写字母/空格/下滑线!

+ version：你这个包的版本，默认是1.0.0。对于npm包的版本号有着一系列的规则，模块的版本号采用X.Y.Z的格式，具体体现为：

  1、修复bug，小改动，增加z。

  2、增加新特性，可向后兼容，增加y

  3、有很大的改动，无法向下兼容,增加x

+ description：项目简介

+ mian：入口文件，默认是Index.js，可以修改成自己的文件 
+ scripts：包含各种脚本执行命令
+ test：测试命令。
+ author：写自己的账号名
+ license：应该是协议

三.发布
----
#### 1.npm login
>npm login 输入用户名，密码，邮箱

>Username:你的用户名

>Password:密码

>Email:邮箱

#### 2.npm publish
>npm publish 发布私包

>npm publish --access=public 发布公开包


四.撤销发布
----

#### 1.npm unpublish
例如：
>1、npm unpublish richard_npm@1.0.0 删除某个版本

>2、npm unpublish richard_npm --force 删除整个npm市场的包


五.更新包
----
#### 1.修改包的版本号（package.json里的version字段）

#### 2.npm publish 发布
>npm version patch && git push --follow-tags &&npm publish 

>npm version minor && git push --follow-tags && npm publish

>npm version major && git push --follow-tags && npm publish

六.发布安装
----
>npm install richard_npm


七.其他命令
----
#### 1.管理包权限查看模块拥有者
>npm owner ls
#### 2.添加一个发布者
>npm owner add
#### 3.删除一个发布者
>npm owner rm
#### 4.查看当前项目引用了哪些包
>npm ls