---
layout: post
title: Python 正则表达式II
image: http://ww3.sinaimg.cn/large/005yyi5Jjw1eoerczxex0j30im08ltau.jpg
category: JsPy&Others
tags: JsPy&Others
date: 2015-06-26
---

  <div tabindex="-1" id="notebook" class="border-box-sizing">
    <div class="container" id="notebook-container">

<div class="cell border-box-sizing text_cell rendered">
<div class="prompt input_prompt">
</div>
<div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="Python-&#27491;&#21017;&#34920;&#36798;&#24335;(&#20108;)">Python &#27491;&#21017;&#34920;&#36798;&#24335;(&#20108;)<a class="anchor-link" href="#Python-&#27491;&#21017;&#34920;&#36798;&#24335;(&#20108;)">&#182;</a></h2><h3 id="&#21152;&#36733;&#30456;&#20851;&#24211;">&#21152;&#36733;&#30456;&#20851;&#24211;<a class="anchor-link" href="#&#21152;&#36733;&#30456;&#20851;&#24211;">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[4]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython2"><pre><span class="kn">from</span> <span class="nn">nltk.book</span> <span class="kn">import</span> <span class="o">*</span>
<span class="kn">import</span> <span class="nn">nltk</span>
<span class="kn">import</span> <span class="nn">re</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area"><div class="prompt"></div>
<div class="output_subarea output_stream output_stdout output_text">
<pre>*** Introductory Examples for the NLTK Book ***
Loading text1, ..., text9 and sent1, ..., sent9
Type the name of the text or sentence to view it.
Type: &apos;texts()&apos; or &apos;sents()&apos; to list the materials.
text1: Moby Dick by Herman Melville 1851
text2: Sense and Sensibility by Jane Austen 1811
text3: The Book of Genesis
text4: Inaugural Address Corpus
text5: Chat Corpus
text6: Monty Python and the Holy Grail
text7: Wall Street Journal
text8: Personals Corpus
text9: The Man Who Was Thursday by G . K . Chesterton 1908
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered">
<div class="prompt input_prompt">
</div>
<div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<ul>
<li>输入测试文本:</li>
</ul>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[24]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython2"><pre><span class="n">f</span> <span class="o">=</span> <span class="nb">open</span><span class="p">(</span><span class="s">&quot;Alcie.txt&quot;</span><span class="p">,</span><span class="s">&quot;r&quot;</span><span class="p">)</span>
<span class="n">text</span> <span class="o">=</span> <span class="n">f</span><span class="o">.</span><span class="n">readlines</span><span class="p">(</span><span class="mi">5</span><span class="p">)</span>
<span class="n">raw</span> <span class="o">=</span> <span class="n">text</span><span class="p">[</span><span class="mi">0</span><span class="p">]</span><span class="o">+</span><span class="n">text</span><span class="p">[</span><span class="mi">1</span><span class="p">]</span><span class="o">+</span><span class="n">text</span><span class="p">[</span><span class="mi">2</span><span class="p">]</span><span class="o">+</span><span class="n">text</span><span class="p">[</span><span class="mi">3</span><span class="p">]</span>
<span class="c">## raw = &quot;&quot;.join(text)</span>
<span class="k">print</span><span class="p">(</span><span class="n">raw</span><span class="p">)</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area"><div class="prompt"></div>
<div class="output_subarea output_stream output_stdout output_text">
<pre>Alice was beginning to get very tired of sitting by her sister on the bank,
 and of having nothing to do: once or twice she had peeped into the
 book her sister was reading, but it had no pictures or conversations
 in it, &quot;and what is the use of a book,&quot;thought Alice &quot;without pictures or conversation?&apos;
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered">
<div class="prompt input_prompt">
</div>
<div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="\s&#21644;\w,&#23545;&#25991;&#26412;&#36827;&#34892;&#20998;&#21106;">\s&#21644;\w,&#23545;&#25991;&#26412;&#36827;&#34892;&#20998;&#21106;<a class="anchor-link" href="#\s&#21644;\w,&#23545;&#25991;&#26412;&#36827;&#34892;&#20998;&#21106;">&#182;</a></h3><h4 id="&#23581;&#35797;&#23558;&#36825;&#20010;&#25991;&#26412;&#36827;&#34892;&#20998;&#21106;:">&#23581;&#35797;&#23558;&#36825;&#20010;&#25991;&#26412;&#36827;&#34892;&#20998;&#21106;:<a class="anchor-link" href="#&#23581;&#35797;&#23558;&#36825;&#20010;&#25991;&#26412;&#36827;&#34892;&#20998;&#21106;:">&#182;</a></h4><ul>
<li>使用r' '分割</li>
<li>使用r'[ \t\n]+'分割</li>
<li>使用正则表达r'\s+'分割</li>
</ul>

</div>
</div>
</div>re.split(r' ',raw)
re.split(r'[ \t\n]+',raw)
re.split(r'\s+',raw)
<div class="cell border-box-sizing text_cell rendered">
<div class="prompt input_prompt">
</div>
<div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>结果比较长就不贴出来了</p>
<ul>
<li>第一个正则表达是有问题的,仅使用空格进行分割会忽略制表符(\t)和换行符(\n)</li>
<li>第二个正则表达匹配了一个或者多个空格/制表/换行符,可以合适的对文本进行分割</li>
<li>第三个正则表达最简洁,和第二个效果相同,是re库的内置缩写,\s代替了空格/制表/换行符</li>
<li>值得一提的是\S代表了\s的补,也就是所有非空格/制表/换行符</li>
</ul>
<h4 id="&#20877;&#27425;,&#20351;&#29992;\w&#26469;&#36827;&#34892;&#20998;&#21106;">&#20877;&#27425;,&#20351;&#29992;\w&#26469;&#36827;&#34892;&#20998;&#21106;<a class="anchor-link" href="#&#20877;&#27425;,&#20351;&#29992;\w&#26469;&#36827;&#34892;&#20998;&#21106;">&#182;</a></h4><p>\w代替了所有字母,数字和下划线</p>
<p>r'\w' = r'[a-zA-Z0-9_]'</p>
<p>同样的,\W代替了\w的补,所有非字母,数字和下划线</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[30]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython2"><pre><span class="n">re</span><span class="o">.</span><span class="n">split</span><span class="p">(</span><span class="s">r&#39;\W+&#39;</span><span class="p">,</span><span class="n">raw</span><span class="p">)[</span><span class="mi">0</span><span class="p">:</span><span class="mi">9</span><span class="p">]</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area"><div class="prompt output_prompt">Out[30]:</div>


<div class="output_text output_subarea output_execute_result">
<pre>[&apos;Alice&apos;, &apos;was&apos;, &apos;beginning&apos;, &apos;to&apos;, &apos;get&apos;, &apos;very&apos;, &apos;tired&apos;, &apos;of&apos;, &apos;sitting&apos;]</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[32]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython2"><pre><span class="n">re</span><span class="o">.</span><span class="n">findall</span><span class="p">(</span><span class="s">r&#39;\w+&#39;</span><span class="p">,</span><span class="n">raw</span><span class="p">)[</span><span class="mi">0</span><span class="p">:</span><span class="mi">9</span><span class="p">]</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area"><div class="prompt output_prompt">Out[32]:</div>


<div class="output_text output_subarea output_execute_result">
<pre>[&apos;Alice&apos;, &apos;was&apos;, &apos;beginning&apos;, &apos;to&apos;, &apos;get&apos;, &apos;very&apos;, &apos;tired&apos;, &apos;of&apos;, &apos;sitting&apos;]</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered">
<div class="prompt input_prompt">
</div>
<div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>再看这样一个例子:</p>
<p>加入我们想分割: "I'm very tired!"</p>
<p>其中"'m"部分想单独取出,用之前的方法是行不通的:</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[34]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython2"><pre><span class="n">raw2</span> <span class="o">=</span> <span class="s">&quot;I&#39;m very tired!&quot;</span>
<span class="n">re</span><span class="o">.</span><span class="n">findall</span><span class="p">(</span><span class="s">r&#39;\w+&#39;</span><span class="p">,</span><span class="n">raw2</span><span class="p">)</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area"><div class="prompt output_prompt">Out[34]:</div>


<div class="output_text output_subarea output_execute_result">
<pre>[&apos;I&apos;, &apos;m&apos;, &apos;very&apos;, &apos;tired&apos;]</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[35]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython2"><pre><span class="n">re</span><span class="o">.</span><span class="n">findall</span><span class="p">(</span><span class="s">r&#39;\w+|\S\w&#39;</span><span class="p">,</span><span class="n">raw2</span><span class="p">)</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area"><div class="prompt output_prompt">Out[35]:</div>


<div class="output_text output_subarea output_execute_result">
<pre>[&apos;I&apos;, &quot;&apos;m&quot;, &apos;very&apos;, &apos;tired&apos;]</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered">
<div class="prompt input_prompt">
</div>
<div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>其他常用的正则表达式的符号还有\d,\D(代表数字)</p>
<table>
<thead><tr>
<th>符号</th>
<th>功能</th>
</tr>
</thead>
<tbody>
<tr>
<td>\b</td>
<td>词边界</td>
</tr>
<tr>
<td>\d</td>
<td>任一十进制数字 r'[0-9]'</td>
</tr>
<tr>
<td>\D</td>
<td>任何非数字字符 r'[^0-9]'</td>
</tr>
<tr>
<td>\s</td>
<td>任何空白字符 r'\t\n\r\f\v'</td>
</tr>
<tr>
<td>\S</td>
<td>任何非空白字符 r'[^\t\n\r\f\v]'</td>
</tr>
<tr>
<td>\w</td>
<td>任何字母数字下划线 r'[a-zA-Z0-9_]'</td>
</tr>
<tr>
<td>\W</td>
<td>任何非字母数字下划线 r'[^a-zA-Z0-9_]'</td>
</tr>
<tr>
<td>\t</td>
<td>制表符</td>
</tr>
<tr>
<td>\n</td>
<td>换行符</td>
</tr>
</tbody>
</table>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered">
<div class="prompt input_prompt">
</div>
<div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="nltk&#20013;&#30340;&#20998;&#35789;">nltk&#20013;&#30340;&#20998;&#35789;<a class="anchor-link" href="#nltk&#20013;&#30340;&#20998;&#35789;">&#182;</a></h3><p>nltk中也提供了分词的形式:</p>

<pre><code>nltk.regexp_tokensize()

</code></pre>
<p>据说这个函数的分词效率更高,并避免了括号特殊处理的需要,看下面的例子:</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[39]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython2"><pre><span class="n">text</span> <span class="o">=</span> <span class="s">&quot;That U.S.A poster-print costs $12.40...&quot;</span>
<span class="n">pattern</span> <span class="o">=</span> <span class="s">r&#39;&#39;&#39;(?x) ## allow verbose regexps</span>
<span class="s">      ([A-Z].)+    ## abbreviations, e.g U.S.A</span>
<span class="s">    | \w+(-\w+)*   ## words like A-B</span>
<span class="s">    | \$?\d+(\.\d+)?%? ## e.g $12.3 40%</span>
<span class="s">    | \.\.\.       ## ellipsis</span>
<span class="s">    | [][.,:&quot;&#39;?():-_`] ## seperate tokens</span>
<span class="s">    &#39;&#39;&#39;</span>
</pre></div>

</div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[40]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython2"><pre><span class="n">nltk</span><span class="o">.</span><span class="n">regexp_tokenize</span><span class="p">(</span><span class="n">text</span><span class="p">,</span><span class="n">pattern</span><span class="p">)</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area"><div class="prompt output_prompt">Out[40]:</div>


<div class="output_text output_subarea output_execute_result">
<pre>[&apos;Th&apos;, &apos;at&apos;, &apos;U.S.A &apos;, &apos;poster-print&apos;, &apos;costs&apos;, &apos;$12.40&apos;, &apos;...&apos;]</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython2"><pre>
</pre></div>

</div>
</div>
</div>

</div>
    </div>
  </div>
