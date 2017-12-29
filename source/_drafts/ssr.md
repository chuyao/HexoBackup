---
title: 梯子，你懂的！
tags: ssr
categories: Tech
---
#### 一、境外服务器申请
有许多选择，任选下列其一即可，申请后的服务器请安装Linux系操作系统，如Ubuntu, Debian, CentOS
- [VULTR][1] *推荐，目前比较便宜，支持支付宝支付，文末将示范申请过程*
- [DIGITALOCEAN][2] *大牌厂商*
- [LINODE][3]
- [AZURE][4] *微软的云服务*

#### 二、部署SSR
服务申请并安装好系统后，使用终端连接到服务器
``` bash
$ wget --no-check-certificate -O shadowsocks-all.sh https://raw.githubusercontent.com/teddysun/shadowsocks_install/master/shadowsocks-all.sh
$ chmod +x shadowsocks-all.sh
$ ./shadowsocks-all.sh 2>&1 | tee shadowsocks-all.log
```
第三个命令执行时出现选项操作
1. 选择选项2，即输入2
2. 按提示输入一个密码，新密码，非系统登录密码
3. 按提示输入一个端口，范围1~65535，建议选择20000以上
4. 选择选项12，即chacha20
5. 选择选项3，即auth_sha1_v4
6. 选择选项2，即http_simple

大致过程如下：

``` bash
Which Shadowsocks server you'd select:
1) Shadowsocks-Python
2) ShadowsocksR
3) Shadowsocks-Go
4) Shadowsocks-libev
Please enter a number (Default Shadowsocks-Python):2

You choose = ShadowsocksR

Please enter password for ShadowsocksR
(Default password: teddysun.com):ssr2017

password = ssr2017

Please enter a port for ShadowsocksR [1-65535]
(Default port: 8989):20002

port = 20002

Please select stream cipher for ShadowsocksR:
1) none
2) aes-256-cfb
3) aes-192-cfb
4) aes-128-cfb
5) aes-256-cfb8
6) aes-192-cfb8
7) aes-128-cfb8
8) aes-256-ctr
9) aes-192-ctr
10) aes-128-ctr
11) chacha20-ietf
12) chacha20
13) rc4-md5
14) rc4-md5-6
Which cipher you'd select(Default: aes-256-cfb):12

cipher = chacha20

Please select protocol for ShadowsocksR:
1) origin
2) verify_deflate
3) auth_sha1_v4
4) auth_sha1_v4_compatible
5) auth_aes128_md5
6) auth_aes128_sha1
7) auth_chain_a
8) auth_chain_b
Which protocol you'd select(Default: origin):3

protocol = auth_sha1_v4

Please select obfs for ShadowsocksR:
1) plain
2) http_simple
3) http_simple_compatible
4) http_post
5) http_post_compatible
6) tls1.2_ticket_auth
7) tls1.2_ticket_auth_compatible
8) tls1.2_ticket_fastauth
9) tls1.2_ticket_fastauth_compatible
Which obfs you'd select(Default: plain):2

obfs = http_simple


Press any key to start...or Press Ctrl+C to cancel
```
按提示按下任意键进行部署，稍等一会，最后看到如下字样则部署成功
``` bash
IPv6 support
Starting ShadowsocksR success

Congratulations, ShadowsocksR server install completed!
Your Server IP        :  169.211.20.50
Your Server Port      :  20002
Your Password         :  ssr2017
Your Protocol         :  auth_sha1_v4
Your obfs             :  http_simple
Your Encryption Method:  chacha20

Your QR Code: (For ShadowsocksR Windows, Android clients only)
 ssr://MTY5Lja1NC4yMC41MDoyMDAwMjphdXRoX3NoYTFfdjQ6Y2hhY0hhMjA6aHR0cF9zaW1wbGU6YzNOeU1qQXhOdy8/b2Jmc3BhcmFtPQ==
Your QR Code has been saved as a PNG file path:
 /mnt/c/Users/xxx/shadowsocks_r_qr.png

Welcome to visit: https://teddysun.com/486.html
Enjoy it!
```
上边显示的也是SSR客户端连接时进行配置的参数，至此，你已经架好了自己梯子了。
#### 三、配置SSR客户端
##### 1、Windows系统客户端
##### 2、Android系统客户端
##### 3、Mac系统客户端





[1]: https://www.vultr.com/?ref=7295913
[2]: https://m.do.co/c/ce4e63a0ccb4
[3]: https://www.linode.com/
[4]: https://azure.microsoft.com
[1000]: https://teddysun.com/486.html