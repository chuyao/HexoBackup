---
title: Kotlin基础教程第三章：Kotlin运算符 (Android)
date: 2017-08-15 21:55:47
tags: 
    - Kotlin
    - Android
categories:
    - Tech
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
&#8195;&#8195;如你所见，每一个二进制运算符都有一个方法让它更易读。当你想对自定义的类使用运算方法时，你会感觉很容易使用以及重载。
``` kotlin
data class Test(val count: Int) {
    operator fun plus(increment: Int): Test {
        return Test(count + increment)
    }
    operator fun times(multiply: Int): Test {
        return Test(count + multiply)
    }
}

val test = Test(10)
println(test + 10)  //输出 -> Test(count=20)
println(test * 2)   //输出 -> Test(count=12)
```
<!-- more -->
阴吹斯汀！
#### 一元运算
&#8195;&#8195;在Java或其它语言中，你一定很熟悉一元运算符。在Kotlin中，只要你愿意，你也可以在自定义类中使用和重载它们。

| 表达式   | 方法                |
| :------- | :------------------|
| +a   | a.unaryPlus()          |
| -a   | a.unaryMinus()         |
| !a   | a.not()                |

``` kotlin
data class Test(val count: Int)

operator fun Test.unaryMinus() = Test(-count)

val test = Test(10)
println(-test)       //输出 -> Test(count=-10)
```
&#8195;&#8195;可以看到，一元方法是没有参数的。当*-test*被调用时，它会检查*unaryMinus()*是否已经被重载，如果是，就会返回适当的结果。
#### 自增和自减
&#8195;&#8195;没有这个运算符，你的循环是不完整的。是的，*++*和*--*是非常有用的运算符，接着看表和重载方法

| 表达式   | 方法                |
| :------- | :------------------|
| a++   | a.inc()         |
| a--   | a.dec()         |
``` kotlin
operator fun BigDecimal.inc() = this + BigDecimal.ONE
var bigDec = BigDecimal.ZERO
println(bigDec++)  //输出 -> 0
println(++bigDec)  //输出 -> 2
```
#### 赋值运算符
&#8195;&#8195;使用赋值运算符，你通过操作二进制运算符来改变对象的值。当使用简单的二进制运算符时，对象的值不会被改变。

| 表达式   | 方法                       |
| :------- | :-------------------------|
| a += b   | a.plusAssign(b)                 |
| a -= b   | a.minusAssign(b)                |
| a *= b   | a.timesAssign(b)                |
| a /= b   | a.divAssign(b)                  |
| a %= b   | a.modAssign(b)                  |
``` kotlin
val mutableCollection = mutableListOf(1, 2, 3)
val iterable = listOf(4, 5)

mutableCollection.plusAssign(iterable)
println(mutableCollection)  //输出 -> [1, 2, 3, 4, 5]

mutableCollection += 6
println(mutableCollection)  //输出 -> [1, 2, 3, 4, 5, 6]
```
#### 其它运算符
&#8195;&#8195;还有许多其它的运算符可以使用

| 表达式   | 方法                       |
| :------- | :-------------------------|
| a in b   | b.contains(a)                 |
| a !in b   | !b.contains(a)                |
| a[i]  | a.get(i)                |
| a[i, j]   | a.get(i, j)                 |
| a[i_1, ..., i_n]   | a.get(i_1, ..., i_n) |
| a[i] = b   | a.set(i, b)              |
| a[i, j] = b   | a.set(i, j, b)              |
| a[i_1, ..., i_n] = b   | a.set(i_1, ..., i_n, b)              |
| a == b   | a?.equals(b) ?: (b === null)              |
| a != b   | !(a?.equals(b) ?: (b === null))              |
| a()   | a.invoke()              |
| a(i)   | a.invoke(i)              |
| a(i, j)   | a.invoke(i, j)              |
| a(i_1, ..., i_n)   | a.invoke(i_1, ..., i_n)              |
| a > b   | a.compareTo(b) > 0             |
| a < b   | a.compareTo(b) < 0              |
| a >= b   | a.compareTo(b) >= 0              |
| a <= b   | a.compareTo(b) <= 0              |

&#8195;&#8195;尝试在你自己的例子中使用上面的运算符，分享一下你的经历。
#### 总结
&#8195;&#8195;在本文中，你已经学习了如何在原始类型数据或自定义类之间使用运算符并重载相应的方法。


[1]: https://chuyao.github.io/2017/08/10/kotlin-android-tutorial-1/
[2]: https://chuyao.github.io/2017/08/13/kotlin-android-tutorial-2/
