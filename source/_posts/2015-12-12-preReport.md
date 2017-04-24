---
layout: post
title: "快速撰写数据报告,preReport"
image: http://ww3.sinaimg.cn/large/005yyi5Jjw1eoerczxex0j30im08ltau.jpg
categories: R
date: 2015-12-12
---


最近总是要做数据校验的事情,于是,写了个小包,
preReport,专门用于生成快速数据校验的报告.

主要做以下几方面的工作:

1. 数据中缺失值的情况
2. 数据中重复观测值的情况
3. 数据中各个变量的情况,包括缺失,分布图,频数表等

目前托管在github,[https://github.com/Lchiffon/preReport](https://github.com/Lchiffon/preReport),可以用
以下代码安装.

```
devtools::install_github("lchiffon/preReport")
library(preReport)
preReport(iris)
```

可以看我post到Rpubs的例子,在[这里](http://rpubs.com/chiffon_9797/preReport)
欢迎试用,欢迎issue~尤其欢迎star.

![png](https://raw.githubusercontent.com/Lchiffon/preReport/master/new.png)
