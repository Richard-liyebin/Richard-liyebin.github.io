---
layout:     post
title:      "JS基础"
subtitle:   "4.数组方法"
date:       2020-11-08
author:     "Lyb"
header-img: "img/post-bg-unix-linux.jpg"
tags:
    - 前端开发
    - JavaScript
---



##  js笔记---------------数组
### 一.js基本数组方法
##### 1.push() pop()
```
1.push() 从当前数组末尾添加元素， 返回的是当前数组的数组长度                               
let arr = [1,2,3,4,5];
arr.push(6,7,8)//输出8

2.pop()从当前数组末尾删除元素，删除的是最后一个元素，返回的是被删除的这个元素
let arr2 = [1,2,3,4,5];
arr2.pop() //输出5
```

##### 2.unshift() shift()
```
1.unshift() 从当前数组开头添加元素，返回的是当前数组的数组长度
let arr = [1,2,3,4,5]
arr.unshift(6,7,8)//输出8
2.shift() 从当前数组开头删除元素，删除的是第一个元素，返回的是被删除的元素值
let arr = [1,2,3,4,5]
arr.shift()//输出1  
```
##### 3.sort()
```
sort（）对数组进行排序，默认排序为升序，sort参数可以是一个回调函数，可以对数组进行降序

1.let arr = [5,4,3,2,1];
arr.sort() //返回[1,2,3,4,5],默认做升序排列

2.let  arr = [1,2,3,4,5]
arr.sort((a,b) => {
    if(a>b){
    return -1
    }
})//降序排列
```
##### 4.reverse()
```
reverse()对数组进行翻转处理，无论数组如何排列，都将他倒序
let arr = [1,2,3,4,5]
arr.reverse()//输出[5,4,3,2,1]
```
##### 5.concat()
```
concat()数组拼接，此方法在使用时，会先在原数组上创建出一个相同的数组副本，然后进行新数组的组合操作，返回的是新数组。记住，concat（）是在新数组上进行修改，对原数组不产生影响

let arr = [1,2,3,4]
arr.concat([4,5,6])//输出[1,2,3,4,4,5,6]新数组
此时的arr仍然是[1,2,3,4]

***注意了，因为arr.concat()出的是一个新数组副本，直接arr.concat([4,5,6])的确是得到了一个新数组，但是你不用变量去接收它，它就会被回收了。因为你没有用它，所以，一般会用一个变量去接收它
let  arr2 = arr.concat([4,5,6])
此时 arr2 [1,2,3,4,5,6]，但arr 仍是[1,2,3,4]
```
##### 6.slice()
```
slice() 截取数组，slice(start,end) start是起始位置 end是结束的位置,，返回的是截取后的数组，也是在使用时创建了一个数组副本，并且不改变原数组，
let arr = [1,2,3,4,5]
1. 不带参数 默认从0位置开始，截取到数组末尾
let arr2 = arr.slice() //返回新的[1,2,3,4,5],
2.带一个参数，从当前位置，截取到数组末尾
let arr3 = arr.slice(1) 从第二个元素开始，截取到最后，返回新的[2,3,4,5]
3.带两个参数，从start，截取到end
let arr4 = arr.slice(0,1) 
```
##### 7.splice()

```
splice(a,b,c) 删除，插入，替换 三个功能都可以实现
根据传递参数的不同，实现不同的功能,a代表起始位置，b代表要删除的个数，c代表替换的值
1.splice(a,b) 删除数组元素 a代表起始位置，b代表删除数组的长度或个数
返回的是被删除的元素,不会创建新副本，会修改原本的数组元素
let arr = [1,2,3,4]
arr.splice(0,1) //返回[1]，此时arr = [2,3,4]

2.splice（a,0,c）插入数组元素，a代表起始位置，b代表删除的个数，c代表添加的数组元素
let arr = [1,2,3,4]
arr.splice(3,0,5,6)//返回[ ],此时arr = [1,2,3,5,6,4],
注意，插入时候的位置，是在3之前插入，而不是之后
如果a超过当前数组长度，默认插入到最后

3.splice(a,1,c) 替换，跟插入原理相同，如果中间删除的个数为1，再把c替换上去，也就是替换

```
##### 8.join() 
```
join() 数组拼接成字符串
let arr = [1,2,3,4,5]
1.arr.join()，没有参数，默认用','隔开 ，返回1,2,3,4,5
2.arr.join("") 参数是空 返回12345
3.arr.join("-") 参数是- 返回 1-2-3-4-5
```

### 二.ES5新增数组方法

##### 9.indexOf() lastIndexOf()
```
1.indexof(a,b)用于查找数组某个元素的位置，找到返回该元素在数组中的位置，没找到返回-1
携带两个参数，a参数是我们需要查找的值，b参数是我们从哪里开始查找
   let arr = [1,2,3,4,5]
   arr.indexOf(3) //返回 2
   arr.indexOf(3,2)//返回 2
   arr.indexOf(6)//返回-1 数组中没有该元素找不到
   arr.indexOf(3,3)//返回-1，数组从第四个元素开始找，当然也找不到
   
 2.lastIndexOf(a,b)也是用于查找数组中的某个元素的位置，从后往前找，找到数组元素，返回正常的他所在的位置，其实跟indexOf（）是一样的原理，不过也是从b位置开始，去寻找a，不过一个往后，一个往前罢了 
```
##### 10.forEach() 
```
forEach（item，index，arr）用于遍历数组并且给数组中的每一项运行给定的函数
此方法没有返回值
arr.forEach((item,index,arr) => { })
```

##### 11.map()
```
map（）指映射的意思，给数组中的每一项运行给定的函数，并且返回每一项组成的新数组,不改变原数组，也是建立一个副本需要被变量接收
 let arr = [1,2,3,4,5]
let arr1 = arr.map((item) => {
    return item*2
})
```
##### 12.filter()
```
filter（）指过滤，给数组中的每一项运行一个给定的函数，并且只会把返回true
的所有选项组成一个新数组，同样不会改变原数组
let arr = [1,2,3,4,5]
let arr1 = arr.filter((item) => {
    if(item%2 === 0){
        return true
    }else{
        return false
    }
})
```
##### 13.every()
```
every（）判断数组中每一项是否都满足条件，如果全部满足才会返回true，否则返回false
let arr = [1,2,3,4,5]
let arr1 = arr.every((item) => {
   rerurn item<6
})
arr1 输出 true
```
##### 14.some()
```
some（） 跟every（）相似，也是返回true或者false，不过some只需要部分满足，就可以返回true
```

##### 15.reduce()

```
reduce((prev,cur,index,arr) => {

},init)也叫做累加器，可以把数组进行累加操作，一般有五个参数
arr 表示将要原数组；
prev 表示上一次调用回调时的返回值也可以叫做上次的累加和，或者初始值 init;
cur 表示当前正在处理的数组元素；
index 表示当前正在处理的数组元素的索引，若提供 init 值，则索引为0，否则索引为1；
init 表示初始值。
```

### 三.ES6拓展数组方法

##### 1.Array.from()
```
1.Array.from()用于把两类对象转换成数组
   a.类数组对象，并且类数组对象必须具备以下条件：{
　                   1.该类数组对象必须具有length属性，用于指定数组的长度。如果没有       length属性，那么转换后的数组是一个空数组。　　
                     2.该类数组对象的属性名必须为数值型或字符串型的数字
                     3.该类数组对象的属性名可以加引号，也可以不加引号
                     }
    b.map set 结构的对象
    
2.Array.from不仅可以把类数组对象和map set结构的对象转换为数组，还可以把字符串转换为数组    
3.Array.from还可以接受第二个参数，作用类似于数组的map方法，用来对每个元素进行处理，将处理后的值放入返回的数组。

Array.from(arrayLike, x => x * x);
// 等同于
Array.from(arrayLike).map(x => x * x);

Array.from([1, 2, 3], (x) => x * x)
// [1, 4, 9]
```
##### 2.Array.of()
```
1.Array.of () 用于将一组值，转换为数组
Array.of(1,2,3,4,5) 返回[1,2,3,4,5]
如果需要，就用变量接住
2.Array.of() 可以代替 new Array ，创建一个新数组
```
##### 3.copyWithin(target，start，end)
```
copyWithin() 用于将数组的某一项复制到数组另一项中,会对当前数组进行改变
let arr = [1,2,3,4,5]
arr.copyWithin(1,4)//返回[1,5,3,4,5]
```
##### 4.find() findIndex()
```
1.find() find参数是一个回调函数，给数组中每一个item，运行函数，直到找到第一个满足条件返回true的成员，并且返回该成员
let arr = [1,2,3,4,5]
arr.find((item) => {
   return  item>4
})//输出5
如果找不到，输出undefined

2.findIndex() 与find（）非常相似，不过findIndex返回的是满足条件返回true的成员的位置，
如果找不到，返回-1
```
##### 5.fill()
```
fill（）方法，使用给定值，填充一个数组
let arr = [1,2,3]
arr.fill(7)//[7,7,7]

fill方法还可以接受第二个和第三个参数，用于指定填充的起始位置和结束位置
['a', 'b', 'c'].fill(7, 1, 2)
// ['a', 7, 'c']
上面代码表示，fill方法从 1 号位开始，向原数组填充 7，到 2 号位之前结束。
```
##### 6.values() keys() entires()
```

ES6 提供三个新的方法——entries()，keys()和values()——用于遍历数组。它们都返回一个遍历器对象（详见《Iterator》一章），可以用for...of循环进行遍历，唯一的区别是keys()是对键名的遍历、values()是对键值的遍历，entries()是对键值对的遍历。
for (let index of ['a', 'b'].keys()) {
  console.log(index);}
// 0
// 1
for (let elem of ['a', 'b'].values()) {
  console.log(elem);}
// 'a'
// 'b'
for (let [index, elem] of ['a', 'b'].entries()) {
  console.log(index, elem);}
// 0 "a"
// 1 "b"
```
##### 7.includes()
```

表示某个数组是否包含给定的值，与字符串的includes方法类似,返回的是一个布尔值true或者false
[1, 2, 3].includes(2)     // true
[1, 2, 3].includes(4)     // false
[1, 2, NaN].includes(NaN) // true

注意了，这个includes（）其实跟indexOf（）很像，都是用于查找数组中是否存在，虽然includes返回的是布尔值，indexOf返回的是位置，或者-1，但是includes可以确定是否包含NAN，

let arr = [1,2,3,NAN]
arr.indexOf(NAN) //返回-1
arr.includes(NAN) //返回true
```
##### 8.flat() flatmap()
```
1.flat（） 用于数组降维，十分重要的数组方法，不传参数默认只降一维，如果flat（2），说明降二维数组，如果参数为Infinity，那么不管多少维度的数组，都降低成一维数组,，同样不改变原数组。也是创建副本，如果需要处理后的数组，那就用变量接住
    let arr = [1,2,[3,4]]
    arr.flat()// [1,2,3,4]
    arr.flat(2)
    arr.flat(Infinity)
    
2.flatmap(() => {}) 同样用于数组降维，与flat区别在于，flatmap（）参数是一个回调函数，相当于map出一个数组映射，给每一个数组元素执行map，然后返回一个新数组，返回以后再执行flat（），但是只能展开一层数组

与map的区别和联系：1.相似点，他们都是映射的形式处理数据
                           2.不同点，map返回的数据如果是数组，是不会打散的
                             flatmap（）会被打散，看例子：
                             let arr = [1,2,3,4,5]
                             arr.flatMap((item) => {
                            return [item,item*2]
                            })// [1, 2, 2, 4, 3, 6, 4, 8, 5, 10]
                            arr.map((item) => {
                            return [item,item*2]
                            })//[[1, 2],[ 2, 4], [3, 6],[ 4, 8], [5, 10]]
                            

```
##### 









