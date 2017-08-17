---
title: Kotlin基础教程第二章：Kotlin变量 (Android)
date: 2017-08-13 17:31:07
tags: 
    - Kotlin
    - Android
categories: Tech
---
&#8195;&#8195;这篇文章，你将学习到Kotlin变量的相关知识。
&#8195;&#8195;在进入今天的主题之前，在上一篇文章，我已经解释了如何在Android Studio中配置Kotlin开发环境，如果对此你还有疑虑，在学习今天的知识前，请先阅读上一篇文章。
##### *[在Android Studio上配置Kotlin开发环境][1]*
#### 变量的定义
&#8195;&#8195;在Kotlin中，*一切都是对象*
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
var s : String = "Allen"
```
&#8195;&#8195;上边的例子将立即对对象进行赋值，通过例子，你可有什么发现？<!-- more -->
&#8195;&#8195;没有？
&#8195;&#8195;分号！
&#8195;&#8195;你可以更简单一点，就像下边这样
``` kotlin
var i = 1
var d = 1.1
var f = 1.1F
var l = 1L
var c = 'c'
var s = "Allen"
```
&#8195;&#8195;通过不同的赋值，变量将被创建为特殊的某一类型。很有趣，是吗！
&#8195;&#8195;下边表格列出的是你定义的对象类型在内存中的占用情况(比特位数)

![类型位宽](3.png)
&#8195;&#8195;你也可以用任何一个已定义的变量并把它赋值给一个新的变量来创建一个对象。
``` kotlin
var ii = i + 1
var dd = d + 2.0
var ff = f + 1
var ll = l + 1
var ss = s + " Shi"

println("ii : $ii, dd : $dd, ff : $ff, ll : $ll, ss : $ss")
```
##### 输出
``` kotlin
ii : 2
dd : 3.1
ff : 2.1
ll : 2
ss : Allen Shi
```
#### 常量
&#8195;&#8195;在Kotlin中，*var*变量很常见，它是可变的，可以被多次赋值。而*val*则指常量，即，它只能被初始化一次。
``` kotlin
var mutable : Int = 5
val immutable : Int = 5
mutable = 10    //合法
immutable = 10  //非法
```
&#8195;&#8195;在Java中，我们常不知不觉使用可变量实例，这让我们经常面对对象在多个地方修改带来的许多问题。当我们创建一个不可变对象时，它可以一直保持它原有的状态，如果我们想要改变它，则需要创建另外一个对象。
&#8195;&#8195;在使用Kotlin开发应用时，建议尽量多使用*val*变量。它们不受当前线程影响，因而它们是线程安全的。
#### 字符串
&#8195;&#8195;这对Kotlin来说太简单了。
``` kotlin
var s = "Allen"
var ss = "My name is $s"  // My name is Allen
var c = s[2]              // c将赋值为字符'i'
```
&#8195;&#8195;使用*$*(美元符号)，可以引用一个对象的值。你也可以把一个字符串看待成一个数组，通过给某一个数组元素赋值来改变这个对象。
#### 安全的空指针
&#8195;&#8195;在以前的文章里，我说过Kotlin是空指针安全的。原因是Kotlin不允许用户将对象赋值*NULL*，除非你告诉Kotlin某个对象可能是空的才允许你那么做。你可以在类型后面加一个*?*(问号)来实现。
``` kotlin
var s : String = "Allen"
s = null //异常

var s : String? = "Allen"
s = null //正确
```
#### 类型转换
&#8195;&#8195;和Java不同，Kotlin没有自动类型转换，你需要自己声明你需要的转换类型。
``` kotlin
val i : Int = 1
val d : Double = i              //不可以
val d : Double = i.toDouble()   //可以
```
#### 总结
&#8195;&#8195;在本文中，你将学习到如何定义不同类型的变量，*var*和*val*关键字的区别，如何从一个类型变量转换到另一个类型的变量。

[1]: https://chuyao.github.io/2017/08/10/kotlin-android-tutorial-1/
[2]: https://antonioleiva.com/about/
