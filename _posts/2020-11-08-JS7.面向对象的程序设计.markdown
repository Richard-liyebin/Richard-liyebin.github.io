---
layout:     post
title:      "JS基础"
subtitle:   "7.面向对象程序设计"
date:       2020-11-8
author:     "Lyb"
header-img: "img/post-bg-unix-linux.jpg"
tags:
    - 前端开发
    - JavaScript
---


## 面向对象的程序设计 （非常重要）

补：创建一个对象在之前讲过，要么new一个Object的实例，要么就直接使用对象字面量的形式进行创建。


1.对象的属性类型 （对象内部的一些东西）
  
  a.数据属性：configurable：（能否delete删除属性)
              enumerable：（能否通过for-in循环遍历属性）
              writable：（能否修改属性得值）
              value:（包含这个属性得数据值）


  b.访问器属性:configurable：（能否delete删除属性)
              enumerable：（能否通过for-in循环遍历属性）
              get：（读取属性时调用得函数）
              set：（设置属性时调用的函数）

````
定义单个属性
Objcet.defineProperty(ppp,'name',{
    configurable：true，
    ....
})


定义多个属性
Object.defineProperties(ppp,{
    name:{
        writable:true,
        value:'ssr'
    },
    age:{
        writable:true,
        value:22,
    },
    _address:{
        writable:true,
        value:'cdc'
    },
    address:{
        get:function(){
            return this._address
        },
        set:function(newval){
            if(newval == 'csc'){
                this._address = 'csc'
                console.log('yes,ok')
            }else{
                console.error('newval must be csc')
            }
            
        }
    }
})

作为一个了解，每一个属性代表的意义，如何去设置一个访问器属性。