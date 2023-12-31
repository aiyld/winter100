---
layout: question
title:  String.slice和String.substring有什么区别？
date:   2020-03-10T06:26:12.000Z
description: 有谁知道这两种方法之间的区别：String.prototype.sliceString.prototype.substring...
img: 
author: Tom小小蛋蛋
category: question
answer: 8
tags: JavaScript
topic: JavaScript
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">有谁知道这两种方法之间的区别：</font></font></p>

<pre><code>String.prototype.slice<font></font>
String.prototype.substring<font></font>
</code></pre></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第506篇《String.slice和String.substring有什么区别？》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Tom卡卡西村村</span>
            <span class="discuss-time">2020.03.10</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">对于</font></font><code>slice(start, stop)</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，如果</font></font><code>stop</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">为负，</font></font><code>stop</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">则将设置为：</font></font></p>

<pre><code>string.length – Math.abs(stop)
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">而不是：</font></font></p>

<pre><code>string.length – 1 – Math.abs(stop)
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">神无StafanTom</span>
            <span class="discuss-time">2020.03.10</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">substr：它使我们能够根据指定的索引来获取部分字符串。</font><font style="vertical-align: inherit;">substr-string.substr（start，end）start的语法-开始索引告诉获取的开始位置。</font><font style="vertical-align: inherit;">end-end索引告诉字符串从何处获取。</font><font style="vertical-align: inherit;">它是可选的。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">slice：它提供了根据指定的索引来获取部分字符串的功能。</font><font style="vertical-align: inherit;">它允许我们指定正数和索引。</font><font style="vertical-align: inherit;">slice的语法-string.slice（start，end）start-起始索引告诉获取开始的位置。end-end索引告诉直到提取字符串的位置。</font><font style="vertical-align: inherit;">它是可选的。</font><font style="vertical-align: inherit;">在“拼接”中，开始索引和结束索引都有助于获取正负索引。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">字符串中“ slice”的示例代码</font></font></p>

<pre><code>var str="Javascript";<font></font>
console.log(str.slice(-5,-1));<font></font>
<font></font>
output: crip<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">字符串中“ substring”的示例代码</font></font></p>

<pre><code>var str="Javascript";<font></font>
console.log(str.substring(1,5));<font></font>
<font></font>
output: avas<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">[*注：负索引从字符串的末尾开始。]</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">TonyJinJin泡芙</span>
            <span class="discuss-time">2020.03.10</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">注意：如果您急于和/或正在寻找简短的答案，请滚动到答案的底部，然后阅读最后两行。如果不急，请阅读整本书。</font></font><br><br><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">让我首先说明事实：</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">语法：</font></font><br>
<code>string.slice(start,end)</code><br>
<code>string.substr(start,length)</code><br>
<code>string.substring(start,end)</code><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">
注释＃1：</font></font><code>slice()==substring()</code></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">它能做什么？</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">
该</font></font><code>slice()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">方法提取字符串的一部分，并以新字符串返回提取的部分。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">
该</font></font><code>substr()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">方法提取从指定位置的字符开始的字符串部分，并返回指定数量的字符。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">
该</font></font><code>substring()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">方法提取字符串的一部分，并以新字符串返回提取的部分。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">
笔记2：</font></font><code>slice()==substring()</code></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">更改原始字符串？</font></font><br>
<code>slice()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">不</font></font><br>
<code>substr()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">不</font></font><br>
<code>substring()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">不</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">
注3：</font></font><code>slice()==substring()</code></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">使用负数作为参数：</font></font><br>
<code>slice()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">选择从字符串末尾开始的字符</font></font><br>
<code>substr()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">选择从字符串末尾开始的字符</font></font><br>
<code>substring()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">不执行</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">
注释＃3：</font></font><code>slice()==substr()</code></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果第一个参数大于第二：</font></font><br>
<code>slice()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">不执行</font></font><br>
<code>substr()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，因为第二个参数不是一个位置，但长度值，它会像往常一样执行，没有任何问题</font></font><br>
<code>substring()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">将交换两个参数，并执行像往常一样</font></font><br></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">第一个参数：</font></font><br>
<code>slice()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">必需，指示：</font></font><br>
<code>substr()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">必需的</font><font style="vertical-align: inherit;">起始索引</font><font style="vertical-align: inherit;">，指示：</font></font><br>
<code>substring()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">必需的</font><font style="vertical-align: inherit;">起始索引</font><font style="vertical-align: inherit;">，指示：起始索引</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">
注释4：</font></font><code>slice()==substr()==substring()</code></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">第二个参数：</font></font><br>
<code>slice()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">可选，提取终止的位置（最多但不包括）</font></font><br>
<code>substr()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">可选，要提取的字符数可选，</font><font style="vertical-align: inherit;">终止提取</font></font><br>
<code>substring()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">的位置（最多但不包括）</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">
注解＃5：</font></font><code>slice()==substring()</code></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果省略第二个参数怎么办？</font></font><br>
<code>slice()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">选择从字符串的开始位置到结尾的</font></font><br>
<code>substr()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">所有字符选择从</font><font style="vertical-align: inherit;">字符串</font><font style="vertical-align: inherit;">的开始位置到结尾的</font></font><br>
<code>substring()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">所有字符选择从</font><font style="vertical-align: inherit;">字符串</font><font style="vertical-align: inherit;">的开始位置到结尾的所有字符</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">
注意＃6：</font></font><code>slice()==substr()==substring()</code></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">因此，您可以说</font></font><code>slice()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">和</font><font style="vertical-align: inherit;">之间有区别</font></font><code>substr()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，而</font></font><code>substring()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">基本上是的副本</font></font><code>slice()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font><br></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">总结中：</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">
如果您知道将要停止的索引（位置）（但不包括在内），</font></font><code>slice()</code><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">
则如果知道要提取的字符的长度，请使用</font></font><code>substr()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">null</span>
            <span class="discuss-time">2020.03.10</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">一个答案很好，但是需要一点阅读。</font><font style="vertical-align: inherit;">尤其是新术语“停止”。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我的围棋（My Go）–除上面丹尼尔（Daniel）的第一个回答外，还通过差异进行整理以使其有用：</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">1）负指标。</font><font style="vertical-align: inherit;">子字符串需要正索引，并将负索引设置为0。slice的负索引表示从字符串末尾开始的位置。</font></font></p>

<pre><code>"1234".substring(-2, -1) == "1234".substring(0,0) == ""<font></font>
"1234".slice(-2, -1) == "1234".slice(2, 3) == "3"<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">2）交换索引。</font><font style="vertical-align: inherit;">子字符串将对索引重新排序，以使第一个索引小于或等于第二个索引。</font></font></p>

<pre><code>"1234".substring(3,2) == "1234".substring(2,3) == "3"<font></font>
"1234".slice(3,2) == ""<font></font>
</code></pre>

<h2><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">--------------------------</font></font></h2>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">一般评论-我觉得第二个索引是切片或子字符串的最后一个字符之后的位置很奇怪。</font><font style="vertical-align: inherit;">我希望“ 1234” .slice（2,2）返回“ 3”。</font><font style="vertical-align: inherit;">这使Andy的困惑超出了合理范围-我希望“ 1234” .slice（2，-1）返回“ 34”。</font><font style="vertical-align: inherit;">是的，这意味着我是Java的新手。</font><font style="vertical-align: inherit;">这也意味着这种行为：</font></font></p>

<pre><code>"1234".slice(-2, -2) == "", "1234".slice(-2, -1) == "3", "1234".slice(-2, -0) == "" &lt;-- you have to use length or omit the argument to get the 4.<font></font>
"1234".slice(3, -2) == "", "1234".slice(3, -1) == "", "1234".slice(3, -0) == "" &lt;-- same issue, but seems weirder.<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我的2c。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">梅米亚</span>
            <span class="discuss-time">2020.03.10</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">slice和substring方法之间的唯一区别是参数</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">两者都有两个参数，例如开始/起始和结束/至。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您不能将负值作为</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">子字符串</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">方法的</font><font style="vertical-align: inherit;">第一个参数传递，</font><font style="vertical-align: inherit;">而让</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">slice</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">方法从末尾遍历它。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">切片方法参数详细信息：</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">参考：</font><a href="http://www.thesstech.com/javascript/string_slice_method" rel="nofollow"><font style="vertical-align: inherit;">http</font></a><font style="vertical-align: inherit;">： 
 </font></font><a href="http://www.thesstech.com/javascript/string_slice_method" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">//www.thesstech.com/javascript/string_slice_method</font></font></a></p>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">争论</font></font></strong></p>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">start_index</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> 
切片应从何处开始的索引。</font><font style="vertical-align: inherit;">如果提供负值，则表示从最后开始。</font><font style="vertical-align: inherit;">例如，最后一个字符为-1。
</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">end_index</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> 
切片结束后的索引。</font><font style="vertical-align: inherit;">如果未提供，则切片将从start_index到字符串的结尾。</font><font style="vertical-align: inherit;">在负值的情况下，将从字符串末尾开始测量索引。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">子字符串方法参数详细信息：</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">REF：</font><a href="http://www.thesstech.com/javascript/string_substring_method" rel="nofollow"><font style="vertical-align: inherit;">http</font></a><font style="vertical-align: inherit;"> : </font></font><a href="http://www.thesstech.com/javascript/string_substring_method" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">//www.thesstech.com/javascript/string_substring_method</font></font></a></p>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">争论</font></font></strong></p>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">from</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> 
应该是一个非负整数，用于指定子字符串应从何处开始的索引。
</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">到</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> 
一个可选的非负整数，以提供在完成子字符串之前的索引。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">小宇宙猴子</span>
            <span class="discuss-time">2020.03.10</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Ben Nadel撰写了一篇很好的文章，指出了这些函数的参数差异：</font></font></p>

<pre><code>String.slice( begin [, end ] )<font></font>
String.substring( from [, to ] )<font></font>
String.substr( start [, length ] )<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">他还指出，如果slice的参数为负，则它们将从结尾引用字符串。</font><font style="vertical-align: inherit;">Substring和substr不会。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这是他关于此的文章</font></font><a href="http://www.bennadel.com/blog/2159-using-slice-substring-and-substr-in-javascript.htm" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">http://www.bennadel.com/blog/2159-using-slice-substring-and-substr-in-javascript.htm</font></font></a></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">卡卡西Mandy</span>
            <span class="discuss-time">2020.03.10</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">子字符串和切片之间的区别-它们是如何与国外的负数和俯瞰线参数一起工作的：</font></font></p>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">子字符串（开始，结束）</font></font></strong></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">负参数将被解释为零。</font><font style="vertical-align: inherit;">太大的值将被截断为字符串的长度：alert（“ testme” .substring（-2））; </font><font style="vertical-align: inherit;">//“ testme”，-2变为0</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">此外，如果开始&gt;结束，则参数会互换，即在起点和终点之间返回绘图线：</font></font></p>

<pre><code>alert ( "testme" .substring (4, -1)); // "test"<font></font>
// -1 Becomes 0 -&gt; got substring (4, 0)<font></font>
// 4&gt; 0, so that the arguments are swapped -&gt; substring (0, 4) = "test"<font></font>
</code></pre>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">切片</font></font></strong></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">从行尾开始测量负值：</font></font></p>

<pre><code>alert ( "testme" .slice (-2)); // "me", from the end position 2<font></font>
alert ( "testme" .slice (1, -1)); // "estm", from the first position to the one at the end.<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">它比奇怪的逻辑子字符串方便得多。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">除IE8-以外的所有浏览器均支持substr的第一个参数的负值。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果在大多数情况下使用这三种方法中的一种，它将是</font></font><strong><em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">slice</font></font></em></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">：否定参数，并且它保持和操作最明显。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">村村JinJin</span>
            <span class="discuss-time">2020.03.10</span>
          </div>
          <div class="discuss-comment"><p><code>slice()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">就像</font></font><code>substring()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">有几种不同的行为一样。</font></font></p>

<pre><code>Syntax: string.slice(start, stop);<font></font>
Syntax: string.substring(start, stop);<font></font>
</code></pre>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">他们有什么共同点：</font></font></strong></p>

<ol>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果</font></font><code>start</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">等于</font></font><code>stop</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">：返回一个空字符串</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果</font></font><code>stop</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">省略，则将字符提取到字符串的末尾</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果任一参数大于字符串的长度，则将使用字符串的长度来代替。</font></font></li>
</ol>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">的区别</font></font></strong> <font style="vertical-align: inherit;"><strong><font style="vertical-align: inherit;">：</font></strong></font><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/substring" rel="noreferrer"><code>substring()</code></a><strong><font style="vertical-align: inherit;"></font></strong></p>

<ol>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果为</font></font><code>start &gt; stop</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，</font></font><code>substring</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">则将交换这两个参数。</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果任一参数为负或为</font></font><code>NaN</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，则将其视为</font></font><code>0</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></li>
</ol>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">的区别</font></font></strong> <font style="vertical-align: inherit;"><strong><font style="vertical-align: inherit;">：</font></strong></font><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/slice" rel="noreferrer"><code>slice()</code></a><strong><font style="vertical-align: inherit;"></font></strong></p>

<ol>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果为</font></font><code>start &gt; stop</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，</font></font><code>slice()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">则返回空字符串。</font><font style="vertical-align: inherit;">（</font></font><code>""</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">）</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果</font></font><code>start</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">为负：像</font></font><code>substr()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在Firefox中</font><font style="vertical-align: inherit;">一样</font><font style="vertical-align: inherit;">，</font><font style="vertical-align: inherit;">从字符串末尾设置char </font><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">在Firefox和IE中都观察到此行为。</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果</font></font><code>stop</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">为负：停止点设置为：（</font></font><code>string.length – Math.abs(stop)</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">原始值），但</font><a href="https://www.ecma-international.org/ecma-262/9.0/index.html#sec-string.prototype.slice" rel="noreferrer"><font style="vertical-align: inherit;">ECMA规范中</font></a></font><code>Math.max(0, string.length + stop)</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">涵盖的</font><font style="vertical-align: inherit;">边界为0（因此</font><font style="vertical-align: inherit;">）</font><font style="vertical-align: inherit;">。</font></font><a href="https://www.ecma-international.org/ecma-262/9.0/index.html#sec-string.prototype.slice" rel="noreferrer"><font style="vertical-align: inherit;"></font></a><font style="vertical-align: inherit;"></font></li>
</ol>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">来源：</font></font><a href="http://rapd.wordpress.com/2007/07/12/javascript-substr-vs-substring/" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">编程和开发的基本艺术：Javascript：substr（）vs substring（）</font></font></a></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
