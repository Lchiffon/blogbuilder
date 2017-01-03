---
layout: post
title: "Express所挖的坑..."
image: http://ww3.sinaimg.cn/large/005yyi5Jjw1eoerczxex0j30im08ltau.jpg
tags: 技术学习
date: 2016-02-01
---


## Express
Express.js是一款轻量级的node框架...可以用于快速的网页开发.

目前自己需要写一个图片标记的HTML工具,作为一个小白,在node的框架和React之间徘徊后,
决定用Express来坑自己一把...

需要安装的环境:

- Node.js
- Express
- express-gennernator

有用的学习链接:
- [Express中文网](http://www.expressjs.com.cn)


## 安装使用Express
- 安装依赖:
```
npm install express --save
npm isntall express-generator -g
```

## Hello World1
用建立一个js文件,比如app.js

```
var express = require('express');
var app = express();

app.get('/', function (req, res) {
  res.send('Hello World!');
});

var server = app.listen(3000, function () {
  var host = server.address().address;
  var port = server.address().port;

  console.log('Example app listening at http://%s:%s', host, port);
});
```

端口3000,app是express的初始化,调用get,以"/"的路径返回HelloWorld,后面的server是建立的IP地址和端口.

用如下的命令来启动app.js
```
npm app.js
```
访问自己的端口`http://localhost:3000`就能看到这个结果了..


## Hello World2

HelloWorld2用express gennernator来建立一个server:
```
express myapp
cd myapp
npm install
```

运行:
```
## Mac&Linux
DEBUG=myapp npm start
## Windows
set DEBUG=myapp & npm start
```

该默认的端口还是3000:`http://localhost:3000`
