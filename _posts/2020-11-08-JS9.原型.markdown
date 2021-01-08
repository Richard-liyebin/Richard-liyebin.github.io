---
layout:     post
title:      "JS基础"
subtitle:   "9.原型"
date:       2020-11-08
author:     "Lyb"
header-img: "img/post-bg-unix-linux.jpg"
tags:
    - 前端开发
    - JavaScript
---



## 原型（重要）
    重要概念：
    1. 当我们创建一个函数时，js就会为该函数创建一个prototype属性。这个属性指向函数的原型对象。（只有函数才有prototype属性）
    2. 在默认情况下，所有的原型对象都会自动获得一个constructor属性，这个属性是一个指向prototype属性所在函数的指针（也就是当前函数）
    3. 所有对象或者实例内部都有一个[[prototype]]属性（也叫做__proto__属性），指向其构造函数的原型对象
     ````
     简单理解(一家三口)：
      function Person(){
        this.name = name;
        this.age = age;
        Person.prototype.address = 'cdc'
      }
      此时的Person就是我们的构造函数，理解为妈妈！与此同时，妈妈的老公也就是爸爸，属于构造函数的原型对象，那么如何去访问到爸爸呢？我们说过，创建函数时，会自动为该函数创建一个prototype属性去指向当前函数的原型对象，所以爸爸应该是妈妈的老公： Person.prototype

      let person1 = new Person('lxl',24)
      此时的person1就是Person new出来的一个实例对象，理解为儿子！
      因为儿子是一个实例（对象），所以内部自然会有一个__proto__属性，指向其构造函数的原型对象（爸爸）
      所以person1.__proto__ === Person.prototype,所以儿子自然也就继承了爸爸和妈妈的东西。

      此时的constructor其实就是让爸爸Person.prototype去重新指向妈妈，即Person == Person.prototype.constructor  , 也可以让儿子去指向妈妈，因为儿子继承了爸爸的constructor 即 person1.constructor == Person.prototype
     ````
     4. 如果修改了原型中的值，也就是说，我不想继承爸爸的那个属性，那我就只好自己设置同名属性，设置同名属性。覆盖掉爸爸的属性即可，但如果覆盖以后，我拼累了，我只需要delete我自己的值，不想打拼了，去继承爸爸家业把，delete删掉自己的属性，又会自动继承父亲的同名属性

     5. hasOwnProperty()方法和in操作符都可以看我们的实例对象是否存在这个属性，这个属性可能是自己的，也可能是构造函数的原型中的。hasOwnProperty只能判断自己是否有这个属性，in操作符，既可以判断自己的又可以判断是不是构造函数的原型对象中的。
     ````

     ````

     注意补充：
      只有函数才有prototype属性，其他对象没有,只有函数，只有函数，只有函数！！！！。
      所有的实例都有[[prototype]]属性，也就是__proto__
     如果不清楚，去回忆一下那个图！