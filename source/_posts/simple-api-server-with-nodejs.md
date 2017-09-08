---
title: 一个简单的Node.js接口服务器
date: 2017-07-11 14:02:57
tags:
    - Node.js
categories:
    - IT
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

为了最大程度的简单，这次使用[Express](http://expressjs.com/)，一个目前非常流行的基于Node.js的Web应用开发框架来实现，帮助我们处理http请求及请求路由的简单实现。<!-- more -->

系统命令行状态下，建立程序目标文件夹
``` bash
$ mkdir myserver
$ cd myserver
```

初始化程序包
``` bash
$ npm init
```

出现的选项提示可以都使用默认选项(即一路enter到底)

安装Express
``` bash
$ npm install express --save
```

新建一个文件index.js，用记事本或其它文本编辑器打开，开始写我们的程序
``` js
var express = require('express'); //引入express模块
var app = express();  //express对象

const verStr = {versionName : '2.0.0', versionCode : 200};  //版本检查返回的数据，假数据，自行修改

app.get('/checkUpdate', function(req, res){ //版本检查接口
  res.send(JSON.stringify(verStr));
});

app.get('/download', function(req, res){  //新版本文件下载接口
  res.download('./new-release.apk');
});

app.listen(3000, function(){  //服务端口监听
  console.log('server now listening at port 3000');
});
```

保存，并把需要测试升级的apk文件(文件名称对应为new-release.apk)放到和index.js同级目录下，最后一步，执行
``` bash
$ node index.js
```

即可大功告成了。

检验一下我们的成果，在本机浏览器访问
`http://localhost:3000/checkUpdate`
`http://localhost:3000/download`

