---
title: 在U盘上建立git仓库，移动的“私有云”
date: 2017-11-17 14:35:23
tags:
    - Git
categories: Tech
---
#### 一、前言
Git作为版本管理工具，其功能之强大，已无需赘述。一般情况下，我们接触到的git都指远程操作，与远程git服务器协作，完成版本迭代管理。如果没有服务器，是否也能使用git呢？当然可以，这期文章，让我们一起来把git和我们的代码搬到U盘上，建立一个真正属于自己而又移动的“私有云”。
#### 二、环境搭建
1、安装好的git环境，参见[Git官网][1]。
2、U盘一个，大小容量没有严格要求。

#### 三、命令行操作
1、在U盘上创建空仓库test.git(我的U盘盘符在PC端是I盘)。

``` bash
$ cd /I
$ mkdir test
$ cd test
$ git init --bare 
```
得到如下显示即表明git仓库创建成功
``` bash
Initialized empty Git repository in I:/test/
```

2、现有git工程与U盘仓库关联(在git工程根目录下执行)

``` bash
$ git remote add usb /i/test
```

3、版本管理，仓库有了，剩下就是推送和拉取文件了

``` bash
$ git push usb master
$ git pull usb master
```


[1]: https://git-scm.com/