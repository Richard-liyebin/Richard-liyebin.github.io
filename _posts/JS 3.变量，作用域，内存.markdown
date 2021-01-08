---
layout:     post
title:      "JS基础"
subtitle:   "3.变量，作用域，内存"
date:       2020-11-8
author:     "Lyb"
header-img: "img/post-bg-unix-linux.jpg"
tags:
    - 前端开发
    - JavaScript
---

##### 1.变量
````
  a.基本类型变量和引用类型变量
    基本类型的变量复制时是重新创建一个内存空间
    引用类型变量复制时，是复制引用的指针，指向同一内存空间

````
##### 2.参数
````
  a.参数的传递只有一种形式，那就是值传递。
  b.基本类型的参数传递时把值复制给参数，引用类型的值传递时把内存地址复制给参数，指向同一地址
  c.引用类型的参数赋值以后，如果在函数内部重新进行引用类型的创建和修改，则被视为局部对象，当函数使用完毕后销毁，不会修改到外部对象。例如：

                function setName(num) {
                  num.name = 'richard';
                }
                let mynum = new Object(); //创建一个新对象
                setName(mynum);   //这里把我们的对象作为参数传递地址给num，指向同一地址。
                console.log(mynum.name) //此时一定是richard

              注意：
                function setName(num) {
                  num.name = 'richard';
                  num = new Object(); //注意了，在函数内部重新定义了num新对象，并且赋值jack
                  num.name = 'Jack';
                }
                let mynum = new Object(); //创建一个新对象
                setName(mynum);   //这里把我们的对象作为参数传递地址给num，指向同一地址。
                console.log(mynum.name) //此时如果不知道会以为是jack毕竟在函数中重新赋值了，但是不是的，此时在函数内部重写对象num时，此时的num变量引用的就是一个局部对象，函数退出则销毁了，只能改变函数内部引用，所以依然不会改变外部对象，因此外部引用打印输出依然是richard。
````


##### 3.类型

````
 a.基本类型 ：String Number Boolean Null Undefined
 b.引用类型 ：Object
 Object类型是一个大类型，所有的引用类型都是Object的实例，都属于对象，但是对象又区分为
 什么类型的对象。像 Object Array Date RegExp 等类型的对象

 c.类型检测 ： 
              1.typeof检测类型
                typeof可检测的类型有number string boolean undefined object funciton六种
````

##### 4.作用域和作用域链
      a.js中的执行环境也称为环境，分为全局环境和局部环境。每个环境中都有与之关联的变量对象。
      b.作用域链的作用就是保证对执行环境中的函数和变量的依次访问。

##### 5.垃圾回收机制

      a.标记清除：
      js中的垃圾回收器会给存储在内存中的所有变量都添加上一个标记。
      之后会去掉环境中的变量和被引用的变量的标记。
      之后垃圾回收器会删除那些依然存在标记的变量，因为已经无法引用了，并清除他们的内存。

      b.引用计数

