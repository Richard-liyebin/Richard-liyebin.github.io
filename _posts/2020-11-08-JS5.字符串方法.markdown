---
layout:     post
title:      "JS基础"
subtitle:   "5.字符串方法"
date:       2020-11-08
author:     "Lyb"
header-img: "img/post-bg-unix-linux.jpg"
tags:
    - 前端开发
    - JavaScript
---


#### 1.字符串截取 slice() substr() substring() 
````
1.slice(a,b) 字符串的截取，从下标为a的字符开始，截取到第b个之前的位置，不包含第b个，如果只有一个参数a,则从a截取到最后。返回的是被截取的那一段副本字符串，对原字符串毫无影响，如果ab都是负值，则负值加上字符串长度变为正值继续计算
例子：

var str = 'hello world';
console.log(str.slice(1,3)) // 返回'el'被截取的字符 
console.log(str) //依然是hello world
console.log(str.slice(-3,-1)) // slice会将负值与字符串长度相加，得到正值。再来计算，即str.slice(8,12)


2.substr(a,b) 字符串的截取，从a字符串开始，截取返回的字符串是b个长度的字符串。如果只有a一个参数，则截取到末尾，不会对原字符串产生影响，如果ab都是负值，则第一个参数加上字符串长度变为正，第二个负值直接变为0
var str = 'hello world'
console.log(str.substr(1)) //"ello world"
console.log(str.substr(1,3)) //"ell"
console.log(str.substr(-3，1)) //第一个加上长度，第二个变为0 即为str.substr(8,1) , 第二个参数一般不为负值，因为代表截取个数

3.substring(a,b) 字符串的截取，从a字符串开始，截取到字符串b的位置，不包含b。如果只有一个值，则截取到最后。如果ab都是负值，则全部转换为0。只要是负值就转换为0
var str = 'hello world'
console.log(str.substring(1)) //"ello world"
console.log(str.substring(1,3)) //"el"


注意，字符串中的slice和substring的截取方式一样，都是从参数a，截取到参数b，而substr的截取方式是从参数a开始，截取b个，三个方法如果没有写第二个参数，则都是从参数a截取到最后。
可以类比数组方法中的slice和splice，slice是从a截取到b，splice是从a开始，截取b个字符串
````

#### 2.字符串操作 concat() 

````
1.concat() 字符串拼接，返回的是一个新字符串，不改变原字符串，同样需要变量接收，也可以接收多个参数，则多个参数一起拼接。
  var str = 'hello world';
  var str1 = str.concat('ll');
  console.log(str,str1) // hello world , hello worldll
````

#### 3.字符串访问单个字符方法 charAt()  charCodeAt()

````
var str = 'hello world';
console.log(str.charAt(1)) //访问1位置的字符，则返回 'e'；
console.log(str.charCodeAt(1)) //访问输出1位置字符的字符编码 返回e的字符编码101
````


#### 4.字符串位置方法 indexOf() lastIndexOf()

````
1.indexOf()字符串跟数组一样，都是找到返回位置，找不到返回-1
var str = 'hello world'
str.indexOf('e')//1
str.indexOf('y')//-1
2.lastIndexOf()从后往前找，找到的字符，返回正常的他所在的位置
str.lastIndexOf('r')//8
````

#### 5.字符串去空格 trim()  trimRight() trimLeft()

````
1.trim() 可以去除左右两端的空格
str = ' hello world ';
str.trim() //返回'hello world'
相当于 str.replace(/^\s+|\s+$/g,'')

2.trimRight() 可以去除右端的空格
str.trimRight() //返回' hello world'
相当于 str.replace(/\s+$/g,'')

3.trimLeft()  可以去除左端的空格
str.trimLeft() //返回'hello world '
相当于 str.replace(/^\s+/g,'')

4.如果要去除所有空格
只能 str.replace(/\s+/g,'')

````


#### 6.字符串大小写转换 toUpperCase()  toLowerCase()

````
1.toUpperCase() 字符串转大写 不改变原字符串，要使用就用变量赋值
str.toUpperCase()即可

````