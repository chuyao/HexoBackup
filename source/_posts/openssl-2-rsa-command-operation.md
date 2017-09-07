---
title: OpenSSL基础教程二：RSA命令行加解密
tags: OpenSSL
categories: Tech
date: 2017-09-07 16:44:07
---

#### 一、概述
&#8195;&#8195;在上一篇教程中，讲解了如何生成RSA密钥，提到了密钥长度设定对加密过程的影响问题。本篇文章，让我们来使用RSA密钥对数据进行加解密，并验证一下密钥长度对加密的影响，依赖于OpenSSL强大而丰富的命令行命令，可以简洁清晰的实现这两个目标。为了方便演示讲解，本文中使用的密钥是默认的512比特长度。
#### 二、公钥加密
&#8195;&#8195;公钥私钥是成对出现，一个加密，另一个解密。当然，数据也可以由私钥加密，由公钥解密。所谓公钥，即对外公开的，公钥由私钥生成而来，知道私钥即可知道公钥，在RSA的设计设想中，这是一条单向线，因此，要自己保护好私钥，把公钥公开，一般情况下，公钥持有者用公钥把明文数据加密成密文，将密文发送给私钥持有者，私钥持有者用私钥对密文解密得到明文数据，完成加解密流程。本文的演示流程也将按照这个来进行。
&#8195;&#8195;新建一个空白文档文件 *data.txt*，用文本编辑器编辑文本内容，输入 *Hello RSA* 并保存，作为我们的明文数据。
&#8195;&#8195;公钥加密，命令行命令 
``` bash
$ openssl rsautl -encrypt -in data.txt -inkey public.key -pubin -out data_en.txt
```
- 意思是：RSA工具(rsautl)加密操作(-encrypt)，导入(-in)明文数据data.txt，导入密钥(-inkey)，声明密钥是公钥(-pubin)，加密后密文输出保存到(-out)data_en.txt文件中。
- 加密时，OpenSSL会默认导入的密钥是私钥，所以，公钥加密需要加上 *-pubin* 参数以表明加密操作是以公钥进行，私钥加密时因为是默认私钥，所以不需要加相关参数。一定要确认使用的是哪个密钥加密，如果使用公钥而又不加 *-pubin* 参数，命令行会报错，加密也会失败。

&#8195;&#8195;命令行无错误提示，即表明加密成功，来看看密文文件 *data_en.txt* 的内容：
``` bash
$ cat data_en.txt
�W��
����	u+�E�=J�w��	���� �n(W˯f�g'n�<grHY����w�=jI�)M�.i
```
&#8195;&#8195;我当然看不懂了！<!-- more -->
&#8195;&#8195;同样的加密操作我们再来一次，看看两次加密得到的密文是否一样。
``` bash
$ openssl rsautl -encrypt -in data.txt -inkey public.key -pubin -out data_en.txt
$ cat data_en.txt
��ީ�q�%EM����vBe)P~�����ϙ��ZԱ[ޥb�9~����Ө|�=�R��c�[��
```
&#8195;&#8195;我当然依然看不懂了，但明显，两次加密生成密文是不一样的，这也是RSA加密算法的重点优势体现，密文是动态的，安全性得到了提升。
#### 三、私钥解密
&#8195;&#8195;前面我们已经得到了密文数据文件 *data_en.txt*，我们来使用私钥进行解密还原。命令行命令
``` bash
$ openssl rsautl -decrypt -in data_en.txt -inkey private.key -out data_de.txt
```
- 意思应该已经很好理解了：RSA工具解密操作(-decrypt)，导入密文数据文件data_en.txt，导入私钥private.key，默认密钥为私钥，解密后明文数据输出保存到 data_de.txt文件中。

&#8195;&#8195;命令行无错误提示，即表明解密成功，来看看明文文件 *data_de.txt* 的内容：
``` bash
$ cat data_de.txt
Hello RSA
```
&#8195;&#8195;好了，是不是很有成就感？！
#### 四、密钥长度问题验证
&#8195;&#8195;先来看看我们经过加解密过程得到的三个文件的大小
``` bash
$ ll data.txt
-rw-r--r-- 1 user 197121 10 Sep   7 15:20 data.txt
$ ll data_en.txt
-rw-r--r-- 1 user 197121 64 Sep   7 15:20 data_en.txt
$ ll data_de.txt
-rw-r--r-- 1 user 197121 10 Sep   7 15:21 data_de.txt
```
&#8195;&#8195;data.txt是10个字节，data_en.txt是64个字节，还原的的data_de.txt是10个字节，符合我们下面进行的公式计算。
&#8195;&#8195;以512比特长度的密钥用公式计算，*512/8 = 64*，即经过这个密钥加密后的密文长度(亦或大小)固定是64个字节，可加密的最大明文数据大小为 *512/8 - 11 = 53* 个字节，一个英文字母即一个字节。我们来验证一下，编辑data.txt，把 *Hello RSA* 替换为 *abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ*，保存后可以查看data.txt的大小，刚好53个字节。
``` bash
$ ll data.txt
-rw-r--r-- 1 user 197121 53 Sep   7 15:32 data.txt
```
&#8195;&#8195;对这个文件执行公钥加密操作，可以看到，是成功的，我们再来编辑这个文件，随意插入一个字母，保存，data.txt大小将变为54字节，再进行一次公钥加密操作
``` bash
$ openssl rsautl -encrypt -in data.txt -inkey public.key -pubin -out data_en.txt
RSA operation error
139970621331096:error:0406D06E:rsa routines:RSA_padding_add_PKCS1_type_2:data too large for key size:rsa_pk1.c:153:
```
&#8195;&#8195;可见，加密失败，因为明文数据长度超过53字节了。要想对这么长的数据进行RSA加密，我们需要一个更大容量的密钥，留个作业，动手去生成一个1024比特长度密钥，来加密一个54字节长度的明文数据，验证一下，可以加深你对这个问题的理解。