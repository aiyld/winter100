---
layout: question
title:  event.stopPropagation和event.preventDefault有什么区别？
date:   2020-03-10T06:25:54.000Z
description: 他们似乎在做同样的事情……是现代的还是老的？还是不同的浏览器支持它们？当我自己处理事件（没有框架）时，我总是检查两者并执行（如果存在）。（我也是ret...
img: 
author: GO西门
category: question
answer: 3
tags: JavaScript
topic: JavaScript
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">他们似乎在做同样的事情……是现代的还是老的？</font><font style="vertical-align: inherit;">还是不同的浏览器支持它们？</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">当我自己处理事件（没有框架）时，我总是检查两者并执行（如果存在）。</font><font style="vertical-align: inherit;">（我也是</font></font><code>return false</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，但我有一种感觉不适用于附带的事件</font></font><code>node.addEventListener</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">）。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">那么为什么两者都呢？</font><font style="vertical-align: inherit;">我应该继续检查两者吗？</font><font style="vertical-align: inherit;">还是实际上有区别？</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（我知道，很多问题，但都是相同的=）</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第505篇《event.stopPropagation和event.preventDefault有什么区别？》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">前端Mandy</span>
            <span class="discuss-time">2020.03.10</span>
          </div>
          <div class="discuss-comment"><p></p><div class="snippet" data-lang="js" data-hide="false" data-console="true" data-babel="false">
<div class="snippet-code">
<pre class="snippet-code-js lang-js prettyprint-override"><code>$("#but").click(function(event){<font></font>
console.log("hello");<font></font>
  event.preventDefault();<font></font>
 });<font></font>
<font></font>
<font></font>
$("#foo").click(function(){<font></font>
 alert("parent click event fired !");<font></font>
});</code></pre>
<pre class="snippet-code-html lang-html prettyprint-override"><code>&lt;script src="https://ajax.googleapis.com/ajax/libs/jquery/2.1.1/jquery.min.js"&gt;&lt;/script&gt;<font></font>
&lt;div id="foo"&gt;<font></font>
  &lt;button id="but"&gt;button&lt;/button&gt;<font></font>
&lt;/div&gt;</code></pre>
</div>
</div>
<p></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">白月光</span>
            <span class="discuss-time">2020.03.10</span>
          </div>
          <div class="discuss-comment"><p><code>event.preventDefault();</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> 停止发生元素的默认操作。</font></font></p>

<p><code>event.stopPropagation();</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> 防止事件使DOM树冒泡，防止任何父处理程序收到该事件的通知。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">例如，如果是的点击方法连接内的链接</font></font><code>DIV</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">或</font></font><code>FORM</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">还附加有点击的方法，它会阻止</font></font><code>DIV</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">或</font></font><code>FORM</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">从发射单击方法。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">小小</span>
            <span class="discuss-time">2020.03.10</span>
          </div>
          <div class="discuss-comment"><p><code>stopPropagation</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> 阻止事件冒泡事件链。</font></font></p>

<p><code>preventDefault</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> 阻止浏览器对该事件执行默认操作。</font></font></p>

<h2><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">例子</font></font></h2>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">preventDefault</font></font></strong></p>

<p></p><div class="snippet" data-lang="js" data-hide="false" data-console="true" data-babel="false">
<div class="snippet-code">
<pre class="snippet-code-js lang-js prettyprint-override"><code>$("#but").click(function (event) {<font></font>
  event.preventDefault()<font></font>
})<font></font>
$("#foo").click(function () {<font></font>
  alert("parent click event fired!")<font></font>
})</code></pre>
<pre class="snippet-code-html lang-html prettyprint-override"><code>&lt;script src="https://ajax.googleapis.com/ajax/libs/jquery/2.1.1/jquery.min.js"&gt;&lt;/script&gt;<font></font>
&lt;div id="foo"&gt;<font></font>
  &lt;button id="but"&gt;button&lt;/button&gt;<font></font>
&lt;/div&gt;</code></pre>
</div>
</div>
<p></p>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">停止传播</font></font></strong></p>

<p></p><div class="snippet" data-lang="js" data-hide="false" data-console="true" data-babel="false">
<div class="snippet-code">
<pre class="snippet-code-js lang-js prettyprint-override"><code>$("#but").click(function (event) {<font></font>
  event.stopPropagation()<font></font>
})<font></font>
$("#foo").click(function () {<font></font>
  alert("parent click event fired!")<font></font>
})</code></pre>
<pre class="snippet-code-html lang-html prettyprint-override"><code>&lt;script src="https://ajax.googleapis.com/ajax/libs/jquery/2.1.1/jquery.min.js"&gt;&lt;/script&gt;<font></font>
&lt;div id="foo"&gt;<font></font>
  &lt;button id="but"&gt;button&lt;/button&gt;<font></font>
&lt;/div&gt;</code></pre>
</div>
</div>
<p></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">使用</font></font><code>stopPropagation</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，只有</font></font><strong><code>button</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">的点击处理程序会</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">被调用，而</font></font><strong><code>div</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">的点击处理程序</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">永远不会触发。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">就像您使用一样</font></font><code>preventDefault</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，只有浏览器的默认操作被停止，但div的单击处理程序仍然会触发。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">以下是有关MDN中DOM事件属性和方法的一些文档：</font></font></p>

<ul>
<li><a href="https://developer.mozilla.org/en-US/docs/Web/API/Event/cancelBubble" rel="noreferrer"><code>event.cancelBubble</code></a></li>
<li><a href="https://developer.mozilla.org/en-US/docs/Web/API/Event/preventDefault" rel="noreferrer"><code>event.preventDefault()</code></a></li>
<li><a href="https://developer.mozilla.org/en-US/docs/Web/API/Event/returnValue" rel="noreferrer"><code>event.returnValue</code></a></li>
<li><a href="https://developer.mozilla.org/en-US/docs/Web/API/Event/stopPropagation" rel="noreferrer"><code>event.stopPropagation()</code></a></li>
</ul>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">对于IE9和FF，您可以只使用preventDefault和stopPropagation。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">为了支持IE8和更低版本，请替换</font></font><code>stopPropagation</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">为</font></font><code>cancelBubble</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">和替换</font></font><code>preventDefault</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">为</font></font><code>returnValue</code></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
