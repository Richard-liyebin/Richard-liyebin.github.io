---
layout:     post
title:      ""
subtitle:   ""
date:        2020-03-23
author:     "Lyb"
header-img: "img/post-bg-unix-linux.jpg"
tags:
    - 前端开发
    - 
---

## android 打包流程

Android 要求所有应用都有一个数字签名才会被允许安装在用户手机上，所以在把应用发布到应用市场之前，你需要先生成一个签名的 AAB 或 APK 包（Google Play 现在要求 AAB 格式，而国内的应用市场目前仅支持 APK 格式。

注意：在打包之前先关注你的 RN 版本，0.6+和0.5+是有区别的，配置也不同，请根据实际项目来看。本文档根据RN 0.6+ 来进行android打包流程的介绍

### 1.生成签名密钥

可以用keytool命令生成一个私有密钥。在 Windows 上keytool命令放在 JDK 的 bin 目录中（比如C:\Program Files\Java\jdkx.x.x_x\bin），你可能需要在命令行中先进入那个目录才能执行此命令。
找到你的Java中的jdk路径，进入到bin文件夹，才此处开启cmd管理员模式，记住是管理员模式，因为大多数人的jdk默认路径在C盘，如果不开启管理员模式会因为无法读写c盘文件的权限而出错！

 C:\Program Files\Java\jdk1.8.0_291\bin（具体路径以自己的为准）下执行cmd

>  keytool -genkeypair -v -storetype PKCS12 -keystore my-release-key.keystore -alias my-key-alias -keyalg RSA -keysize 2048 -validity 1000

>注意记住你的密钥库口令和-alias 后的 my-key-alias这个别名，到时候配置需要用到

````
输入密钥库口令:
再次输入新口令:
您的名字与姓氏是什么?
  [Unknown]:  liyebin
您的组织单位名称是什么?
  [Unknown]:  py
您的组织名称是什么?
  [Unknown]:  py
您所在的城市或区域名称是什么?
  [Unknown]:  cdc
您所在的省/市/自治区名称是什么?
  [Unknown]:  sc
该单位的双字母国家/地区代码是什么?
  [Unknown]:  China
CN=liyebin, OU=py, O=py, L=cdc, ST=sc, C=China是否正确?
  [否]:  v
您的名字与姓氏是什么?
  [liyebin]:  liyebin
您的组织单位名称是什么?
  [py]:  py
您的组织名称是什么?
  [py]:  py
您所在的城市或区域名称是什么?
  [cdc]:  cdc
您所在的省/市/自治区名称是什么?
  [sc]:  sc
该单位的双字母国家/地区代码是什么?
  [China]:  China
CN=liyebin, OU=py, O=py, L=cdc, ST=sc, C=China是否正确?
  [否]:  是

正在为以下对象生成 2,048 位RSA密钥对和自签名证书 (SHA256withRSA) (有效期为 1,000 天):
         CN=liyebin, OU=py, O=py, L=cdc, ST=sc, C=China
[正在存储my-release-key.keystore]

这就表示生成成功

在运行上面这条语句之后，密钥库里应该已经生成了一个单独的密钥，有效期为 10000 天。--alias 参数后面的别名是你将来为应用签名时所需要用到的，所以记得记录这个别名。

最后它会生成一个叫做my-release-key.keystore的密钥库文件!!!!(在bin文件夹下)

````
> 需要记住的是你的口令，也就是你自己输入的密码，还有 -alias 后的 my-key-alias这个别名

### 2.设置 gradle 变量

> 把my-release-key.keystore文件放到你工程中的android/app文件夹下。
编辑~/.gradle/gradle.properties（全局配置，对所有项目有效）或是项目目录/android/gradle.properties（项目配置，只对所在项目有效）。如果没有gradle.properties文件你就自己创建一个，添加如下的代码（注意把其中的****替换为相应密码）

````
MYAPP_RELEASE_STORE_FILE=my-release-key.keystore
MYAPP_RELEASE_KEY_ALIAS=my-key-alias //这里是你的别名
MYAPP_RELEASE_STORE_PASSWORD=*****  //这里是你的密钥口令
MYAPP_RELEASE_KEY_PASSWORD=*****    //这里是你的密钥口令

记得替换!!!
````

### 3.把签名配置加入到项目的 gradle 配置中

>编辑你项目目录下的android/app/build.gradle，添加如下的签名配置：

````
...
android {
    ...
    defaultConfig { ... }
    signingConfigs {
        release {
            if (project.hasProperty('MYAPP_RELEASE_STORE_FILE')) {
                storeFile file(MYAPP_RELEASE_STORE_FILE)
                storePassword MYAPP_RELEASE_STORE_PASSWORD
                keyAlias MYAPP_RELEASE_KEY_ALIAS
                keyPassword MYAPP_RELEASE_KEY_PASSWORD
            }
        }
    }
    buildTypes {
        release {
            ...
            signingConfig signingConfigs.release
        }
    }
}
...
````

### 4.生成发行 APK 包

> 进入到我们项目的的android文件夹下（如果本来就在就不需要）

> powershell中执行 ./gradlew assembleRelease 或 cmd中执行 gradlew assembleRelease

注意：请确保 gradle.properties 中没有包含_org.gradle.configureondemand=true_，否则会跳过 js 打包的步骤，导致最终生成的是一个无法运行的空壳。

生成的 APK 文件位于android/app/build/outputs/apk/release/app-release.apk，它已经可以用来发布了！！！


### 5.测试应用的发行版本

>直接在项目目录下执行 npx react-native run-android --variant=release

注意--variant=release参数只能在你完成了上面的签名配置之后才可以使用。你现在可以关掉运行中的 packager 了，因为你所有的代码和框架依赖已经都被打包到 apk 包中，可以离线运行了。

在夜神模拟器上就会打包一个新的app，不需要开启server，和其他的，都能正常执行了，这就完成了基本的android打包操作