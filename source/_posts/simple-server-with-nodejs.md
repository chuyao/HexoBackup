---
title: 一个简单的Node.js服务器
date: 2017-07-11 14:02:57
tags:
    - Tech
    - Node.js
categories: Tech
---
先来看个[官方Hello World](https://nodejs.org/en/about/)，几行代码即可搭建一个服务器。
``` js
const http = require('http');

const hostname = '127.0.0.1';
const port = 3000;

const server = http.createServer((req, res) => {
  res.statusCode = 200;
  res.setHeader('Content-Type', 'text/plain');
  res.end('Hello World\n');
});

server.listen(port, hostname, () => {
  console.log(`Server running at http://${hostname}:${port}/`);
});
```
十分简洁，只要有点javascript语法知识，就能看懂。
当然，并不是所看到的那么简单，要让这几行代码“简单”起来，需要依赖于一个安装好的Node环境，关于Node环境安装，不想赘述太多，网上的教程一大堆，这里简单总结一下：
1. Windows系统环境
下载[官方安装源](https://nodejs.org/en/download/)安装即可；
2. Linux系统环境
推荐使用[nvm](https://github.com/creationix/nvm/blob/master/README.md#install-script)安装及管理node版本，当然，也可以访问上面提到的官方安装源，下载安装。

请尽量安装使用LTS版本，经过上边的步骤，就可以如开头所说的，快速搭建一个简单服务器了。
下边进入正题，先说一个场景，一个客户端开发人员，需要对接口进行测试，需要接口假数据，真的会有一些开发人员说：“没有数据我开发不了！”，而碰巧后端同事又还没空开发接口、做假数据，怎么办？求人不如求己！具体到开发案例场景，客户端开发需要一个升级检查功能(一般包含两部分，版本检查，高版本文件下载)，针对这个场景，今天用node.js来实现解决方案。

