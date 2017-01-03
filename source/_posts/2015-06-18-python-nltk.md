---
layout: post
title: Python 正则表达式
image: http://ww3.sinaimg.cn/large/005yyi5Jjw1eoerczxex0j30im08ltau.jpg
category: JsPy&Others
tags: JsPy&Others
date: 2015-06-18
---

  <div tabindex="-1" id="notebook" class="border-box-sizing">
    <div class="container" id="notebook-container">

<div class="cell border-box-sizing text_cell rendered">
<div class="prompt input_prompt">
</div>
<div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="Python-&#27491;&#21017;&#34920;&#36798;&#24335;">Python &#27491;&#21017;&#34920;&#36798;&#24335;<a class="anchor-link" href="#Python-&#27491;&#21017;&#34920;&#36798;&#24335;">&#182;</a></h2>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[17]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython2"><pre><span class="kn">from</span> <span class="nn">nltk.book</span> <span class="kn">import</span> <span class="o">*</span>
<span class="kn">import</span> <span class="nn">nltk</span>
<span class="kn">import</span> <span class="nn">re</span>
<span class="n">wordlist</span> <span class="o">=</span> <span class="p">[</span><span class="n">w</span> <span class="k">for</span> <span class="n">w</span> <span class="ow">in</span> <span class="n">nltk</span><span class="o">.</span><span class="n">corpus</span><span class="o">.</span><span class="n">words</span><span class="o">.</span><span class="n">words</span><span class="p">(</span><span class="s">&#39;en&#39;</span><span class="p">)</span> <span class="k">if</span> <span class="n">w</span><span class="o">.</span><span class="n">islower</span><span class="p">()]</span>
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
<h3 id="1&#24320;&#22987;^&#19982;&#32467;&#26463;\$">1&#24320;&#22987;^&#19982;&#32467;&#26463;\$<a class="anchor-link" href="#1&#24320;&#22987;^&#19982;&#32467;&#26463;\$">&#182;</a></h3><p>^匹配一个正则表达式的开始，\$匹配一个正则表达式的结束:</p>
<p>比如r'ed$'代表以ed结束的正则表达</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[10]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython2"><pre><span class="n">regexp</span> <span class="o">=</span> <span class="s">r&#39;ed$&#39;</span>
<span class="p">[</span><span class="n">w</span> <span class="k">for</span> <span class="n">w</span> <span class="ow">in</span> <span class="n">wordlist</span> <span class="k">if</span> <span class="n">re</span><span class="o">.</span><span class="n">search</span><span class="p">(</span><span class="n">regexp</span><span class="p">,</span><span class="n">w</span><span class="p">)][</span><span class="mi">0</span><span class="p">:</span><span class="mi">10</span><span class="p">]</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area"><div class="prompt output_prompt">Out[10]:</div>


<div class="output_text output_subarea output_execute_result">
<pre>[u&apos;abaissed&apos;,
 u&apos;abandoned&apos;,
 u&apos;abased&apos;,
 u&apos;abashed&apos;,
 u&apos;abatised&apos;,
 u&apos;abed&apos;,
 u&apos;aborted&apos;,
 u&apos;abridged&apos;,
 u&apos;abscessed&apos;,
 u&apos;absconded&apos;]</pre>
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
<p>或者匹配以aa开头的字符：</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[11]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython2"><pre><span class="n">regexp</span> <span class="o">=</span> <span class="s">r&#39;^aa&#39;</span>
<span class="p">[</span><span class="n">w</span> <span class="k">for</span> <span class="n">w</span> <span class="ow">in</span> <span class="n">wordlist</span> <span class="k">if</span> <span class="n">re</span><span class="o">.</span><span class="n">search</span><span class="p">(</span><span class="n">regexp</span><span class="p">,</span><span class="n">w</span><span class="p">)]</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area"><div class="prompt output_prompt">Out[11]:</div>


<div class="output_text output_subarea output_execute_result">
<pre>[u&apos;aa&apos;, u&apos;aal&apos;, u&apos;aalii&apos;, u&apos;aam&apos;, u&apos;aardvark&apos;, u&apos;aardwolf&apos;]</pre>
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
<h3 id="2&#20219;&#24847;&#21333;&#20010;&#23383;&#31526;&quot;.&quot;&#21644;&#21487;&#36873;&quot;?&quot;">2&#20219;&#24847;&#21333;&#20010;&#23383;&#31526;"."&#21644;&#21487;&#36873;"?"<a class="anchor-link" href="#2&#20219;&#24847;&#21333;&#20010;&#23383;&#31526;&quot;.&quot;&#21644;&#21487;&#36873;&quot;?&quot;">&#182;</a></h3><p>"."代表任何单个字符</p>
<p>"?"代表之前一个字符是可以选择的，比如r'E-?mail'可以匹配到Email和E-mail</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[12]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython2"><pre><span class="n">regexp</span> <span class="o">=</span> <span class="s">r&#39;^b.t$&#39;</span>
<span class="p">[</span><span class="n">w</span> <span class="k">for</span> <span class="n">w</span> <span class="ow">in</span> <span class="n">wordlist</span> <span class="k">if</span> <span class="n">re</span><span class="o">.</span><span class="n">search</span><span class="p">(</span><span class="n">regexp</span><span class="p">,</span><span class="n">w</span><span class="p">)]</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area"><div class="prompt output_prompt">Out[12]:</div>


<div class="output_text output_subarea output_execute_result">
<pre>[u&apos;bat&apos;, u&apos;bet&apos;, u&apos;bit&apos;, u&apos;bot&apos;, u&apos;but&apos;]</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[19]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython2"><pre><span class="n">regexp</span> <span class="o">=</span> <span class="s">r&#39;e-?mail&#39;</span>
<span class="nb">sum</span><span class="p">(</span><span class="mi">1</span> <span class="k">for</span> <span class="n">w</span> <span class="ow">in</span> <span class="n">nltk</span><span class="o">.</span><span class="n">book</span><span class="o">.</span><span class="n">text5</span> <span class="k">if</span> <span class="n">re</span><span class="o">.</span><span class="n">search</span><span class="p">(</span><span class="n">regexp</span><span class="p">,</span><span class="n">w</span><span class="p">))</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area"><div class="prompt output_prompt">Out[19]:</div>


<div class="output_text output_subarea output_execute_result">
<pre>3</pre>
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
<h3 id="3&#33539;&#22260;&#19982;&#38381;&#21253;">3&#33539;&#22260;&#19982;&#38381;&#21253;<a class="anchor-link" href="#3&#33539;&#22260;&#19982;&#38381;&#21253;">&#182;</a></h3><h4 id="&#33539;&#22260;">&#33539;&#22260;<a class="anchor-link" href="#&#33539;&#22260;">&#182;</a></h4><p>r'^[abc]'匹配以abc开头的字符括号中的字母顺序没有关系</p>
<p>r'^[a-d]'匹配以a-d开头的字符</p>
<h4 id="&#38381;&#21253;">&#38381;&#21253;<a class="anchor-link" href="#&#38381;&#21253;">&#182;</a></h4><p>'+' 代表一个或多个实例</p>
<p>'*' 代表0个或几个实例</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[39]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython2"><pre><span class="n">chatWords</span> <span class="o">=</span> <span class="nb">sorted</span><span class="p">(</span><span class="nb">set</span><span class="p">(</span><span class="n">w</span> <span class="k">for</span> <span class="n">w</span> <span class="ow">in</span> <span class="n">nltk</span><span class="o">.</span><span class="n">corpus</span><span class="o">.</span><span class="n">nps_chat</span><span class="o">.</span><span class="n">words</span><span class="p">()))</span>
<span class="n">regexp</span> <span class="o">=</span> <span class="s">r&#39;^[ha]+$&#39;</span>
<span class="p">[</span><span class="n">w</span> <span class="k">for</span> <span class="n">w</span> <span class="ow">in</span> <span class="n">chatWords</span> <span class="k">if</span> <span class="n">re</span><span class="o">.</span><span class="n">search</span><span class="p">(</span><span class="n">regexp</span><span class="p">,</span><span class="n">w</span><span class="p">)][</span><span class="mi">0</span><span class="p">:</span><span class="mi">10</span><span class="p">]</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area"><div class="prompt output_prompt">Out[39]:</div>


<div class="output_text output_subarea output_execute_result">
<pre>[u&apos;a&apos;,
 u&apos;aaaaaaaaaaaaaaaaa&apos;,
 u&apos;aaahhhh&apos;,
 u&apos;ah&apos;,
 u&apos;ahah&apos;,
 u&apos;ahahah&apos;,
 u&apos;ahh&apos;,
 u&apos;ahhahahaha&apos;,
 u&apos;ahhh&apos;,
 u&apos;ahhhh&apos;]</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[31]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython2"><pre><span class="n">regexp1</span> <span class="o">=</span> <span class="s">r&#39;^m+i+n+e+$&#39;</span>
<span class="p">[</span><span class="n">w</span> <span class="k">for</span> <span class="n">w</span> <span class="ow">in</span> <span class="n">chatWords</span> <span class="k">if</span> <span class="n">re</span><span class="o">.</span><span class="n">search</span><span class="p">(</span><span class="n">regexp1</span><span class="p">,</span><span class="n">w</span><span class="p">)]</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area"><div class="prompt output_prompt">Out[31]:</div>


<div class="output_text output_subarea output_execute_result">
<pre>[u&apos;miiiiiiiiiiiiinnnnnnnnnnneeeeeeeeee&apos;,
 u&apos;miiiiiinnnnnnnnnneeeeeeee&apos;,
 u&apos;mine&apos;,
 u&apos;mmmmmmmmiiiiiiiiinnnnnnnnneeeeeeee&apos;]</pre>
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
<div class=" highlight hl-ipython2"><pre><span class="n">regexp2</span> <span class="o">=</span> <span class="s">r&#39;^m*i*n*e*$&#39;</span>
<span class="p">[</span><span class="n">w</span> <span class="k">for</span> <span class="n">w</span> <span class="ow">in</span> <span class="n">chatWords</span> <span class="k">if</span> <span class="n">re</span><span class="o">.</span><span class="n">search</span><span class="p">(</span><span class="n">regexp2</span><span class="p">,</span><span class="n">w</span><span class="p">)]</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area"><div class="prompt output_prompt">Out[32]:</div>


<div class="output_text output_subarea output_execute_result">
<pre>[u&apos;&apos;,
 u&apos;e&apos;,
 u&apos;i&apos;,
 u&apos;in&apos;,
 u&apos;m&apos;,
 u&apos;me&apos;,
 u&apos;meeeeeeeeeeeee&apos;,
 u&apos;mi&apos;,
 u&apos;miiiiiiiiiiiiinnnnnnnnnnneeeeeeeeee&apos;,
 u&apos;miiiiiinnnnnnnnnneeeeeeee&apos;,
 u&apos;min&apos;,
 u&apos;mine&apos;,
 u&apos;mm&apos;,
 u&apos;mmm&apos;,
 u&apos;mmmm&apos;,
 u&apos;mmmmm&apos;,
 u&apos;mmmmmm&apos;,
 u&apos;mmmmmmmmiiiiiiiiinnnnnnnnneeeeeeee&apos;,
 u&apos;mmmmmmmmmm&apos;,
 u&apos;mmmmmmmmmmmmm&apos;,
 u&apos;mmmmmmmmmmmmmm&apos;,
 u&apos;n&apos;,
 u&apos;ne&apos;]</pre>
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
<p>'[^..]'括号中的^匹配所有不在其中的字符</p>
<p>比如匹配所有非元音字母：</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[38]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython2"><pre><span class="n">regexp2</span> <span class="o">=</span> <span class="s">r&#39;^[^aeiouAEIOU]+$&#39;</span>
<span class="p">[</span><span class="n">w</span> <span class="k">for</span> <span class="n">w</span> <span class="ow">in</span> <span class="n">wordlist</span> <span class="k">if</span> <span class="n">re</span><span class="o">.</span><span class="n">search</span><span class="p">(</span><span class="n">regexp2</span><span class="p">,</span><span class="n">w</span><span class="p">)][</span><span class="mi">0</span><span class="p">:</span><span class="mi">10</span><span class="p">]</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area"><div class="prompt output_prompt">Out[38]:</div>


<div class="output_text output_subarea output_execute_result">
<pre>[u&apos;b&apos;, u&apos;by&apos;, u&apos;byth&apos;, u&apos;c&apos;, u&apos;cly&apos;, u&apos;cry&apos;, u&apos;crypt&apos;, u&apos;cwm&apos;, u&apos;cyp&apos;, u&apos;cyst&apos;]</pre>
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
<h3 id="4&#20854;&#20182;&#38656;&#35201;&#29992;&#21040;&#30340;&#34920;&#36798;">4&#20854;&#20182;&#38656;&#35201;&#29992;&#21040;&#30340;&#34920;&#36798;<a class="anchor-link" href="#4&#20854;&#20182;&#38656;&#35201;&#29992;&#21040;&#30340;&#34920;&#36798;">&#182;</a></h3><ul>
<li>'\’转义，比如'.'匹配'.','\$'匹配‘\$'</li>
<li>'|'表示选择，比如'(ed|ing)\$'代表以ed或者ing结尾的字符</li>
<li>'{m,n}'表示重复次数，m到n次，左右可舍弃</li>
</ul>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[41]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython2"><pre><span class="n">wsj</span> <span class="o">=</span> <span class="nb">sorted</span><span class="p">(</span><span class="nb">set</span><span class="p">(</span><span class="n">nltk</span><span class="o">.</span><span class="n">corpus</span><span class="o">.</span><span class="n">treebank</span><span class="o">.</span><span class="n">words</span><span class="p">()))</span>
<span class="p">[</span><span class="n">w</span> <span class="k">for</span> <span class="n">w</span> <span class="ow">in</span> <span class="n">wsj</span> <span class="k">if</span> <span class="n">re</span><span class="o">.</span><span class="n">search</span><span class="p">(</span><span class="s">&#39;^[0-9]+\.[0-9]+$&#39;</span><span class="p">,</span><span class="n">w</span><span class="p">)][</span><span class="mi">1</span><span class="p">:</span><span class="mi">10</span><span class="p">]</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area"><div class="prompt output_prompt">Out[41]:</div>


<div class="output_text output_subarea output_execute_result">
<pre>[u&apos;0.05&apos;, u&apos;0.1&apos;, u&apos;0.16&apos;, u&apos;0.2&apos;, u&apos;0.25&apos;, u&apos;0.28&apos;, u&apos;0.3&apos;, u&apos;0.4&apos;, u&apos;0.5&apos;]</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[42]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython2"><pre><span class="p">[</span><span class="n">w</span> <span class="k">for</span> <span class="n">w</span> <span class="ow">in</span> <span class="n">wsj</span> <span class="k">if</span> <span class="n">re</span><span class="o">.</span><span class="n">search</span><span class="p">(</span><span class="s">&#39;^[A-Z]+\$$&#39;</span><span class="p">,</span><span class="n">w</span><span class="p">)]</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area"><div class="prompt output_prompt">Out[42]:</div>


<div class="output_text output_subarea output_execute_result">
<pre>[u&apos;US$&apos;]</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[43]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython2"><pre><span class="p">[</span><span class="n">w</span> <span class="k">for</span> <span class="n">w</span> <span class="ow">in</span> <span class="n">wsj</span> <span class="k">if</span> <span class="n">re</span><span class="o">.</span><span class="n">search</span><span class="p">(</span><span class="s">&#39;^[0-9]{4}&#39;</span><span class="p">,</span><span class="n">w</span><span class="p">)][</span><span class="mi">0</span><span class="p">:</span><span class="mi">10</span><span class="p">]</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area"><div class="prompt output_prompt">Out[43]:</div>


<div class="output_text output_subarea output_execute_result">
<pre>[u&apos;1614&apos;,
 u&apos;1637&apos;,
 u&apos;1738.1&apos;,
 u&apos;1787&apos;,
 u&apos;1901&apos;,
 u&apos;1903&apos;,
 u&apos;1917&apos;,
 u&apos;1920s&apos;,
 u&apos;1925&apos;]</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[44]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython2"><pre><span class="p">[</span><span class="n">w</span> <span class="k">for</span> <span class="n">w</span> <span class="ow">in</span> <span class="n">wsj</span> <span class="k">if</span> <span class="n">re</span><span class="o">.</span><span class="n">search</span><span class="p">(</span><span class="s">&#39;^[0-9]+-[a-z]{3,5}&#39;</span><span class="p">,</span><span class="n">w</span><span class="p">)][</span><span class="mi">0</span><span class="p">:</span><span class="mi">10</span><span class="p">]</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area"><div class="prompt output_prompt">Out[44]:</div>


<div class="output_text output_subarea output_execute_result">
<pre>[u&apos;10-day&apos;,
 u&apos;10-lap&apos;,
 u&apos;10-year&apos;,
 u&apos;100-megabyte&apos;,
 u&apos;100-share&apos;,
 u&apos;11-month-old&apos;,
 u&apos;12-member&apos;,
 u&apos;12-point&apos;,
 u&apos;12-year&apos;,
 u&apos;14-hour&apos;]</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[45]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython2"><pre><span class="p">[</span><span class="n">w</span> <span class="k">for</span> <span class="n">w</span> <span class="ow">in</span> <span class="n">wsj</span> <span class="k">if</span> <span class="n">re</span><span class="o">.</span><span class="n">search</span><span class="p">(</span><span class="s">&#39;[a-z]{5,}-[a-z]{2,3}-[a-z]&#39;</span><span class="p">,</span><span class="n">w</span><span class="p">)][</span><span class="mi">0</span><span class="p">:</span><span class="mi">10</span><span class="p">]</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area"><div class="prompt output_prompt">Out[45]:</div>


<div class="output_text output_subarea output_execute_result">
<pre>[u&apos;black-and-white&apos;,
 u&apos;bread-and-butter&apos;,
 u&apos;father-in-law&apos;,
 u&apos;machine-gun-toting&apos;,
 u&apos;savings-and-loan&apos;,
 u&apos;search-and-seizure&apos;,
 u&apos;truth-in-lending&apos;]</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[46]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython2"><pre><span class="p">[</span><span class="n">w</span> <span class="k">for</span> <span class="n">w</span> <span class="ow">in</span> <span class="n">wsj</span> <span class="k">if</span> <span class="n">re</span><span class="o">.</span><span class="n">search</span><span class="p">(</span><span class="s">&#39;(ed|ing)$&#39;</span><span class="p">,</span><span class="n">w</span><span class="p">)][</span><span class="mi">0</span><span class="p">:</span><span class="mi">10</span><span class="p">]</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area"><div class="prompt output_prompt">Out[46]:</div>


<div class="output_text output_subarea output_execute_result">
<pre>[u&apos;62%-owned&apos;,
 u&apos;Absorbed&apos;,
 u&apos;According&apos;,
 u&apos;Adopting&apos;,
 u&apos;Advanced&apos;,
 u&apos;Advancing&apos;,
 u&apos;Alfred&apos;,
 u&apos;Allied&apos;,
 u&apos;Annualized&apos;,
 u&apos;Anything&apos;]</pre>
</div>

</div>

</div>
</div>

</div>
