---
layout:     post
title:      "JS基础"
subtitle:   "1.HTML中的js"
date:       2020-11-8
author:     "Lyb"
header-img: "img/post-bg-unix-linux.jpg"
tags:
    - 前端开发
    - JavaScript
---

+ script标签中的几个属性
  
  1.type 编写代码使用的脚本语言的类型

  2.src 表示要执行代码的外部文件

  3.defer 延迟脚本执行 ，延迟后，按照从上到下依次执行,这个比较重要
  ```
  <script defer="defer"></script>

  ```

  4.async 异步脚本执行，不保证按照顺序执行
  ```
  <script async></script>
  ```


  > 1.浏览器在解析页面时，会从上到下依次解析，遇到js脚本时，会停止解析document，先执行js后
  再去执行document。所以，如果我们的js文件耗时较长，则对于浏览器性能，会有很大阻碍，所以为什么
  我们经常说把js放在页面最后进行加载，就是为了增加性能。
  
  > 2.defer属性和async属性可以解决这个问题，他可以让我们的document在解析时，异步去解析js脚本
  此时我们的页面不会受到影响，解决了性能优化

  > 3.defer属性延迟加载js，一般在DOMContentloaded事件之前执行

  > 4.DOMContentloaded事件是页面的生命周期中的一环，HTML的生命周期大概有4个阶段 DOMContentLoaded, load, beforeunload, unload
   
  > 5.DOMContentLoaded 当页面的DOM元素已经渲染完成，也就是已经读取到了/HTML最后这个标签，但是img元素等资源还没有进行读取
  此时DOMContentLoaded方法可以去访问DOM节点，这个在jQuery中相当于$(document).ready(()=>{})

  > 6.load此时浏览器已经把页面和静态资源image等全部读取,这个相当于jQuery中的$(document).load(()=>{})

  > 7.defer属性和async属性都是解决js阻塞的方法，他们都是执行的异步加载模式，defer属性是延迟执行
  在浏览器解析html时异步进行js的加载，但是要等到html解析完毕后，在页面的DomContentloaded之前执行
  此时页面的css和img大小等还没有。async属性是异步执行，在浏览器解析html是同样异步加载js，但是它不会
  等待页面加载完成，与页面加载同时进行，只要是异步js加载完毕后，立即执行加载完毕的js，此时由于执行了js，
  页面渲染引擎会暂停执行html的渲染。如果不清楚可以去看图。