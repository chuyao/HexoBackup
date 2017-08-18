---
title: Kotlin基础教程第四章：Kotlin类 (Android)
date: 2017-08-18 15:54:36
tags: 
    - Kotlin
    - Android
categories: Tech
---

&#8195;&#8195;本篇文章，让我们来学习Kotlin类及其属性。
&#8195;&#8195;欢迎你回头学习之前的文章，可以让你更好的继续学习Kotlin知识。
#### 类
&#8195;&#8195;如果你曾学习过任何一门“面向对象编程”语言，你将对类及其属性很熟悉。
>一个类可以比作模板或蓝图，用来创建不同的对象，并定义对象的属性及行为。

在Java中，要创建一个类，需要定义一个类，定义它的构造器、它的*getter*和*setter*方法，通过这些方式，简单的给成员变量赋值或取出它们的值。这些乏味的工作不会出现在Kotlin中。
##### *Java*
``` java
public class Person {
    private String name;
    public Person(String name) {
        this.name = name;
    }
    public String getName() {
        return this.name;
    }
}
```
##### *Kotlin*
``` kotlin
class Person(val name: String)
```
&#8195;&#8195;怎么样？是不是很简洁明了？Kotlin一行代码即可实现Java需要九行代码才能实现的功能。写这样的代码，岂能不感叹“*人生苦短，快用Kotlin！*”
&#8195;&#8195;你应该已经注意到了，类的前边没有*public*关键字，是因为在Kotlin中，所有的类默认都是*public*的，所以可以丢掉了。
#### 属性
&#8195;&#8195;在定义的类中，一般含有一些成员变量和方法，通常，这些数据都是私有的，不能直接访问，普遍的做法是通过创建*getter*方法来获取这些数据。在所有的“*面向对象编程*”语言中，这些做法的结合，通常称为“*封装*”。在Kotlin中，赋值和取值方法有很大的不同。
&#8195;&#8195;声明一个属性有两种方式，如果是以 *val* 声明，则这个属性是只读的，而如果是以 *var* 声明，则这个属性是可变的，你可以在任何时刻修改它。
``` kotlin
class Person (
    val name : String,  // 只读，产生成员变量及getter
    var age : Int   // 可变的，产生成员变量，getter及setter
)
```
&#8195;&#8195;任何时候，你想声明一个属性，就会产生一个成员变量，一个getter或setter(取决于如何声明)。下边的例子，你可以看到如何创建一个Person实例对象，并访问它的属性。<!-- more -->
``` kotlin
var person = Person("Allen Shi", 18)
println(person.name)    //输出-> Allen Shi
println(person.age)     //输出-> 18
```
#### 自定义访问器
&#8195;&#8195;设想一下，你定义了一个属性并想要通过自己的逻辑来返回结果。通过自定义访问器即可实现。在本文的例子中，我们想要知道某个人是否成年，我们不需要在类中存储任何附加的属性就可简单的实现。
``` kotlin
class Person(
    val name : String,
    var age : Int
) {
    val isAdult : Boolean
    get() {
        return age > 18
    }
}
```
&#8195;&#8195;在这个方法里，我们定义了一个isAdult属性，通过检查age值来决定isAdult的返回值。注意，你需要将方法用val关键字来声明，否则会报错。
``` kotlin
var person1 = Person("Allen", 20)
println(person1.isAdult)    //输出-> true
var person2 = Person("Eva", 18)
println(person2.isAdult)    //输出-> false
```
#### 总结
&#8195;&#8195;本文，我们学习了如何声明一个类及其属性，收获了在Kotlin中的getter和setter属性，现在，你也可以声明自己的属性方法，使用自己的逻辑来返回你需要的结果了。