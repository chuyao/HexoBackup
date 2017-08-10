---
title: Kotlin基础教程第一章：在Android Studio上配置Kotlin开发环境
date: 2017-08-10 15:36:15
tags: 
    - Kotlin
    - Android
categories: Tech
---
&#8195;&#8195;如果你之前了解过Kotlin，认为它是一门很强大的语言，那么你应该尝试去学习和使用它，这就是你来到这里的原因。这篇文章，我们将学习如何配置Android Studio下的Kotlin开发环境。
&#8195;&#8195;启动Android Studio，新建一个项目工程，如下图如示
![新工程 + Kotlin支持](1.png)
&#8195;&#8195;按照下一步提示创建工程并等待创建过程完成。

&#8195;&#8195;*对于Android Studio 2.x版本，你需要预先安装Kotlin插件，安装步骤为“File -> Settings -> Plugin”，在弹出的对话框搜索栏内搜索“Kotlin”，安装并重启你的Android Studio。*

&#8195;&#8195;先让我们看一下新建工程的*gradle*文件。
![工程根目录build.gradle](2.png)
1. Kotlin依赖版本声明。(这篇文章编写时，版本号为1.1.3-2)
2. Kotlin依赖插件声明。

&#8195;&#8195;接着来看主模块的*gradle*文件。
![主模块目录build.gradle](3.png)
1. 插件应用于该模块。
2. Kotlin标准库。你可以从[Kotlin官网][1]获取更多相关信息。

&#8195;&#8195;你应该已经注意到，当Kotlin类创建时，类文件的后缀名默认已经变成“.kt”。
![MainActivity.kt](4.png)
1. 所有的实例对象以冒号“:”和类的默认构造器形式展现。
2. 所有的重载方法以*override*关键字开头。
3. 你需要在实例对象后面加一个问号“*?*”来声明它是一个对象。

&#8195;&#8195;现在，像以往一样运行你的应用。
![输出HelloKotlin](5.png)

### 原文出自[Chapter 1 : Configuring Android Studio with Kotlin][2]

[1]: https://kotlinlang.org/api/latest/jvm/stdlib/
[2]: http://chintanrathod.com/chapter-1-configuring-android-studio-kotlin/