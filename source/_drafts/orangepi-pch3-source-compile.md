---
title: OrangePi-PCH3安卓源码编译
tags: Android
categories: Tech
---
#### 一、源码下载
[官方源码][1]
下载的源码文件是分块的压缩包，需要合并再解压
linux环境合并解压
``` bash
$ cat xxx_1 xx_2 > xx.tar.gz
```
archive菜单直接解压xx.tar.gz

#### 二、编译环境准备(以ubuntu1604为例)
1、python2.7.3
2、GNU Make 3.81-3.82(ubuntu1604自带make版本4.1，需要重新安装)
下载[3.81版本make][2]，解压后得到deb包
``` bash
$ sudo apt-get remove make
$ sudo dpkg -i xxx.deb
```
3、JDK安装，只支持jdk1.6
4、平台支持软件安装
``` bash
$ sudo apt-get install git gnupg flex bison gperf build-essential zip curl libc6-dev libncurses5-dev:i386 x11proto-core-dev libx11-dev:i386 libreadline6-dev:i386 libgl1-mesa-glx:i386 libgl1-mesa-dev g++-multilib mingw32 tofrodos python-markdown libxml2-utils xsltproc zlib1g-dev:i386
$ sudo ln -s /usr/lib/i386-linux-gnu/mesa/libGL.so.1 /usr/lib/i386-linux-gnu/libGL.so
$ sudo dpkg-reconfigure dash
$ sudo apt-get install gawk
$ sudo apt-get install u-boot-tools
$ sudo apt-get install fakeroot
```
5、lichee编译(kernel)
``` bash
$ cd lichee
$ ./build.sh lunch
```
选择sun8iw7p1-android-dolphin
6、源码编译
``` bash
$ cd android
$ source ./build/envsetup.sh
$ lunch dolphin_fvd_p1-eng
$ extract-bsp
$ make -j2
$ pack
```

[1]: http://www.orangepi.cn/downloadresourcescn/orangepipc/oragepipc_e3edd0dd47da54c0b8f7aa2230.html
[2]: http://mirrors.ustc.edu.cn/gnu/make/