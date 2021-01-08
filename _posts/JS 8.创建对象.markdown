---
layout:     post
title:      "JS基础"
subtitle:   "8.创建对象"
date:       2020-11-8
author:     "Lyb"
header-img: "img/post-bg-unix-linux.jpg"
tags:
    - 前端开发
    - JavaScript
---


## 创建对象

### 一.工厂模式

````
function createPerson(name,age,address){
  var o = new Object();
  o.name = name;
  o.age = age;
  o.address = address
  o.sayname = function(){
    console.log('my name is '+ o.name)
  }
  return o //返回最后创建好的对象
}
var personOne = createPerson('lyb',22,'cdc')

````
> 工厂模式可以为我们创建多个相似的对象，但是无法让我们检测对象的类型，因此构造函数模式出现



### 二.构造函数模式

````
function Person(name,age,address){
  this.name = name ;
  this.age = age;
  this.address = address;
  this.sayname = (() => {
    console.log('my c name is '+ this.name)
  })
}

var person1 = new Person('lyb',22,'cdc')

此时检测person1对象的类型：

 person1.constructor == Person //true
 person1 instanceof Person //true
````
> 此时我们可以检测到person1的类型，即用 person1.constructor == Person 或者 person1 instanceof Person

#### 注意： 
    
   1. 构造函数毕竟也是一个函数，this指向的是全局环境

    ````
    this的指向问题：
        1.obj.fun()  fun中的this指向当前调用fun方法的obj对象
        2.new Fun()  Fun中的this->指的是正在创建的新对象
        3.fun()和匿名函数自调用 this因为前面没有. 默认指window
        4.构造函数类型.prototype.fun fun中的this指将来调用fun.前的子对象
        5.如果this不是想要的 fun.call（）替换this的对象
    ````

   2. 将构造函数当作普通函数，毕竟构造函数也是函数，如果不用new，那么跟一般的普通函数毫无区别
   
      ````
        function Person(name,age,address){
            this.name = name ;
            this.age = age;
            this.address = address;
            this.sayname = (() => {
            console.log('my c name is '+ this.name)
         })
      }
        Person('lu',22,'csc') //当作一般函数直接传参调用
        所有的this都指向window，因此调用的时候
        window.sayname() // 'my c name is lu'
        window.name // lu

      ````

   
     3. 既然构造函数可以当成一般函数使用，则也可以改变其作用域，正如之前所了解，使用call进行改变
      ````
      var o = new Object()
      Person.call(o,'lz',25,'cxc')
      o.sayname()// 'my c name is cxc
      o.name // 'lz'
      ````
    
    4. 构造函数的this既然指向的是全局环境，里面的变量和函数都可以使用window去访问到，那么会出现一个问题（重要重要重要重要重要）
      ````
       function Person(name,age,address){
            this.sayname = (() => {
            console.log('my c name is '+ this.name)
         })
      }
      var person1 = new Person('LX',23,'CDC')
      var person2 = new Person('XS',25,'CSC')
      此时的person1和person2都是构造函数Person的实例，没有什么问题，但是在Person内部的函数写法，会使得每一次创建新的实例时，都会去重新创建一个新的sayname方法。这样就极大的浪费了内存空间
      例如 person1.sayname == person2.sayname //返回false

      解决方法很简单，我们在构造函数外部创建出一个方法，然后引用进去就可以了，这样就能保证每一个构造函数得实例对象，都指向同一个方法:

        function Person(name,age,address){
            this.sayname = sayname
        }
        function sayname(){
          console.log(this.name)
        }
        var person1 = new Person('LX',23,'CDC')
        var person2 = new Person('XS',25,'CSC')
      因为此时得sayname方法指向全局，所以构造函数得所有sayname方法都指向全局。
        person1.sayname == person2.sayname //返回true
      此时的person1和person2都使用同一个全局函数sayname  
     

     问题又出现了，虽然能够满足多个实例共用一个全局方法，但是如果我们构造函数需要很多方法呢？岂不是要在全局定义很多个全局方法，这样就违背了封装的意义了，因此下一种模式出现！！！
        ````
      
  ### 三.原型模式

      ````
      function Person(){
        Person.prototype.name = 'lyb';
        Person.prototype.age = 23;
        Person.prototype.address = 'cdc'
        Person.prototype.sayname = (() => {
          console.log('my name is '+this.name)
        })
      }
      var person1 = new Person();
      person1.sayname();
      var person2 = new Person();
      person2.sayname();

      ````


  
      