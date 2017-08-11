---
title: (译) Kotlin变量 (Android)
date: 2017-08-10 17:31:07
tags: 
    - Kotlin
    - Android
    - Translation
categories: Tech
---
&#8195;&#8195;这篇文章，你将学习到Kotlin变量的相关知识。
&#8195;&#8195;在进入今天的主题之前，在上一篇文章，我已经解释了如何在Android Studio中配置Kotlin开发环境，如果对此你还有疑虑，在学习今天的知识前，请先阅读上一篇文章。
##### *[在Android Studio上配置Kotlin开发环境][1]*
#### 变量的定义
&#8195;&#8195;在Kotlin中，*一切都是对象*
![WTF](1.gif)
>在Kotlin中，一切都是对象。这里没有我们在Java中使用的原始数据类型。这真的是很有意思，因为对于所有的变量，我们都可以使用同样的方式来对待。--[安东尼奥.雷瓦][2]

&#8195;&#8195;是的，这是真的，这是Kotlin非常酷炫的地方，而原因，“安东尼奥.雷瓦”已经说过了。让我们来定义第一个变量。
#### 定义第一个变量
&#8195;&#8195;你可以使用*var*或*val*关键字简单的定义变量并指派给对象。
``` kotlin
var <object_name> : <Type> = <Value>
val <object_name> : <Type> = <Value>
```
##### 例如
``` kotlin
var i : Int = 1
var d : Double = 1.1
var f : Float = 1.1F
var l : Long = 1L
var c : Char = 'c'
var s : String = "Chintan"
```
上边的例子将立即对对象进行赋值，通过例子，你可有什么发现？
没有？
分号！
![Yeah!](2.gif)
你可以更简单一点，就像下边这样
``` kotlin
var i = 1
var d = 1.1
var f = 1.1F
var l = 1L
var c = 'c'
var s = "Chintan"
```
通过赋值，变量

[1]: https://chuyao.github.io/2017/08/10/kotlin-android-tutorial-1/
[2]: https://antonioleiva.com/about/
