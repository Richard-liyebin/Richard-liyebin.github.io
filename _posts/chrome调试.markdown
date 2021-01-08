---
layout:     post
title:      "chrome 调试技巧"
subtitle:   "chrome 调试"
date:       2020-12-1
author:     "Lyb"
header-img: "img/post-bg-unix-linux.jpg"
tags:
    - 前端开发
    - Chrome
---

chrome 调试技巧
----
### 1.console 部分

> 1.console.log('abc') 普通打印

> 2.console.error('abc') 打印错误信息

> 3.console.info('abc') 打印信息

> 4.console.warn('abc') 打印警告

````
![Image text] 
````

> 5.console.log("%s年",2020) '%s'表示字符串,替换后面的东西为字符串，并打印

> 6.console.log("%d年"，2020) '%d'表示整数，替换后面的东西

> 7.console.log("%f",3.1415) '%f'表示浮点数， 表示打印成浮点数

> 8.console.log("%o",obj) '%o'表示对象

> 9.console.log("%c我是%自定义样式",{"font-size:30px","color:red"})前面的%c为30px,后面的自定义样式为红色

> 10.console.dir() 打印对象，成为Object的形式,而不是直接显示{a:"1"},

> 11.console.table() 把对象打印成table表格的形式，更加直观

> 12.console.count() 写在函数中，用于打印函数的调用次数，返回调用次数值

> 13.console.time() 开启一个计时器
> 14.console.timeEnd() 用于关闭定时器 
> 他俩可以一起使用，用于测试执行所需要的时间，返回的是从time到timeEnd的所有时间


### 2.Debug 代码调试

+ 1.熟悉调试工具调试器
+ 2.任重道远，渐渐熟悉


### 3.react 代码调试， react Devtool
### 4.vue 代码调试， vue Devtool

### 5.快速定位文件

> 1.ctrl+p 在devtool中打开搜索文件框，进行文件的迅速搜索和定位

> 2.ctrl+p 中搜索@，可以迅速查询到当前成员函数名

### 6.快捷开启f12和选择元素按钮

> 1.ctrl+shift+c 快捷开启f12
> 2.再次ctrl+shift+c 

### 6.js代码格式化

>1.在代码调试的位置，左下角有一个{}标记，点击即可把打包的代码格式化，便于查看

### 7.chrome截图

> 1.打开chrome，打开f12开发者工具，并且ctrl+shift+p，打开功能工具，输入screenshot，可以选择截图方式，可全屏，可部分，可截取dom节点，比较方便

### 8.缓存上一步的操作

> 1.$_ 符号，可以进行上一步操作的缓存，打印出上一次执行的结果

### 9.$ $$ 快速选择dom

> $相当于querySelect（） $$相当于querySelectAll()


### 10.css属性快速设定值 

>shift+方向键，上下以10倍增减

>ctrl+方向键，上下以100倍增减

>alt+方向键，上下以0.1增减

>元素上按H键，可以快速显示隐藏