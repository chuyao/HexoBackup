---
title: Kotlin基础教程第一章：在Android Studio中配置Kotlin环境
date: 2017-08-10 15:36:15
tags: 
    - Kotlin
    - Android
categories:
    - IT
---
&#8195;&#8195;如果你之前了解过Kotlin，认为它是一门很强大的语言，那么你应该尝试去学习和使用它，这就是你来到这里的原因。这篇文章，我们将学习如何配置Android Studio下的Kotlin开发环境。
&#8195;&#8195;启动Android Studio，新建一个项目工程，如下图如示
![新工程 + Kotlin支持(需要手动勾选)](1.png)
&#8195;&#8195;按照下一步提示创建工程并等待创建过程完成。

&#8195;&#8195;*对于Android Studio 2.x版本，你需要预先安装Kotlin插件，安装步骤为“File -> Settings -> Plugin”，在弹出的对话框搜索栏内搜索“Kotlin”，安装并重启你的Android Studio。*
![2.x版本kotlin插件安装](1_1.png)

&#8195;&#8195;先让我们看一下新建工程的*gradle*文件。
![工程根目录build.gradle](2.png)
1. Kotlin依赖版本声明；(这篇文章编写时，版本号为1.1.4)<!-- more -->
2. Kotlin依赖插件声明。

*阿里云maven镜像声明*
``` groovy
maven{ url 'http://maven.aliyun.com/nexus/content/groups/public/'}  //使用阿里云镜像，可以加快gradle或kolin插件的更新速度
```

&#8195;&#8195;接着来看主模块的*gradle*文件。
![主模块目录build.gradle](3.png)
1. 插件应用于该模块；
2. Kotlin标准库。你可以从[Kotlin官网][1]获取更多相关信息。

&#8195;&#8195;你应该已经注意到，当Kotlin类创建时，类文件的后缀名默认已经变成“.kt”。
![MainActivity.kt](4.png)
1. 所有的实例对象以冒号“:”和类的默认构造器形式展现。
2. 所有的重写方法以*override*关键字开头。
3. 你需要在实例对象后面加一个问号“*?*”来声明它是一个对象。

&#8195;&#8195;现在，像以往一样运行你的应用。
![输出HelloKotlin](5.png)

[1]: https://kotlinlang.org/api/latest/jvm/stdlib/