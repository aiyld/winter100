---
layout: question
title:  window.onload与document.onload
date:   2020-03-11T07:09:58.000Z
description: 哪个受到更广泛的支持：window.onload或document.onload？...
img: 
author: 伽罗JinJin西门
category: question
answer: 5
tags: JavaScript
topic: JavaScript
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">哪个受到更广泛的支持：</font></font><code>window.onload</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">或</font></font><code>document.onload</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">？</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第722篇《window.onload与document.onload》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">TomGO</span>
            <span class="discuss-time">2020.03.11</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Window.onload是标准，但是-PS3（基于Netfront）中的Web浏览器不支持window对象，因此您不能在其中使用它。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">ItachiJinJin</span>
            <span class="discuss-time">2020.03.11</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">window.onload但是，它们通常是同一回事。</font><font style="vertical-align: inherit;">同样，body.onload在IE中成为window.onload。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">阿飞小卤蛋</span>
            <span class="discuss-time">2020.03.11</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在Chrome中，window.onload与有所不同</font></font><code>&lt;body onload=""&gt;</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，而Firefox（版本35.0）和IE（版本11）都相同。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您可以通过以下代码段进行探索：</font></font></p>

<pre><code>&lt;!DOCTYPE html&gt;<font></font>
&lt;html xmlns="http://www.w3.org/1999/xhtml"&gt;<font></font>
    &lt;head&gt;<font></font>
        &lt;meta http-equiv="Content-Type" content="text/html; charset=utf-8" /&gt;<font></font>
        &lt;!--import css here--&gt;<font></font>
        &lt;!--import js scripts here--&gt;<font></font>
<font></font>
        &lt;script language="javascript"&gt;<font></font>
<font></font>
            function bodyOnloadHandler() {<font></font>
                console.log("body onload");<font></font>
            }<font></font>
<font></font>
            window.onload = function(e) {<font></font>
                console.log("window loaded");<font></font>
            };<font></font>
        &lt;/script&gt;<font></font>
    &lt;/head&gt;<font></font>
<font></font>
    &lt;body onload="bodyOnloadHandler()"&gt;<font></font>
<font></font>
        Page contents go here.<font></font>
<font></font>
    &lt;/body&gt;<font></font>
&lt;/html&gt;<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在Chrome控制台中，您将同时看到“窗口加载”（首先出现）和“主体加载”。</font><font style="vertical-align: inherit;">但是，您将在Firefox和IE中看到“ body onload”。</font><font style="vertical-align: inherit;">如果您</font></font><code>window.onload.toString()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在IE＆FF的控制台中</font><font style="vertical-align: inherit;">运行“ </font><font style="vertical-align: inherit;">”，则会看到：</font></font></p>

<blockquote>
  <p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">“函数onload（event）{bodyOnloadHandler（）}”</font></font></p>
</blockquote>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这意味着赋值“ window.onload = function（e）...”被覆盖。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">GO前端</span>
            <span class="discuss-time">2020.03.11</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">总的想法是，</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在window.onload火灾</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">时文档的窗口</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">准备演示</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">和</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">document.onload火灾</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">的时候</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">DOM树</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（文档内的标记代码生成）的</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">完成</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">理想情况下，订阅</font></font><a href="http://en.wikipedia.org/wiki/DOM_events" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">DOM树事件</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，可以通过Javascript进行屏幕外操作，</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">几乎不</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">占用</font><strong><font style="vertical-align: inherit;">CPU负载</font></strong><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">相反，</font><font style="vertical-align: inherit;">当尚未请求，解析和加载多个外部资源时</font><font style="vertical-align: inherit;">，</font></font><strong><code>window.onload</code></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">可能</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">要花一些时间</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">►测试场景：</font></font></strong></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">要观察差异以及</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">选择</font><strong><font style="vertical-align: inherit;">的浏览器如何</font></strong></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">实现</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">上述</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">事件处理程序</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，只需将以下代码插入文档的</font></font><code>&lt;body&gt;</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">--标记中。</font></font></p>

<pre><code>&lt;script language="javascript"&gt;<font></font>
window.tdiff = []; fred = function(a,b){return a-b;};<font></font>
window.document.onload = function(e){ <font></font>
    console.log("document.onload", e, Date.now() ,window.tdiff,  <font></font>
    (window.tdiff[0] = Date.now()) &amp;&amp; window.tdiff.reduce(fred) ); <font></font>
}<font></font>
window.onload = function(e){ <font></font>
    console.log("window.onload", e, Date.now() ,window.tdiff, <font></font>
    (window.tdiff[1] = Date.now()) &amp;&amp; window.tdiff.reduce(fred) ); <font></font>
}<font></font>
&lt;/script&gt;<font></font>
</code></pre>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">►结果：</font></font></strong></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这是由此产生的行为，对于Chrome v20（可能是大多数当前的浏览器）而言，是可观察到的。 </font></font></p>

<ul>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">没有</font></font><code>document.onload</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">事件。</font></font></li>
<li><code>onload</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在中声明时触发两次，在中声明时触发</font></font><code>&lt;body&gt;</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">一次</font></font><code>&lt;head&gt;</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（事件在此充当</font></font><code>document.onload</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">）。</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">根据计数器的状态进行计数和操作可以模拟两种事件行为。 </font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">或者</font></font><code>window.onload</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，在HTML- </font></font><code>&lt;head&gt;</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">元素</font><font style="vertical-align: inherit;">的范围内</font><font style="vertical-align: inherit;">声明</font><font style="vertical-align: inherit;">事件处理程序</font><font style="vertical-align: inherit;">。</font></font></li>
</ul>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">►示例项目：</font></font></strong></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">上面的代码摘自</font></font><a href="https://github.com/lsauer/KeyBoarder/tree/gh-pages" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">该项目的</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">代码库（</font></font><code>index.html</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">和</font></font><code>keyboarder.js</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">）。</font></font></p>

<hr>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">有关</font></font><a href="https://developer.mozilla.org/en-US/docs/DOM/window#Event_handlers" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">window对象</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">的</font><a href="https://developer.mozilla.org/en-US/docs/DOM/window#Event_handlers" rel="noreferrer"><font style="vertical-align: inherit;">事件处理程序的</font></a><font style="vertical-align: inherit;">列表</font><font style="vertical-align: inherit;">，请参考MDN文档。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">猿前端前端</span>
            <span class="discuss-time">2020.03.11</span>
          </div>
          <div class="discuss-comment"><h2><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">他们什么时候开火？</font></font></h2>

<p><a href="https://developer.mozilla.org/en-US/docs/Web/API/GlobalEventHandlers.onload" rel="noreferrer"><code>window.onload</code></a></p>

<ul>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">默认情况下，会在加载整个页面（</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">包括</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">其内容（图像，CSS，脚本等））</font><font style="vertical-align: inherit;">时触发</font><font style="vertical-align: inherit;">。</font></font></li>
</ul>

<p>In some browsers it now takes over the role of <code>document.onload</code> and fires when the DOM is ready as well.</p>

<p><code>document.onload</code></p>

<ul>
<li>It is called when the DOM is ready which can be <strong>prior</strong> to images and other external content is loaded.</li>
</ul>

<h2>How well are they supported?</h2>

<p><code>window.onload</code> appears to be the most widely supported. In fact, some of the most modern browsers have in a sense replaced <code>document.onload</code> with <code>window.onload</code>.</p>

<p>Browser support issues are most likely the reason why many people are starting to use libraries such as <a href="http://jquery.com/" rel="noreferrer">jQuery</a> to handle the checking for the document being ready, like so:</p>

<pre><code>$(document).ready(function() { /* code here */ });<font></font>
$(function() { /* code here */ });<font></font>
</code></pre>

<hr>

<p>For the purpose of history. <code>window.onload</code> vs <code>body.onload</code>:</p>

<blockquote>
  <p>A similar question was asked on <a href="http://www.codingforums.com/archive/index.php/t-106229.html" rel="noreferrer">codingforums</a> a while
  back regarding the usage of <code>window.onload</code> over <code>body.onload</code>. The
  result seemed to be that you should use <code>window.onload</code> because it is
  good to separate your structure from the action.</p>
</blockquote></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
