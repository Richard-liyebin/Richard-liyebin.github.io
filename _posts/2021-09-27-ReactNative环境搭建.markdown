---
layout:     post
title:      "React-Native"
subtitle:   "React-Native环境搭建"
date:       2021-9-27
author:     "Lyb"
header-img: "img/post-bg-unix-linux.jpg"
tags:
    - 前端开发
    - React-Native
---


## react-native Windows 安装文档 （详细且明确）(针对开启VPN的情况，如果不开启VPN，就会导致下载出错)


### RN环境搭建以及调试环境配置（windows android）

### 一. 配置基本的开发环境
#####  Node Python2 JDK（版本必须是1.8） 
> Node 版本使用12.x.x 或者 10.x.x，不要使用过高版本，否则容易出错！ 

> Python 版本必须是 2.x 否则容易出错

> JDK版本必须是1.8 否则容易出错

#### 1.安装Node(推荐nvm安装)
     ···
     node 版本管理推荐使用nvm进行安装，这样可以安装多个node版本，便于切换使用，因为
     react native环境搭建的话，不需要很高版本的node！

     命令：
     nvm --version 安装好了查看版本
     nvm install 12.x.x 或者 nvm install 10.x.x
     nvm list 可以看到你当前安装好的node版本
     nvm use 12.x.x 使用
     
     ···

#### 2.安装python 2（请记住它的安装路径！！！）

    ```
    网站 https://www.python.org/downloads/release/python-272/
    下载好了一路next即可
    没什么难度
    记住它的安装路径！

    ```
#### 3.安装JDK（请记住他的安装路径！！！）

    ```
    网站：https://www.cnblogs.com/heaven21cn/p/12596546.html
    或者：https://www.cnblogs.com/nojacky/p/9497724.html
    下载好了一路next即可
    请记住它的安装路径！
    
    ```
### 二.配置Android环境
· 配置之前，先检查一下以下基本配置，确认无误进行下一步

##### 1.node 
````
node --version   

v12.x.x 或者 v10.x.x
````
##### 2.python  
````
python

Python 2.7.17 (v2.7.17:c2f86d86e6, Oct 19 2019, 21:01:17) [MSC v.1500 64 bit (AMD64)] on win32
Type "help", "copyright", "credits" or "license" for more information.
>>>

````

##### 3.java -version ， javac
````
输入 java -version：

C:\Users\Root>java -version
java version "1.8.0_291"
Java(TM) SE Runtime Environment (build 1.8.0_291-b10)
Java HotSpot(TM) 64-Bit Server VM (build 25.291-b10, mixed mode)


输入 javac：

用法: java [-options] class [args...]
           (执行类)
   或  java [-options] -jar jarfile [args...]
           (执行 jar 文件)
其中选项包括:
    -d32          使用 32 位数据模型 (如果可用)
    -d64          使用 64 位数据模型 (如果可用)
    -server       选择 "server" VM
                  默认 VM 是 server.

    -cp <目录和 zip/jar 文件的类搜索路径>
    -classpath <目录和 zip/jar 文件的类搜索路径>
                  用 ; 分隔的目录, JAR 档案
                  和 ZIP 档案列表, 用于搜索类文件。
    -D<名称>=<值>
                  设置系统属性
    -verbose:[class|gc|jni]
                  启用详细输出
    -version      输出产品版本并退出
    -version:<值>
                  警告: 此功能已过时, 将在
                  未来发行版中删除。
                  需要指定的版本才能运行
    -showversion  输出产品版本并继续
    -jre-restrict-search | -no-jre-restrict-search
                  警告: 此功能已过时, 将在
                  未来发行版中删除。
                  在版本搜索中包括/排除用户专用 JRE
    -? -help      输出此帮助消息
    -X            输出非标准选项的帮助
    -ea[:<packagename>...|:<classname>]
    -enableassertions[:<packagename>...|:<classname>]
                  按指定的粒度启用断言
    -da[:<packagename>...|:<classname>]
    -disableassertions[:<packagename>...|:<classname>]
                  禁用具有指定粒度的断言
    -esa | -enablesystemassertions
                  启用系统断言
    -dsa | -disablesystemassertions
                  禁用系统断言
    -agentlib:<libname>[=<选项>]
                  加载本机代理库 <libname>, 例如 -agentlib:hprof
                  另请参阅 -agentlib:jdwp=help 和 -agentlib:hprof=help
    -agentpath:<pathname>[=<选项>]
                  按完整路径名加载本机代理库
    -javaagent:<jarpath>[=<选项>]
                  加载 Java 编程语言代理, 请参阅 java.lang.instrument
    -splash:<imagepath>
                  使用指定的图像显示启动屏幕
有关详细信息, 请参阅 http://www.oracle.com/technetwork/java/javase/documentation/index.html。

````
### 安装Android Studio并安装里面的SDK支持
>下载 Android Studio 安装包：http://www.android-studio.org

详细教程 https://www.react-native.cn/docs/environment-setup
跟着上面步骤来选版本！！！！

> 需要安装的SDK大概有  
> SDK Platforms：Android 10 (Q)   
> SDK Platforms：Android SDK Platform 29 
> SDK Platforms：Intel x86 Atom_64 System Image
> SDK Tools： 29.0.2
> SDK Tools NDK： 20.1.5948944

注意：SDK路径尽量不要装在C盘，因为会偶尔出现磁盘空间不足报错的情况


### 三.夜神模拟器配置

> 基本不需要配置什么，只需要打开模拟器，启动项目即可
> 注意，调试环境debugger报错时，先从chrome打开 http://localhost:8081/debugger-ui/
> 再进行服务启动和项目启动
>   先yarn start 启动服务 再打开调试页面 http://localhost:8081/debugger-ui/    最后yarn android  就能看到，你的模拟器已经和项目以及chrome调试器连接在一起了！！！！


### 四.红屏报错
详情见https://blog.csdn.net/m00123456789/article/details/78133534，里面的报错汇总的还是挺多，如找不到，百度谷歌一下吧
