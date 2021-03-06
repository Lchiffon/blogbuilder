---
layout: post
title: 读书笔记:谱分析
categories: 技术学习
date: 2014-07-08
---


- 今天晚上讨论课,准备是讲一下谱分析和极值理论基础的.极值理论之前准备的差不多了,然后今天下午这段时间整理下谱分析的一些知识

## 谱分析

### 宽平稳过程

宽平稳过程指一个期望为常数的二阶矩过程中:
cov(X(t),X(s))=R(s-t) 也就是说协方差函数不随时间的推移而改变.

宽平稳过程又称平稳过程,与之相对应的是严平稳过程,所有统计性质随着时间的推移都不发生变化.

对于一个宽平稳过程的协方差函数,R(s,t)=R(s-t)有如下的性质:

-  R(0)=D(t)
-  0期协方差等于自己的方差
-  |R(z)|<=R(0)
-  容易从相关系数属于[-1,1]证出
-  R(z)与R(-z)的共轭相等
-  在一个非复随即过程就转化为二者相等
-   R(z)为z的非负定函数

所以,实平稳过程的协方差函数应该是一个偶函数

--------


为什么要介绍宽平稳过程呢?
事实上,对于谱分析的定义,是在一个宽平稳过程的协方差函数上定义的,也是一个一般化的情况.对于非平稳的序列,需要通过差分等运算转化成宽平稳的过程

### 平稳过程的谱分解

#### 协方差函数(相关函数)的谱分解

平稳过程的谱分解依赖于一个正交增量过程,而协方差函数的谱分解则是对于协方差函数做的一个傅里叶变换

#### 正交增量过程

一个随机过程满足:

1. 对任意t1
2. 不重叠区间上的增量相互正交
3. x(t)均方右连续

[连续情形] 根据Bochner-Khintchine定理,一个连续的非负定函数都可以用一个分布函数F(x)来做傅里叶变换,这就是协方差函数(相关函数)的谱分解 同时,可以用一个正交增量过程来对原平稳过程进行谱分解

[离散情形] 根据Herglotz’s定理,一个离散时间序列是可以用一个分布函数来描 述相关函数,一个正交增量过程来描述原时间序列的.

在进行谱分解的时候,得到的分布函数F(x)就是相关函数的功率谱函数 ,如果相关函数的绝对值之和是有限的,则功率谱函数的导数存在 ,可以得到相关函数的谱密度函数就是f(x)

具体谱分析所涉及到的方面就是以上的部分,感觉写的乱乱的, 赶紧自己准备一些晚上讲的例子,这里就不发了

查看更多关于平稳过程的信息到wiki百科: (http://en.wikipedia.org/wiki/Stationary_process)
