---
layout: post
title: "0.3.2版本新增的一些theme"
image: http://ww3.sinaimg.cn/large/005yyi5Jjw1eoerczxex0j30im08ltau.jpg
categories: R
date: 2016-02-23
---

感谢@yycc,提供百度地图新增的一个地图样式的支持.链接在[这里](http://developer.baidu.com/map/custom/list.htm)我将REmap中remap函数新增很多不同的themes,用color来进行控制,已更新github~
用如下的命令重新安装:

```
devtools::install_github("lchiffon/REmap")
```

>REmap是一个托管于[github](http://github.com/lchiffon/REmap)的R包,可以完成基于Echarts的交互式地图绘制.
>历史文章见[这里](http://lchiffon.github.io/2015/07/23/REmapGuide.html)



先贴下效果图(几个暗色系还是不错的,由于地图是基于城市优化的,所以在国家级的效果上看其实一般,细节之处,大家可以自己尝试):

![](http://lchiffon.github.io/reveal_slidify/echarts/all.png)

使用方法如下:

```
library(REmap)
geoData  = get_geo_position(unique(demoC[demoC==demoC]))
# this may take some time,be patient~

remapB(markLineData = demoC,geoData = geoData)

# Different themes
remapB(markLineData = demoC,color = "Blue",geoData = geoData)
remapB(markLineData = demoC,color = "light",geoData = geoData)
remapB(markLineData = demoC,color = "dark",geoData = geoData)
remapB(markLineData = demoC,color = "redalert",geoData = geoData)
remapB(markLineData = demoC,color = "googlelite",geoData = geoData)
```

color变量继以前的"Bright"和"Blue"外,新增以下支持:

- "light"
  + 清新蓝风格
- "dark"
  + 黑夜风格
- "redalert"
  + 红色警戒风格
- "googlelite"
  + 精简风格
- "grassgreen"
  + 自然绿风格
- "midnight"
  + 午夜蓝风格
- "pink"
  + 浪漫粉风格
- "darkgreen"
  + 青春绿风格
- "bluish"
  + 清新蓝绿风格
- "grayscale"
  + 高端灰风格
- "hardedge"
  + 强边界风格


具体可参看百度链接:[http://developer.baidu.com/map/custom/list.htm](http://developer.baidu.com/map/custom/list.htm)
