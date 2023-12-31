---
layout: question
title:  jQuery.click（）与onClick
date:   2020-03-12T06:58:23.000Z
description: 我有一个庞大的jQuery应用程序，并且我将以下两种方法用于点击事件。第一种方法的HTML<div id="myDiv">Some Conte...
img: 
author: 乐小小猪猪
category: question
answer: 8
tags: JavaScript
topic: JavaScript
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我有一个庞大的jQuery应用程序，并且我将以下两种方法用于点击事件。</font></font></p>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">第一种方法</font></font></strong></p>

<h3><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">的HTML</font></font></h3>

<pre><code>&lt;div id="myDiv"&gt;Some Content&lt;/div&gt;
</code></pre>

<h3><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">jQuery的</font></font></h3>

<pre><code>$('#myDiv').click(function(){<font></font>
    //Some code<font></font>
});<font></font>
</code></pre>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">第二种方法</font></font></strong></p>

<h3><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">的HTML</font></font></h3>

<pre><code>&lt;div id="myDiv" onClick="divFunction()"&gt;Some Content&lt;/div&gt;
</code></pre>

<h3><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">JavaScript函数调用</font></font></h3>

<pre><code>function divFunction(){<font></font>
    //Some code<font></font>
}<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我在应用程序中使用第一种或第二种方法。</font><font style="vertical-align: inherit;">哪一个更好？</font><font style="vertical-align: inherit;">性能更好？</font><font style="vertical-align: inherit;">和标准？</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第1030篇《jQuery.click（）与onClick》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Sam蛋蛋Itachi</span>
            <span class="discuss-time">2020.03.12</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">第一种使用</font></font><code>onclick</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">方法不是jQuery，而是简单的Javascript，因此您不会得到jQuery的开销。</font><font style="vertical-align: inherit;">如果您需要将选择器扩展到其他元素而无需将事件处理程序添加到每个元素，则可以通过选择器扩展jQuery方式，但是现在您有了它，是否需要使用jQuery只是一个问题。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">就个人而言，由于您使用的是jQuery，因此我会坚持使用它，因为它是一致的，并且确实使标记与脚本脱钩。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">小胖Green</span>
            <span class="discuss-time">2020.03.12</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">第一种方法是首选。</font><font style="vertical-align: inherit;">它使用</font></font><a href="http://www.quirksmode.org/js/events_advanced.html" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">高级事件注册模型</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，这意味着您可以将多个处理程序附加到同一元素。</font><font style="vertical-align: inherit;">您可以轻松访问事件对象，并且处理程序可以存在于任何函数的范围内。</font><font style="vertical-align: inherit;">而且，它是动态的，即可以随时调用，特别适合动态生成的元素。</font><font style="vertical-align: inherit;">不管您直接使用jQuery，其他库还是直接使用本机方法都没有关系。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">第二种方法使用内联属性，需要大量全局函数（这会导致名称空间污染），并将内容/结构（HTML）与行为（JavaScript）混合在一起。</font><font style="vertical-align: inherit;">不要使用它。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您对性能或标准的问题无法轻易回答。</font><font style="vertical-align: inherit;">两种方法完全不同，并且执行不同的操作。</font><font style="vertical-align: inherit;">第一个比较强大，而第二个则被鄙视（被认为是不好的风格）。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">猴子古一蛋蛋</span>
            <span class="discuss-time">2020.03.12</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">好吧，</font></font><a href="http://en.wikipedia.org/wiki/JQuery" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">jQuery</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">的主要思想之一</font><font style="vertical-align: inherit;">就是将JavaScript与讨厌的</font></font><a href="http://en.wikipedia.org/wiki/HTML" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">HTML</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">代码</font><font style="vertical-align: inherit;">分开</font><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">第一种方法是要走的路。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">DavaidHarry</span>
            <span class="discuss-time">2020.03.12</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">大多数情况下，当性能是唯一标准时，原生JavaScript方法是优于jQuery的更好选择，但是jQuery利用JavaScript并使开发变得容易。</font><font style="vertical-align: inherit;">您可以使用jQuery，因为它不会降低性能。</font><font style="vertical-align: inherit;">在您的特定情况下，性能差异是可以忽略的。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">路易Near番长</span>
            <span class="discuss-time">2020.03.12</span>
          </div>
          <div class="discuss-comment"><pre><code>&lt;whatever onclick="doStuff();" onmouseover="in()" onmouseout="out()" /&gt;
</code></pre>

<p><strong><font style="vertical-align: inherit;"></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">事件实际上</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">对性能不利</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（</font><font style="vertical-align: inherit;">主要是</font><font style="vertical-align: inherit;">在</font></font><em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Internet Explorer中</font></font></em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，请参见图）</font><strong><font style="vertical-align: inherit;">。onclick，onmouseover，onmouseout等</font></strong><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">如果使用</font></font><a href="http://en.wikipedia.org/wiki/Microsoft_Visual_Studio" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Visual Studio进行</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">编码</font><font style="vertical-align: inherit;">，则在使用这些</font><font style="vertical-align: inherit;">代码</font><font style="vertical-align: inherit;">运行页面时，其中的每一个都会创建一个单独的SCRIPT块，占用内存，从而降低性能。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">更不用说您应该</font></font><a href="https://en.wikipedia.org/wiki/Separation_of_concerns" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">分开关注</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">：JavaScript和布局应该分开！</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">最好为这些事件中的任何一个创建evenHandlers，一个事件可以捕获成千上万的项目，而不是为每个事件创建成千上万的单独脚本块！</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（此外，其他所有人都在说。）</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Mandy神乐</span>
            <span class="discuss-time">2020.03.12</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">恕我直言，仅当满足以下条件时，onclick才是.click的首选方法：</font></font></p>

<ul>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">页面上有很多元素</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">单击事件仅注册一个事件</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您担心移动性能/电池寿命</font></font></li>
</ul>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我之所以形成这种观点，是因为移动设备上的JavaScript引擎比同代的台式机慢4至7倍。</font><font style="vertical-align: inherit;">当我访问移动设备上的网站并收到滚动抖动时，我讨厌它，因为jQuery绑定了所有事件，但以牺牲用户体验和电池寿命为代价。</font><font style="vertical-align: inherit;">另一个最近的支持因素，尽管这只应该是***机构关心的问题；），但我们在IE7弹出窗口中显示了一个消息框，指出JavaScript进程要花很长时间...等待或取消。</font><font style="vertical-align: inherit;">每当有很多要通过jQuery绑定的元素时，就会发生这种情况。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">神奇</span>
            <span class="discuss-time">2020.03.12</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">两种方法都</font><font style="vertical-align: inherit;">可以用于不同的目的，</font><font style="vertical-align: inherit;">这两者都不是</font></font><em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">更好的选择</font></font></em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font><code>onClick</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（实际上应该是</font></font><code>onclick</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">）性能稍好一些，但是我非常怀疑您会注意到那里的区别。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">值得注意的是，它们执行不同的操作：</font></font><code>.click</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">可以绑定到任何jQuery集合，而</font></font><code>onclick</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">必须在要</font><font style="vertical-align: inherit;">绑定到其</font><font style="vertical-align: inherit;">的元素上内联使用。</font><font style="vertical-align: inherit;">您也只能将一个事件绑定到using </font></font><code>onclick</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，而</font></font><code>.click</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">让您继续绑定事件。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在我看来，我会保持一致，只</font></font><code>.click</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在各处</font><font style="vertical-align: inherit;">使用它，</font><font style="vertical-align: inherit;">并将</font></font><em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">所有</font></font></em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> JavaScript代码放在一起，并与HTML分开。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">不要使用</font></font><code>onclick</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">除非您知道自己在做什么，否则可能没有任何理由使用它。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">乐小宇宙</span>
            <span class="discuss-time">2020.03.12</span>
          </div>
          <div class="discuss-comment"><p><code>$('#myDiv').click</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">更好，因为它将JavaScript代码与</font></font><a href="http://en.wikipedia.org/wiki/HTML" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">HTML</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">分开</font><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">必须设法使页面</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">行为和结构</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">保持</font><strong><font style="vertical-align: inherit;">不同</font></strong><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">这很有帮助。</font></font></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
