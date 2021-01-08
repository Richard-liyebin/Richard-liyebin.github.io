---
layout:     post
title:      "React生命周期"
subtitle:   "react 生命周期"
date:       2020-11-8
author:     "Lyb"
header-img: "img/post-bg-unix-linux.jpg"
tags:
    - 前端开发
    - React
---


### React 生命周期
##### 初始化阶段 运行阶段 销毁阶段

###### 一.初始化阶段
```

1.各种静态属性的设置
static defaultprops = { 
    name:'lyb',
    age:'22'
}

2.constructor（）{} 方法
设置组件的初始化状态

3.componentWillMount（） { }
组件即将被渲染到页面之前触发，此时可以开启定时器，或者向服务器发送请求等等

4.render（）
组件渲染阶段

5.componentDidMount（）{}
组件渲染完成之后触发，此时DOM元素已经存在，可以进行DOM操作，或者发送ajax也可以

```
###### 二.运行中的阶段

```
1.componentWillReceiveProps（nextProps）{}
组件接收到属性时触发，例如传递props变量的时候等等

注意：1.在接受父组件改变后的props需要重新渲染组件时用到的比较多
        2接受一个参数nextProps，它代表当前最新的值
       3.通过对比nextProps和this.props，将nextProps的state为当前组件的state，从而重新渲染组件


2.shouldComponentUpdate（newProps，newState）{}

当组件接收到新属性，或者组件的状态发生改变时触发。组件首次渲染时并不会触发 shouldComponentUpdate(newProps, newState) { if (newProps.number < 5) return true; return false } //该钩子函数可以接收到两个参数，新的属性和状态，返回true/false来控制组件是否需要更新。

主要用于性能优化(部分更新)唯一用于控制组件重新渲染的生命周期，由于在react中，setState以后，state发生变化，组件会进入重新渲染的流程，在这里return false可以阻止组件的更新因为react父组件的重新渲染会导致其所有子组件的重新渲染，这个时候其实我们是不需要所有子组件都跟着重新渲染的，因此需要在子组件的该生命周期中做判断


3、componentWillUpdate()
组件即将被更新时触发

shouldComponentUpdate返回true以后，组件进入重新渲染的流程，进入componentWillUpdate,这里同样可以拿到nextProps和nextState。

4、componentDidUpdate(prevProps，prevState)
组件被更新完成后触发。页面中产生了新的DOM的元素，可以进行DOM操作

组件更新完毕后，react只会在第一次初始化成功会进入componentDidmount,之后每次重新渲染后都会进入这个生命周期，这里可以拿到prevProps和prevState，即更新前的props和state。



```
###### 三.销毁阶段
```

1、componentWillUnmount()

组件被销毁时触发。这里我们可以进行一些清理操作，例如清理定时器，取消Redux的订阅事件等等。
```
