---
layout: question
title:  为什么Date.parse给出不正确的结果？
date:   2020-05-28T02:04:02.000Z
description: 情况一：new Date(Date.parse("Jul 8, 2005"));输出：2005年7月8日星期五00 00 00 GMT-070...
img: 
author: Elena镜风
category: question
answer: 8
tags: JavaScript TypeScript
topic: TypeScript
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><h3><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">情况一：</font></font></h3>

<pre class="lang-js prettyprint prettyprinted" style=""><code><span class="kwd">new</span><span class="pln"> </span><span class="typ">Date</span><span class="pun">(</span><span class="typ">Date</span><span class="pun">.</span><span class="pln">parse</span><span class="pun">(</span><span class="str">"Jul 8, 2005"</span><span class="pun">));</span></code></pre>

<h3><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">输出：</font></font></h3>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">2005年7月8日星期五00:00:00 GMT-0700（PST）</font></font></p>

<h3><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">案例二：</font></font></h3>

<pre class="lang-js prettyprint prettyprinted" style=""><code><span class="kwd">new</span><span class="pln"> </span><span class="typ">Date</span><span class="pun">(</span><span class="typ">Date</span><span class="pun">.</span><span class="pln">parse</span><span class="pun">(</span><span class="str">"2005-07-08"</span><span class="pun">));</span></code></pre>

<h3><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">输出：</font></font></h3>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Thu Jul 07 2005 17:00:00 GMT-0700（PST）</font></font></p>

<hr>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">为什么第二次解析不正确？</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第4183篇《为什么Date.parse给出不正确的结果？》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">MonsterKK</span>
            <span class="discuss-time">2020.05.28</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在</font></font><a href="https://stackoverflow.com/a/2587398/6695569"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">从CMS接受的答案</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">是正确的，我刚才已经增加了一些功能：</font></font></p>

<ul>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">修剪和清理输入空间</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">解析斜线，破折号，冒号和空格</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">具有默认的日期和时间</font></font></li>
</ul>

<hr>

<pre class="lang-js prettyprint prettyprinted" style=""><code><span class="com">// parse a date time that can contains spaces, dashes, slashes, colons</span><span class="pln">
</span><span class="kwd">function</span><span class="pln"> parseDate</span><span class="pun">(</span><span class="pln">input</span><span class="pun">)</span><span class="pln"> </span><span class="pun">{</span><span class="pln">
    </span><span class="com">// trimes and remove multiple spaces and split by expected characters</span><span class="pln">
    </span><span class="kwd">var</span><span class="pln"> parts </span><span class="pun">=</span><span class="pln"> input</span><span class="pun">.</span><span class="pln">trim</span><span class="pun">().</span><span class="pln">replace</span><span class="pun">(</span><span class="str">/ +(?= )/</span><span class="pln">g</span><span class="pun">,</span><span class="str">''</span><span class="pun">).</span><span class="pln">split</span><span class="pun">(</span><span class="str">/[\s-\/:]/</span><span class="pun">)</span><span class="pln">
    </span><span class="com">// new Date(year, month [, day [, hours[, minutes[, seconds[, ms]]]]])</span><span class="pln">
    </span><span class="kwd">return</span><span class="pln"> </span><span class="kwd">new</span><span class="pln"> </span><span class="typ">Date</span><span class="pun">(</span><span class="pln">parts</span><span class="pun">[</span><span class="lit">0</span><span class="pun">],</span><span class="pln"> parts</span><span class="pun">[</span><span class="lit">1</span><span class="pun">]-</span><span class="lit">1</span><span class="pun">,</span><span class="pln"> parts</span><span class="pun">[</span><span class="lit">2</span><span class="pun">]</span><span class="pln"> </span><span class="pun">||</span><span class="pln"> </span><span class="lit">1</span><span class="pun">,</span><span class="pln"> parts</span><span class="pun">[</span><span class="lit">3</span><span class="pun">]</span><span class="pln"> </span><span class="pun">||</span><span class="pln"> </span><span class="lit">0</span><span class="pun">,</span><span class="pln"> parts</span><span class="pun">[</span><span class="lit">4</span><span class="pun">]</span><span class="pln"> </span><span class="pun">||</span><span class="pln"> </span><span class="lit">0</span><span class="pun">,</span><span class="pln"> parts</span><span class="pun">[</span><span class="lit">5</span><span class="pun">]</span><span class="pln"> </span><span class="pun">||</span><span class="pln"> </span><span class="lit">0</span><span class="pun">);</span><span class="pln"> </span><span class="com">// Note: months are 0-based</span><span class="pln">
</span><span class="pun">}</span></code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Stafan路易</span>
            <span class="discuss-time">2020.05.28</span>
          </div>
          <div class="discuss-comment"><p>Both are correct, but they are being interpreted as dates with two different timezones. So you compared apples and oranges:</p>

<pre class="lang-js prettyprint prettyprinted" style=""><code><span class="com">// local dates</span><span class="pln">
</span><span class="kwd">new</span><span class="pln"> </span><span class="typ">Date</span><span class="pun">(</span><span class="str">"Jul 8, 2005"</span><span class="pun">).</span><span class="pln">toISOString</span><span class="pun">()</span><span class="pln">            </span><span class="com">// "2005-07-08T07:00:00.000Z"</span><span class="pln">
</span><span class="kwd">new</span><span class="pln"> </span><span class="typ">Date</span><span class="pun">(</span><span class="str">"2005-07-08T00:00-07:00"</span><span class="pun">).</span><span class="pln">toISOString</span><span class="pun">()</span><span class="pln"> </span><span class="com">// "2005-07-08T07:00:00.000Z"</span><span class="pln">
</span><span class="com">// UTC dates</span><span class="pln">
</span><span class="kwd">new</span><span class="pln"> </span><span class="typ">Date</span><span class="pun">(</span><span class="str">"Jul 8, 2005 UTC"</span><span class="pun">).</span><span class="pln">toISOString</span><span class="pun">()</span><span class="pln">        </span><span class="com">// "2005-07-08T00:00:00.000Z"</span><span class="pln">
</span><span class="kwd">new</span><span class="pln"> </span><span class="typ">Date</span><span class="pun">(</span><span class="str">"2005-07-08"</span><span class="pun">).</span><span class="pln">toISOString</span><span class="pun">()</span><span class="pln">             </span><span class="com">// "2005-07-08T00:00:00.000Z"</span></code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我删除了该</font></font><code>Date.parse()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">调用，因为它已自动用于字符串参数。</font><font style="vertical-align: inherit;">我还使用</font></font><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/toISOString" rel="nofollow noreferrer" title="Date.prototype.toISOString（）"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">ISO8601格式</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">比较了日期，因此您可以直观地比较本地日期和UTC日期之间的日期。</font><font style="vertical-align: inherit;">时间相隔7个小时，这是时区差异，也是为什么测试显示两个不同的日期。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">创建这些相同的本地/ UTC日期的另一种方法是：</font></font></p>

<pre class="lang-js prettyprint prettyprinted" style=""><code><span class="kwd">new</span><span class="pln"> </span><span class="typ">Date</span><span class="pun">(</span><span class="lit">2005</span><span class="pun">,</span><span class="pln"> </span><span class="lit">7</span><span class="pun">-</span><span class="lit">1</span><span class="pun">,</span><span class="pln"> </span><span class="lit">8</span><span class="pun">)</span><span class="pln">           </span><span class="com">// "2005-07-08T07:00:00.000Z"</span><span class="pln">
</span><span class="kwd">new</span><span class="pln"> </span><span class="typ">Date</span><span class="pun">(</span><span class="typ">Date</span><span class="pun">.</span><span class="pln">UTC</span><span class="pun">(</span><span class="lit">2005</span><span class="pun">,</span><span class="pln"> </span><span class="lit">7</span><span class="pun">-</span><span class="lit">1</span><span class="pun">,</span><span class="pln"> </span><span class="lit">8</span><span class="pun">))</span><span class="pln"> </span><span class="com">// "2005-07-08T00:00:00.000Z"</span></code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">但是我仍然强烈推荐</font></font><a href="http://momentjs.com/" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Moment.js</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，</font><a href="http://momentjs.com/" rel="nofollow noreferrer"><font style="vertical-align: inherit;">它既</font></a></font><a href="http://momentjs.com/docs/#/parsing/" rel="nofollow noreferrer" title="Moment.js文件"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">简单又强大</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">：</font></font></p>

<pre class="lang-js prettyprint prettyprinted" style=""><code><span class="com">// parse string</span><span class="pln">
moment</span><span class="pun">(</span><span class="str">"2005-07-08"</span><span class="pun">).</span><span class="pln">format</span><span class="pun">()</span><span class="pln">       </span><span class="com">// "2005-07-08T00:00:00+02:00"</span><span class="pln">
moment</span><span class="pun">.</span><span class="pln">utc</span><span class="pun">(</span><span class="str">"2005-07-08"</span><span class="pun">).</span><span class="pln">format</span><span class="pun">()</span><span class="pln">   </span><span class="com">// "2005-07-08T00:00:00Z"</span><span class="pln">
</span><span class="com">// year, month, day, etc.</span><span class="pln">
moment</span><span class="pun">([</span><span class="lit">2005</span><span class="pun">,</span><span class="pln"> </span><span class="lit">7</span><span class="pun">-</span><span class="lit">1</span><span class="pun">,</span><span class="pln"> </span><span class="lit">8</span><span class="pun">]).</span><span class="pln">format</span><span class="pun">()</span><span class="pln">     </span><span class="com">// "2005-07-08T00:00:00+02:00"</span><span class="pln">
moment</span><span class="pun">.</span><span class="pln">utc</span><span class="pun">([</span><span class="lit">2005</span><span class="pun">,</span><span class="pln"> </span><span class="lit">7</span><span class="pun">-</span><span class="lit">1</span><span class="pun">,</span><span class="pln"> </span><span class="lit">8</span><span class="pun">]).</span><span class="pln">format</span><span class="pun">()</span><span class="pln"> </span><span class="com">// "2005-07-08T00:00:00Z"</span></code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">小胖Gil</span>
            <span class="discuss-time">2020.05.28</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这个</font></font><a href="https://code.google.com/p/flexible-js-formatting/" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">轻量级的日期解析库</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">应该解决所有类似的问题。</font><font style="vertical-align: inherit;">我喜欢该库，因为它很容易扩展。</font><font style="vertical-align: inherit;">也有可能（不是很简单，但是就不那么难了）。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">解析示例：</font></font></p>

<pre class="lang-js prettyprint prettyprinted" style=""><code><span class="kwd">var</span><span class="pln"> caseOne </span><span class="pun">=</span><span class="pln"> </span><span class="typ">Date</span><span class="pun">.</span><span class="pln">parseDate</span><span class="pun">(</span><span class="str">"Jul 8, 2005"</span><span class="pun">,</span><span class="pln"> </span><span class="str">"M d, Y"</span><span class="pun">);</span><span class="pln">
</span><span class="kwd">var</span><span class="pln"> caseTwo </span><span class="pun">=</span><span class="pln"> </span><span class="typ">Date</span><span class="pun">.</span><span class="pln">parseDate</span><span class="pun">(</span><span class="str">"2005-07-08"</span><span class="pun">,</span><span class="pln"> </span><span class="str">"Y-m-d"</span><span class="pun">);</span></code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">然后格式化回字符串（您会注意到两种情况给出的结果完全相同）：</font></font></p>

<pre class="lang-js prettyprint prettyprinted" style=""><code><span class="pln">console</span><span class="pun">.</span><span class="pln">log</span><span class="pun">(</span><span class="pln"> caseOne</span><span class="pun">.</span><span class="pln">dateFormat</span><span class="pun">(</span><span class="str">"M d, Y"</span><span class="pun">)</span><span class="pln"> </span><span class="pun">);</span><span class="pln">
console</span><span class="pun">.</span><span class="pln">log</span><span class="pun">(</span><span class="pln"> caseTwo</span><span class="pun">.</span><span class="pln">dateFormat</span><span class="pun">(</span><span class="str">"M d, Y"</span><span class="pun">)</span><span class="pln"> </span><span class="pun">);</span><span class="pln">
console</span><span class="pun">.</span><span class="pln">log</span><span class="pun">(</span><span class="pln"> caseOne</span><span class="pun">.</span><span class="pln">dateFormat</span><span class="pun">(</span><span class="str">"Y-m-d"</span><span class="pun">)</span><span class="pln"> </span><span class="pun">);</span><span class="pln">
console</span><span class="pun">.</span><span class="pln">log</span><span class="pun">(</span><span class="pln"> caseTwo</span><span class="pun">.</span><span class="pln">dateFormat</span><span class="pun">(</span><span class="str">"Y-m-d"</span><span class="pun">)</span><span class="pln"> </span><span class="pun">);</span></code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">若合</span>
            <span class="discuss-time">2020.05.28</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">尽管</font></font><a href="https://stackoverflow.com/a/2587398"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">CMS是正确的</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，认为将字符串传递到parse方法通常是不安全的，但</font><font style="vertical-align: inherit;">15.9.4.2节中</font><font style="vertical-align: inherit;">的新</font></font><a href="http://www.ecma-international.org/publications/files/ECMA-ST/ECMA-262.pdf" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">ECMA-262第5版</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（也称为ES5）规范建议</font></font><code>Date.parse()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">实际上应该处理ISO格式的日期。</font><font style="vertical-align: inherit;">旧的规范没有这样的要求。</font><font style="vertical-align: inherit;">当然，旧的浏览器和某些当前的浏览器仍然不提供此ES5功能。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您的第二个示例没有错。</font><font style="vertical-align: inherit;">它是UTC中指定的日期，由</font></font><code>Date.prototype.toISOString()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">表示，但是以您当地的时区表示。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Tom凯</span>
            <span class="discuss-time">2020.05.28</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">根据</font></font><a href="http://blog.dygraphs.com/2012/03/javascript-and-dates-what-mess.html" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">http://blog.dygraphs.com/2012/03/javascript-and-dates-what-mess.html</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">的格式，“ yyyy / mm / dd”解决了常见问题。</font><font style="vertical-align: inherit;">他说：“请尽可能将日期字符串粘贴到“ YYYY / MM / DD”。它被普遍支持且明确。使用这种格式，所有时间都在本地。</font><font style="vertical-align: inherit;">我已经设置了测试：</font></font><a href="http://jsfiddle.net/jlanus/ND2Qg/432/" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">http</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> : </font><a href="http://jsfiddle.net/jlanus/ND2Qg/432/" rel="nofollow noreferrer"><font style="vertical-align: inherit;">//jsfiddle.net/jlanus/ND2Qg/432/</font></a><font style="vertical-align: inherit;"> 
此格式：+通过使用ymd排序和4位数字的年份避免了日和月顺序的歧义+避免了UTC与本地问题的冲突</font></font><a href="http://blog.dygraphs.com/2012/03/javascript-and-dates-what-mess.html" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">dygraphs的</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">家伙</font><font style="vertical-align: inherit;">通过使用斜杠+ danvk来符合ISO格式</font><font style="vertical-align: inherit;">，他说这种格式在所有浏览器中都很好。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">千羽</span>
            <span class="discuss-time">2020.05.28</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">使用</font></font><a href="https://momentjs.com/docs/#/parsing/string-format/" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">moment.js</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">解析日期：</font></font></p>

<pre class="lang-js prettyprint prettyprinted" style=""><code><span class="kwd">var</span><span class="pln"> caseOne </span><span class="pun">=</span><span class="pln"> moment</span><span class="pun">(</span><span class="str">"Jul 8, 2005"</span><span class="pun">,</span><span class="pln"> </span><span class="str">"MMM D, YYYY"</span><span class="pun">,</span><span class="pln"> </span><span class="kwd">true</span><span class="pun">).</span><span class="pln">toDate</span><span class="pun">();</span><span class="pln">
</span><span class="kwd">var</span><span class="pln"> caseTwo </span><span class="pun">=</span><span class="pln"> moment</span><span class="pun">(</span><span class="str">"2005-07-08"</span><span class="pun">,</span><span class="pln"> </span><span class="str">"YYYY-MM-DD"</span><span class="pun">,</span><span class="pln"> </span><span class="kwd">true</span><span class="pun">).</span><span class="pln">toDate</span><span class="pun">();</span></code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">第三个参数确定严格的解析（从2.3.0版本开始可用）。</font><font style="vertical-align: inherit;">没有它，moment.js可能还会给出错误的结果。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">DavaidTony宝儿</span>
            <span class="discuss-time">2020.05.28</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">疯狂是有办法的。</font><font style="vertical-align: inherit;">通常，如果浏览器可以将日期解释为ISO-8601，它将被解释为日期。</font><font style="vertical-align: inherit;">“ 2005-07-08”属于此阵营，因此被解析为UTC。</font><font style="vertical-align: inherit;">“ 2005年7月8日”不能，因此在当地时间进行了解析。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">看到</font></font><a href="http://blog.dygraphs.com/2012/03/javascript-and-dates-what-mess.html"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">JavaScript和日期，真是麻烦！</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">更多。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">猴子</span>
            <span class="discuss-time">2020.05.28</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在第5版规范发布之前，该</font></font><a href="http://bclary.com/2004/11/07/#a-15.9.4.2" rel="nofollow noreferrer"><code>Date.parse</code></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">方法完全</font></font><em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">依赖</font></font></em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">于</font><em><font style="vertical-align: inherit;">实现</font></em><font style="vertical-align: inherit;">（</font><font style="vertical-align: inherit;">除后者返回数字而不是a之外</font><font style="vertical-align: inherit;">，其他</font><font style="vertical-align: inherit;">方法</font></font><code>new Date(string)</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">等效</font><font style="vertical-align: inherit;">）。</font><font style="vertical-align: inherit;">在第5版规范中，添加了该要求以支持</font><a href="http://www.ecma-international.org/ecma-262/5.1/#sec-15.9.1.15" rel="nofollow noreferrer"><font style="vertical-align: inherit;">简化的</font></a><a href="http://www.ecma-international.org/ecma-262/5.1/#sec-15.9.1.15" rel="nofollow noreferrer"><em><font style="vertical-align: inherit;">（并且略有错误）</font></em></a><a href="http://www.ecma-international.org/ecma-262/5.1/#sec-15.9.1.15" rel="nofollow noreferrer"><font style="vertical-align: inherit;"> ISO-8601</font></a><font style="vertical-align: inherit;">（另请参见</font><a href="https://stackoverflow.com/questions/51715259/what-are-valid-date-time-strings-in-javascript/"><font style="vertical-align: inherit;">JavaScript中有效的日期时间字符串是什么？</font></a><font style="vertical-align: inherit;">）。</font><font style="vertical-align: inherit;">但是除此之外，</font><font style="vertical-align: inherit;">除了必须接受任何</font><font style="vertical-align: inherit;">输出（不说那是什么）</font><font style="vertical-align: inherit;">之外，</font><font style="vertical-align: inherit;">对什么</font><font style="vertical-align: inherit;">/ </font><font style="vertical-align: inherit;">应该接受</font><em><font style="vertical-align: inherit;">没有任何</font></em><font style="vertical-align: inherit;">要求</font><font style="vertical-align: inherit;">。</font></font><a href="http://bclary.com/2004/11/07/#a-15.9.4.2" rel="nofollow noreferrer"><code>Date.parse(string)</code></a><font style="vertical-align: inherit;"></font><code>Date</code><font style="vertical-align: inherit;"></font><a href="http://www.ecma-international.org/ecma-262/5.1/#sec-15.9.1.15" rel="nofollow noreferrer"><font style="vertical-align: inherit;"></font><em><font style="vertical-align: inherit;"></font></em><font style="vertical-align: inherit;"></font></a><font style="vertical-align: inherit;"></font><a href="https://stackoverflow.com/questions/51715259/what-are-valid-date-time-strings-in-javascript/"><font style="vertical-align: inherit;"></font></a><font style="vertical-align: inherit;"></font><em><font style="vertical-align: inherit;"></font></em><font style="vertical-align: inherit;"></font><code>Date.parse</code><font style="vertical-align: inherit;"></font><code>new Date(string)</code><font style="vertical-align: inherit;"></font><code>Date#toString</code><font style="vertical-align: inherit;"></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如2017年的ECMAScript（版本8）的，被要求的实现来解析其输出</font></font><code>Date#toString</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">和</font></font><code>Date#toUTCString</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，但是未指定这些字符串的格式。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">从ECMAScript 2019（版本9）开始，</font></font><a href="http://ecma-international.org/ecma-262/9.0/#sec-date.prototype.tostring" rel="nofollow noreferrer"><code>Date#toString</code></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">和</font><font style="vertical-align: inherit;">的格式</font></font><a href="http://ecma-international.org/ecma-262/9.0/#sec-date.prototype.toutcstring" rel="nofollow noreferrer"><code>Date#toUTCString</code></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">分别指定为：</font></font></p>

<ol>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">ddd MMM DD YYYY HH：mm：ss ZZ [（时区名称）] </font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">例如Tue Jul 10 2018 18:39:58 GMT + 0530（IST）</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">ddd，DD MMM YYYY HH：mm：ss Z </font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">例如 </font><font style="vertical-align: inherit;">2018年7月10日星期二13:09:58 GMT</font></font></li>
</ol>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">提供了2种</font></font><code>Date.parse</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">应在新的实现中可靠解析的</font><font style="vertical-align: inherit;">格式</font><font style="vertical-align: inherit;">（请注意，支持并不普遍，并且不兼容的实现将在一段时间内继续使用）。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我建议手动解析日期字符串，并将</font></font><a href="http://bclary.com/2004/11/07/#a-15.9.3.1" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Date构造函数</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">与年，月和日参数一起使用，以避免产生歧义：</font></font></p>

<pre class="lang-js prettyprint prettyprinted" style=""><code><span class="com">// parse a date in yyyy-mm-dd format</span><span class="pln">
</span><span class="kwd">function</span><span class="pln"> parseDate</span><span class="pun">(</span><span class="pln">input</span><span class="pun">)</span><span class="pln"> </span><span class="pun">{</span><span class="pln">

  </span><span class="kwd">let</span><span class="pln"> parts </span><span class="pun">=</span><span class="pln"> input</span><span class="pun">.</span><span class="pln">split</span><span class="pun">(</span><span class="str">'-'</span><span class="pun">);</span><span class="pln">

  </span><span class="com">// new Date(year, month [, day [, hours[, minutes[, seconds[, ms]]]]])</span><span class="pln">
  </span><span class="kwd">return</span><span class="pln"> </span><span class="kwd">new</span><span class="pln"> </span><span class="typ">Date</span><span class="pun">(</span><span class="pln">parts</span><span class="pun">[</span><span class="lit">0</span><span class="pun">],</span><span class="pln"> parts</span><span class="pun">[</span><span class="lit">1</span><span class="pun">]-</span><span class="lit">1</span><span class="pun">,</span><span class="pln"> parts</span><span class="pun">[</span><span class="lit">2</span><span class="pun">]);</span><span class="pln"> </span><span class="com">// Note: months are 0-based</span><span class="pln">
</span><span class="pun">}</span></code></pre></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
