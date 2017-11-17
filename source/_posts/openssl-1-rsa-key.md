---
title: OpenSSL基础教程一：RSA加解密算法密钥
date: 2017-09-07 01:15:21
tags:
    - OpenSSL
categories:
    - Tech
---

#### 一、概述
&#8195;&#8195;1、关于OpenSSL的历史及应用领域，这里不作过多阐述，它是一个开源的安全套接字层密码库，由此你可以大致知道它的用处，想更多的了解，请访问[OpenSSL官方网站][1]及[OpenSSL开源代码库][2]。这里，主要讲解一下OpenSSL在RSA加密情景下的应用，如何生成RSA算法密钥及密钥的相关知识。
&#8195;&#8195;2、RSA，即非对称加解密，加解密原理推荐参考[RSA算法原理（一）][3]及其系列文章。
&#8195;&#8195;3、OpenSSL作为知名的开源软件包，广泛被各大开源系统收录作为系统级软件包，比如主流版本的[Ubuntu][4]、[CentOS][5]等Linux系操作系统，及闭源的[MacOS][6](即苹果操作系统，Unix系)，本文涉及的命令行操作均在Linux环境下进行，所以，基础的Linux操作系统知识是必须的。打开命令行工具，执行 *openssl version -a* 命令，可检测你的操作系统是否具备OpenSSL的执行环境。
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
&#8195;&#8195;这是最基本的生成RSA密钥的命令，其中，密钥保存的文件名可自定义，不限后缀，可以指定文件路径，如 *~/Desktop/private.key* 当然，这个命令还可以加上一些可选参数，如：<!-- more -->
###### *openssl genrsa -aes128 -out private.key 2048*
- *-aes128*，将私钥以AES-128算法保护，另有-aes129，-aes256
- *2048*，指定私钥长度为2048比特，默认是512比特，但512比特长度在现今技术环境下已不够安全，在被攻击的情况下，这个长度的密钥容易被黑客推算还原，可以使用512的整数倍值，1024，2048，4096等，推荐使用2048，这个长度的密钥已经相对安全可靠了。关于这个长度，还涉及到明文的长度问题，后面再作说明。

&#8195;&#8195;让我们看看密钥的内容，其实是一堆文本字符串。
``` bash
$ cat private.key

-----BEGIN RSA PRIVATE KEY-----
MIIBOwIBAAJBALY3hztE11iplu8kIGOixQ9j7fueLEtp4nyIw3RivuSkI5ao7NS9
P78TsH7H6LGJnlN2Ss/FU8BHWKLHwhB/wRECAwEAAQJBALMu+55+3bzkV/Yl8mvI
Hjw6KkYqjqhCIWQRIRMMH2e5kDDstwrNl2/bKA/wqN6blfpENZ7l7IPV/+sJRgBq
irkCIQDaPYuBix+iXO3mueO+FUtjX6M/d8sY44af7M+N7pltvwIhANW+Z8n5QNAC
QOVE4mpYWK8AFQx9wYoSP/zU+w04iCUvAiEAthiiPZ3y8Euv6VNztpgYBju3f+6Z
lRPLsccrS5cpiAsCIBbSzBZfDTKo6vEQV/TvFhkpsxWwX/g0VqzSuTQCM1d1AiA/
O3uwoR4AWrZ5wehhXNNi8yk4l5J8AUpxPVVMkeXYqA==
-----END RSA PRIVATE KEY-----
```
&#8195;&#8195;而其实作为密钥，它所包含的信息远比这一串字符串多得多。
``` bash
$ openssl rsa -text -in private.key

Private-Key: (512 bit)
modulus:
    00:b6:37:87:3b:44:d7:58:a9:96:ef:24:20:63:a2:
    c5:0f:63:ed:fb:9e:2c:4b:69:e2:7c:88:c3:74:62:
    be:e4:a4:23:96:a8:ec:d4:bd:3f:bf:13:b0:7e:c7:
    e8:b1:89:9e:53:76:4a:cf:c5:53:c0:47:58:a2:c7:
    c2:10:7f:c1:11
publicExponent: 65537 (0x10001)
privateExponent:
    00:b3:2e:fb:9e:7e:dd:bc:e4:57:f6:25:f2:6b:c8:
    1e:3c:3a:2a:46:2a:8e:a8:42:21:64:11:21:13:0c:
    1f:67:b9:90:30:ec:b7:0a:cd:97:6f:db:28:0f:f0:
    a8:de:9b:95:fa:44:35:9e:e5:ec:83:d5:ff:eb:09:
    46:00:6a:8a:b9
prime1:
    00:da:3d:8b:81:8b:1f:a2:5c:ed:e6:b9:e3:be:15:
    4b:63:5f:a3:3f:77:cb:18:e3:86:9f:ec:cf:8d:ee:
    99:6d:bf
prime2:
    00:d5:be:67:c9:f9:40:d0:02:40:e5:44:e2:6a:58:
    58:af:00:15:0c:7d:c1:8a:12:3f:fc:d4:fb:0d:38:
    88:25:2f
exponent1:
    00:b6:18:a2:3d:9d:f2:f0:4b:af:e9:53:73:b6:98:
    18:06:3b:b7:7f:ee:99:95:13:cb:b1:c7:2b:4b:97:
    29:88:0b
exponent2:
    16:d2:cc:16:5f:0d:32:a8:ea:f1:10:57:f4:ef:16:
    19:29:b3:15:b0:5f:f8:34:56:ac:d2:b9:34:02:33:
    57:75
coefficient:
    3f:3b:7b:b0:a1:1e:00:5a:b6:79:c1:e8:61:5c:d3:
    62:f3:29:38:97:92:7c:01:4a:71:3d:55:4c:91:e5:
    d8:a8
writing RSA key
-----BEGIN RSA PRIVATE KEY-----
MIIBOwIBAAJBALY3hztE11iplu8kIGOixQ9j7fueLEtp4nyIw3RivuSkI5ao7NS9
P78TsH7H6LGJnlN2Ss/FU8BHWKLHwhB/wRECAwEAAQJBALMu+55+3bzkV/Yl8mvI
Hjw6KkYqjqhCIWQRIRMMH2e5kDDstwrNl2/bKA/wqN6blfpENZ7l7IPV/+sJRgBq
irkCIQDaPYuBix+iXO3mueO+FUtjX6M/d8sY44af7M+N7pltvwIhANW+Z8n5QNAC
QOVE4mpYWK8AFQx9wYoSP/zU+w04iCUvAiEAthiiPZ3y8Euv6VNztpgYBju3f+6Z
lRPLsccrS5cpiAsCIBbSzBZfDTKo6vEQV/TvFhkpsxWwX/g0VqzSuTQCM1d1AiA/
O3uwoR4AWrZ5wehhXNNi8yk4l5J8AUpxPVVMkeXYqA==
-----END RSA PRIVATE KEY-----
```
&#8195;&#8195;这才是它的真实面目，如果你接触过其它加密算法，应该对*modulus*、*exponent*不会感到陌生。
##### 公钥的生成
###### *RSA算法密钥总是成对出现，先有私钥，再用私钥生成公钥*
``` bash
$ openssl rsa -in private.key -pubout -out public.key

writing RSA key
```
&#8195;&#8195;*openssl rsa -in private.key -pubout -out public.key* 这条命令的意思是：指定由(-in)私钥private.key生成公钥(-pubout)，并保存到名为public.key的文件中，参数*-in*及*-pubout*是必须的，而*-out*则跟私钥生成时的意义相同。
&#8195;&#8195;来看一下公钥的内容
``` bash
$ cat public.key

-----BEGIN PUBLIC KEY-----
MFwwDQYJKoZIhvcNAQEBBQADSwAwSAJBALY3hztE11iplu8kIGOixQ9j7fueLEtp
4nyIw3RivuSkI5ao7NS9P78TsH7H6LGJnlN2Ss/FU8BHWKLHwhB/wRECAwEAAQ==
-----END PUBLIC KEY-----
```
&#8195;&#8195;至此，我们已经完整的获取了一对RSA算法密钥，可以使用它们对数据进行加解密了。
&#8195;&#8195;回到之前生成私钥时提到的私钥长度的问题。在RSA算法中，对于一个已经生成的私钥来说，它的长度决定了密文的长度，比如，1024参数生成的密钥加密一段明文数据后，得到的密文长度换算为字节长度是 *1024/8 = 128*，形象一点，是128个英文字母的长度，这是固定的，也就是说，无论你的明文数据长度是多少，用这个密钥加密生成的密文总是也是最大有128个字节那么长，这是由算法本身决定的。显然，当明文数据超过128个字节时，使用这个密钥加密，只有前128字节的数据被加密了，其余的会被舍弃，这种情况下，加密后的密文是无法解密还原为之前的明文的，算法会报错。实际上，RSA算法规定密文需要11字节冗余，因此，最大可加密明文长度应该是 *1024/8 - 11 = 117*，即，明文不能超过117字节。所以，在使用RSA算法时，你需要评估一下你的明文数据，测量明文数据长度，留出冗余度，再决定你需要多长的密钥，从而生成正确的满足需求的密钥对。
&#8195;&#8195;可以意料到，因为算法的复杂，RSA加解密的开销代价是很大的，加解密的耗时，会随着密钥长度的增长及明文长度增长而比例增长，因此，RSA算法更适合用于微量数据的加解密。


[1]: https://www.openssl.org
[2]: https://github.com/openssl/openssl
[3]: http://www.ruanyifeng.com/blog/2013/06/rsa_algorithm_part_one.html
[4]: https://www.ubuntu.com
[5]: https://www.centos.org
[6]: https://www.apple.com/macos/sierra/