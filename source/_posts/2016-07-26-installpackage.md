---
title: "wordcloud2 in CRAN"
image: http://ww3.sinaimg.cn/large/005yyi5Jjw1eoerczxex0j30im08ltau.jpg
categories: R
date: 2016-07-26
---

最近把`wordcloud2`发布到了CRAN上,所以,以后就可以直接用`install.packages('wordcloud2')`进行安装.

这样是不是这篇博客有点短,我再加个用wordcloud2 做头像的方法:

- 写一个文件,把你喜欢的词(认识的不认识的)放进去
- 调整下字数,认识的字少的话可以把文件重复几遍
- 生成词频,我用的是<code>seq</code>生成,再用一些小的数字去填空白
- wordcloud!


```r
setwd('E:/tmp')
word = readLines('chiffon.txt')</code></pre>
word1 = c(word,word,word,word,word)
n = length(word)
freq = c(n:1 + 5,
         rep(15,n),
         rep(5,n),
         rep(5,n),
         rep(5,n))
library(wordcloud2)
dat = data.frame(word,freq)
# wordcloud2(dat,size = 0.3)
letterCloud(dat,'R', color = 'random-light',
  backgroundColor = 'black',size = 0.3)
```

<img src='http://7xr5em.com1.z0.glb.clouddn.com/tou.png' />
