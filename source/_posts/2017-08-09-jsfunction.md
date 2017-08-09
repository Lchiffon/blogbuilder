---
title: "如何不污染作用域"
image: http://ww3.sinaimg.cn/large/005yyi5Jjw1eoerczxex0j30im08ltau.jpg
categories: R
date: 2017-04-25
---

JS代码里面有个有趣的函数写法, 是把一个函数**定义好之后立即执行**, 这样函数内部的内容不会污染整个作用域(大概可以用这个词吧)

```js
(function(){
 XXX
})()
```

虽然这样的代码在R里面也是可以用滴, 但是相比于JS这种写法的流行程度, 在R里面基本没怎么见人用过,
非要强说的话apply类函数里面也是有这样的匿名函数, 但是不太常见这种定义立即执行的过程.

然而仔细想想还是有几个使用的场景的

## 读取数据并执行操作

一个经典的例子是读取数据, 做一些操作, 做好之后把结果存在另一个文件里面, 如何保证变量空间中绝对干净?
可以使用这样的定义执行过程:

```r
(function(){
 dat = read.csv("data/dat.csv")
 model = lm(y~.,dat)
 res = predict(model,newx=dat)
 dat$res = res
 write.csv(dat, "data/datResult.csv")
})()
```

当然, 这只是省掉了`rm(dat,model,res)`这样一句代码

## do的过程

这个东西感觉又是个冷门的很的知识, 这个`do`来源于`dplyr::do`的函数(plyr中也有, 但不做讨论), 这个`do`的功能是对一个`group_by`
之后的数据框做汇总整理, 再返回一个数据框

比如帮助文档里面有这样的一个例子:

对数据的`cyl`进行group by, 对每个小组训练一个线性模型, 再取出它的参数, **需要分两步`do`执行**
```r
by_cyl <- group_by(mtcars, cyl)
do(by_cyl, head(., 2))
# 根据groupby 训练N个模型
models <- by_cyl %>% do(mod = lm(mpg ~ disp, data = .))
models
```
```r
Source: local data frame [3 x 2]
Groups: <by row>

# A tibble: 3 × 2
    cyl      mod
* <dbl>   <list>
1     4 <S3: lm>
2     6 <S3: lm>
3     8 <S3: lm>

```
```r
# 提取参数
models %>% do(data.frame(coef = coef(.$mod)))
```
```r
Source: local data frame [6 x 1]
Groups: <by row>

# A tibble: 6 × 1
          coef
*        <dbl>
1 40.871955322
2 -0.135141815
3 19.081987419
4  0.003605119
5 22.032798914
6 -0.019634095
```

但如果用定义函数立即执行的操作, 是可以在函数内部为所欲为的写代码了:

```r
models2 <- by_cyl %>% do((function(){
		mod = lm(mpg ~ disp, data = .)
		data.frame(coef = coef(mod))
	})())
```

```r
Source: local data frame [6 x 2]
Groups: cyl [3]

    cyl         coef
  <dbl>        <dbl>
1     4 40.871955322
2     4 -0.135141815
3     6 19.081987419
4     6  0.003605119
5     8 22.032798914
6     8 -0.019634095
```

恩恩, 大概就是这样, GL, HF~

