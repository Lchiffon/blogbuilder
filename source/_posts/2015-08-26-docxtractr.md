---
layout: post
title: "R中的黑魔法--读取WORD文档中的表格"
image: http://ww3.sinaimg.cn/large/005yyi5Jjw1eoerczxex0j30im08ltau.jpg
tags: R
date: 2015-08-26
---

<p>今天早上刷RSS,看到一条消息,说有个包能读取docx的文件,于是就去看了看,玩起来还不错的样子.
所有我就写了一个简单的攻略.从使用,中文支持,还有这个包的原理进行一些叙述,以方便大家使用这个黑魔法<sup>_<sup>.</sup></sup></p>

<p><code>docxtractr</code>是由<a href="https://github.com/hrbrmstr">hrbrmstr</a>托管在github上的开源项目,目前作者正在为CRAN check做最后的一些工作,<a href="https://github.com/hrbrmstr/docxtractr">这里</a>是该项目github的主页,
这里是作者写的<a href="http://rud.is/b/2015/08/24/new-pacakge-docxtractr-easily-extract-tables-from-microsoft-word-docs/">推广软文</a>
(都是鹰文的blog)</p>

<p><br/></p>

<h3>安装</h3>

<p><code>docxtractr</code>包的安装需要使用devtools包</p>

<pre><code class="r">devtools::install_github(&quot;hrbrmstr/docxtractr&quot;)
library(docxtractr)
</code></pre>

<p><br/></p>

<h3>参考示例</h3>

<p>先拿一个简单的示例来热热身.</p>

<p>图片中是一个docx文件,这个文件中有5个表格,尝试读取其中的第一个表格</p>

<p><img src="http://7xr5em.com1.z0.glb.clouddn.com/30.png"></p>

<pre><code class="r">complx &lt;- read_docx(system.file(&quot;examples/complex.docx&quot;,
                                package=&quot;docxtractr&quot;))
docx_tbl_count(complx)
</code></pre>

<pre><code>## [1] 5
</code></pre>

<pre><code class="r">docx_extract_tbl(complx, 1, header=TRUE)
</code></pre>

<pre><code>## Source: local data frame [3 x 4]
##
##   This      Is     A   Column
## 1    1     Cat   3.4      Dog
## 2    3    Fish 100.3     Bird
## 3    5 Pelican   -99 Kangaroo
</code></pre>

<p>读取的结果可以转换为一个数据框,进行进一步的操作:</p>

<pre><code class="r">docx_tbl = docx_extract_tbl(complx, 1, header=TRUE)
as.data.frame(docx_tbl)
</code></pre>

<pre><code>##   This      Is     A   Column
## 1    1     Cat   3.4      Dog
## 2    3    Fish 100.3     Bird
## 3    5 Pelican   -99 Kangaroo
</code></pre>

<p><br/></p>

<h3>非结构化的表格</h3>

<p><code>docxtract</code>可以读取结构化和非结构化的表格,作者提供了一个非结构化表格的例子:</p>

<p><img src="http://7xr5em.com1.z0.glb.clouddn.com/31.png"></p>

<p>尝试一下它的读取:</p>

<pre><code class="r">## 读取并查看表的个数
realworld = read_docx(
               system.file(&quot;examples/realworld.docx&quot;,
                            package=&quot;docxtractr&quot;))
docx_tbl_count(realworld)
</code></pre>

<pre><code>## [1] 8
</code></pre>

<pre><code class="r">## 读取第一个表格
docx_extract_tbl(realworld, 1, header=TRUE)
</code></pre>

<pre><code>## Source: local data frame [8 x 9]
##
##   Lesson 1:  Step 1        NA       NA.1                   NA.2
## 1           Country Birthrate Death Rate Population Growth 2005
## 2               USA      2.06      0.51%                  0.92%
## 3             China      1.62       0.3%                   0.6%
## 4             Egypt      2.83      0.41%                   2.0%
## 5             India      2.35      0.34%                  1.56%
## 6             Italy      1.28      0.72%                  0.35%
## 7            Mexico      2.43      0.25%                  1.41%
## 8           Nigeria      4.78      0.26%                  2.46%
## Variables not shown: NA (chr), NA (chr), NA (chr), NA (chr), NA (chr)
</code></pre>

<pre><code class="r">## 读取第二个表格
docx_extract_tbl(realworld, 2, header=TRUE)
</code></pre>

<pre><code>## Source: local data frame [8 x 3]
##
##   Lesson 1:  Step 2                                             NA
## 1           Country                   Shape of Pyramid: Prediction
## 2               USA Stable base, stable middle, narrow at very top
## 3             China                         Narrow base, large top
## 4             Egypt                         Large base, narrow top
## 5             India                      Larger base, narrower top
## 6             Italy         Stable base, stable middle, larger top
## 7            Mexico                       Large base, narrower top
## 8           Nigeria                         Large base, narrow top
## Variables not shown: NA (chr)
</code></pre>

<p>与图片中的表格对比,看起来还可以,对吧~</p>

<p><code>docxtract</code>会直接把少的地方加上NA&hellip;(类似<code>read.table</code>中的<code>fill=T</code>)</p>

<p><br/></p>

<h3>请问你支持中文么?</h3>

<p>docxtract的开发者并没有在函数中嵌入读取中文时常需要调(jiu)整(jie)的encoding参数,所以,我比较好奇:</p>

<p><strong>docxtract支持中文形式么?</strong></p>

<p>为了验证这个问题,我建立了一个docx的文件,里面扔了一个表格,表格的形式为:</p>

<table><thead>
<tr>
<th>This</th>
<th>Is</th>
<th>A</th>
<th>Column</th>
</tr>
</thead><tbody>
<tr>
<td>1</td>
<td>Cat</td>
<td>3.4</td>
<td>狗</td>
</tr>
<tr>
<td>3</td>
<td>Fish</td>
<td>100.3</td>
<td>鸟</td>
</tr>
<tr>
<td>5</td>
<td>Pelican</td>
<td>-99</td>
<td>袋鼠</td>
</tr>
</tbody></table>

<p><img src="http://7xr5em.com1.z0.glb.clouddn.com/32.png"></p>

<pre><code class="r">complx &lt;- read_docx(&quot;newTry.docx&quot;)
docx_extract_tbl(complx, 1, header=TRUE)
</code></pre>

<pre><code>## Source: local data frame [3 x 4]
##
##   This      Is     A Column
## 1    1     Cat   3.4     狗
## 2    3    Fish 100.3     鸟
## 3    5 Pelican   -99   袋鼠
</code></pre>

<p><strong>还不错,读取成功了&hellip;</strong></p>

<p>看起来很美好,但是,<strong>这是在Linux下实现的结果</strong>,在windows下并不能成功读取出文件的中文形式-_-||</p>

<p><br/></p>

<h4>win下的中文问题</h4>

<p>Tips: <strong>以下是我对原因的一些探索,跳过并不影响阅读</strong></p>

<p>对于原始的函数,read_docx,类似<a href="http://lchiffon.github.io/2014/11/29/slidify-chinese.html">slidify中文乱码的问题</a>
我尝试更改了本地语言格式:</p>

<ul>
<li>设置语言为中文(<code>Sys.setlocale(&quot;LC_CTYPE&quot;, &quot;chs&quot;)</code>)的时候完全不能读取</li>
<li>设置语言为英文的时候(<code>Sys.setlocale(&quot;LC_CTYPE&quot;, &quot;eng&quot;)</code>)可以读出现乱码

<ul>
<li><code>Encoding()</code>函数检测读取出内容的编码为&#39;unknown&#39;</li>
<li>尝试用<code>iconv</code>或者<code>stringi</code>包中的函数进行转换,&#39;GBK&#39;,&#39;GB2312&#39;,&#39;ASCII&#39;均无法识别</li>
</ul></li>
</ul>

<p>之后的尝试便进入了混乱模式:</p>

<p>于是我去clone了他的源码,做了一些更改,<code>docxtract</code>是基于<code>xml2</code>包来实现读写的
<code>xml_read</code>函数中有一个<code>encoding</code>的选项,我把这个选项加了进去并重新加载更改后的包也并没有解决这个问题
&hellip;&hellip;&hellip;</p>

<h4>废了这么多话,最后想说的是windows用户并不能进行中文表格的读取&hellip;</h4>

<p><br/></p>

<h3>docx的原理</h3>

<p>如果你尝试读取一个doc文件,<code>docxtract</code>是不支持的,为什么呢,先看一段<a href="http://baike.baidu.com/link?url=tDQlEgjyfoAFLkI2DS8IW2PIMKOWuGsKgyAPD_4rblSyszFpArcYrNTnVQzNCm5JsnORK75P140bmD81fYC_Ha">百度百科</a></p>

<blockquote>
<p>docx格式的文件本质上是一个ZIP文件。将一个docx文件的后缀改为ZIP后是可以用解压工具打开或是解压的。事实上，Word2007的基本文件就是ZIP格式的，他可以算作是docx文件的容器。
docx 格式文件的主要内容是保存为XML格式的，但文件并非直接保存于磁盘。它是保存在一个ZIP文件中，然后取扩展名为docx。
将.docx 格式的文件后缀改为ZIP后解压, 可以看到解压出来的文件夹中有word这样一个文件夹，它包含了Word文档的大部分内容。而其中的document.xml文件则包含了文档的主要文本内容。</p>
</blockquote>

<p><code>docxtract</code>就是通过xml来进行读取的,doc文件不能被转换为xml,所以也就不能读取了&hellip;</p>

<h3>总结</h3>

<ul>
<li><code>docxtractr</code>包可以完成一些简单的docx中表格读取的问题</li>
<li>可以处理结构化和非结构化的数据读取</li>
<li>对于中文,与很多包类似,支持Liunx(MAC应该也没问题),Windows用户暂时享受不到它的光芒</li>
<li>由于原理的问题,不支持doc文件的读取</li>
</ul>
