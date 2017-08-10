---
title: (译) Kotlin基础教程第三章：Kotlin运算符 (Android)
date: 2017-08-10 21:55:47
tags: 
    - Kotlin
    - Android
    - Translation
categories: Tech
---
&#8195;&#8195;在这篇文章里，你将学习到运算符知识及它们在Kotlin中的运用。
&#8195;&#8195;但是在进入正题之前，我已经在之前的文章里解释了如何在Android Studio中配置Kotlin开发环境及Kotlin语言变量。如果你还有不清楚的地方，请先阅读之前的文章再来进行这篇文章知识的学习。
##### [第一章：在Android Studio中配置Kotlin环境][1]
##### [第二章：Kotlin变量 (Android)][2]
#### 二进制运算符
&#8195;&#8195;在运算符的使用上，Kotlin是一门强大的语言。在其它计算机语言如Java中，是不允许用户在非原始类型数据间使用算术运算符的。你想对ArrayList使用“*+*”，是不允许的。但Kotlin可以，Kotlin提供了二进制运算符相对应的可重载的方法名。

| 表达式   | 方法                       |
| :------- | :-------------------------|
| a + b   | a.plus(b)                 |
| a - b   | a.minus(b)                |
| a * b   | a.times(b)                |
| a / b   | a.div(b)                  |
| a % b   | a.rem(b), a.mod(b)(过时的) |
| a..b    | a.rangeTo(b)              |
##### 注意
&#8195;&#8195;如果你正在使用的Kotlin是1.1版本，请使用*rem()*方法，*mod()*方法从1.1版本开始已经过时了。


[1]: https://chuyao.github.io/2017/08/10/kotlin-android-tutorial-1/
[2]: https://chuyao.github.io/2017/08/10/kotlin-android-tutorial-2/
