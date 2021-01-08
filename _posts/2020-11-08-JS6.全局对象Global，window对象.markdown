---
layout:     post
title:      "JS基础"
subtitle:   "6.全局对象"
date:       2020-11-08
author:     "Lyb"
header-img: "img/post-bg-unix-linux.jpg"
tags:
    - 前端开发
    - JavaScript
---

#### 全局对象Global

概念：全集对象global是js中的兜底对象，意思就是，只要是不属于任何其他对象的属性和方法，那么都可以看作是global对象的方法。例如isNaN() isFinite() parseInt() parseFloat()等都是属于global对象的方法。

典型的几个方法：

一：URI编码方法： 

    编码：
    1.encodeURI() 对整个uri进行编码，但是不会对本身属于uri的特殊字符比如/ ： 等进行编码
    2.encodeURIComponent() 对uri的某一部分进行编码，一般多用于查询字符串参数的编码


    解码：
    1.decodeURI() 
    2.decodeURIComponent()



二：evel解析方法

    evel()是整个ECMAscript最强大的方法，他相当于一个完整的代码解析器，可以帮我们把代码进行解析，执行，但是在evel内创建的变量和函数都不会被提升，只能根据js规则进行顺序执行；严格模式下不可用


#### window对象

概念：在浏览器中，因为浏览器环境中没有Global对象，Global对象在js解释器中，浏览器把Global看作是window对象的一部分，所以在全局作用域中声明的变量和函数，都成了window对象的属性。换句话说，在浏览器中，window对象包含了全局对象，但同时，window对象还包含了其他一些功能。