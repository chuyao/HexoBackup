---
title: OpenSSL基础教程一：RSA加解密算法密钥
tags: OpenSSL
categories: Tech
---
#### 一、概述
&#8195;&#8195;1、关于OpenSSL的历史及应用领域，这里不作过多阐述，它是一个开源的安全套接字层密码库，由此你可以大致知道它的用处，想更多的了解，请访问[OpenSSL官方网站][1]及[OpenSSL开源代码库][2]。这里，主要讲解一下OpenSSL在RSA加密情景下的应用，如何生成RSA算法密钥及密钥的相关知识。
&#8195;&#8195;2、RSA，即非对称加解密，加解密原理推荐参考[RSA算法原理（一）][3]及其系列文章。
&#8195;&#8195;3、OpenSSL作为知名的开源软件包，广泛被各大开源系统收录作为系统级软件包，比如主流版本的[Ubuntu][4]、[CentOS][5]等操作系统，及闭源的[MacOS][6](即苹果操作系统)，本文涉及的命令行操作均在Linux环境下进行，所以，基础的Linux操作系统知识是必须的。打开命令行工具，执行 *openssl version -a* 命令，可检测你的操作系统是否具备OpenSSL的执行环境。
``` bash
$ openssl version -a

OpenSSL 0.9.8zh 14 Jan 2016
built on: Jan 23 2017
platform: darwin64-x86_64-llvm
options:  bn(64,64) md2(int) rc4(ptr,char) des(idx,cisc,16,int) blowfish(idx) 
compiler: -arch x86_64 -fmessage-length=0 -pipe -Wno-trigraphs -fpascal-strings -fasm-blocks -O3 -D_REENTRANT -DDSO_DLFCN -DHAVE_DLFCN_H -DL_ENDIAN -DMD32_REG_T=int -DOPENSSL_NO_IDEA -DOPENSSL_PIC -DOPENSSL_THREADS -DZLIB -mmacosx-version-min=10.6
OPENSSLDIR: "/System/Library/OpenSSL"
```
&#8195;&#8195;以上显示即正常。
#### 二、OpenSSL生成RSA密钥对
##### 私钥的生成
``` bash
$ openssl genrsa -out private.key

Generating RSA private key, 512 bit long modulus
.......++++++++++++
.....++++++++++++
e is 65537 (0x10001)
```
&#8195;&#8195;*openssl genrsa -out private.key* 这条命令的意思是：生成一个RSA算法私钥(genrsa)，保存到(-out)名为private.key的文件中。
&#8195;&#8195;这是最基本的生成RSA密钥的命令，其中，密钥保存的文件名可自定义，不限后缀，可以指定文件路径，如 *~/Desktop/private.key* 当然，这个命令还可以加上一些可选参数，如：
###### *openssl genrsa -aes128 -out private.key 2048*
- *-aes128*，将私钥以AES-128算法保护，另有-aes129，-aes256
- *2048*，指定私钥长度为2048比特，默认是512比特，但512比特长度在现今技术环境下已不够安全，在被攻击的情况下，这个长度的密钥容易被黑客推算还原，可以使用512的整数倍值，1024，2048，4096等，推荐使用2048，这个长度的密钥已经相对安全可靠了。关于这个长度，还涉及到明文的长度问题，后面再作说明。


[1]: https://www.openssl.org
[2]: https://github.com/openssl/openssl
[3]: http://www.ruanyifeng.com/blog/2013/06/rsa_algorithm_part_one.html
[4]: www.ubuntu.com
[5]: https://www.centos.org
[6]: https://www.apple.com/macos/sierra/