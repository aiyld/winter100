---
layout: question
title:  $ {document）.ready（）的非jQuery等效项是什么？
date:   2020-03-16T04:11:57.000Z
description: 什么是非jQuery等效项$(document).ready()？...
img: 
author: 小宇宙古一
category: question
answer: 7
tags: JavaScript
topic: JavaScript
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">什么是非jQuery等效项</font></font><code>$(document).ready()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">？</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第1710篇《$ {document）.ready（）的非jQuery等效项是什么？》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">小宇宙卡卡西</span>
            <span class="discuss-time">2020.03.16</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在普通的JavaScript中，没有库？</font><font style="vertical-align: inherit;">这是一个错误。</font></font><code>$</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">只是一个标识符，除非您定义它，否则是未定义的。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">jQuery将</font></font><code>$</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">其</font><font style="vertical-align: inherit;">定义</font><font style="vertical-align: inherit;">为自己的“所有对象”（也称为，</font></font><code>jQuery</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">因此您可以在不与其他库冲突的情况下使用它）。</font><font style="vertical-align: inherit;">如果您不使用jQuery（或其他定义它的库），则</font></font><code>$</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">不会被定义。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">还是您在问普通JavaScript中的等效词是什么？</font><font style="vertical-align: inherit;">在这种情况下，您可能想要</font></font><a href="https://developer.mozilla.org/en/DOM/window.onload" rel="noreferrer"><code>window.onload</code></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，它并不完全等效，但是是在原始JavaScript中接近相同效果的最快，最简单的方法。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">西里Mandy</span>
            <span class="discuss-time">2020.03.16</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在最近的浏览器中，最简单的方法是使用适当的</font></font><a href="https://developer.mozilla.org/en-US/docs/Web/API/GlobalEventHandlers" rel="nofollow noreferrer"><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">GlobalEventHandlers</font></font></strong></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，</font></font><em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">onDOMContentLoaded</font></font></em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，</font></font><em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">onload</font></font></em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，</font></font><em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">onloadeddata</font></font></em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（...）</font></font></p>

<p></p><div class="snippet" data-lang="js" data-hide="false" data-console="true" data-babel="false">
<div class="snippet-code">
<pre class="snippet-code-js lang-js prettyprint-override"><code>onDOMContentLoaded = (function(){ console.log("DOM ready!") })()<font></font>
<font></font>
onload = (function(){ console.log("Page fully loaded!") })()<font></font>
<font></font>
onloadeddata = (function(){ console.log("Data loaded!") })()</code></pre>
</div>
</div>
<p></p>

<p><em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">当初始HTML文档已完全加载和解析时，无需等待样式表，图像和子帧完成加载，就会触发DOMContentLoaded事件。</font><font style="vertical-align: inherit;">完全不同的事件加载应仅用于检测页面已满。</font><font style="vertical-align: inherit;">在DOMContentLoaded更合适的地方使用负载是一个非常普遍的错误，因此要谨慎。</font></font></em></p>

<p><a href="https://developer.mozilla.org/en-US/docs/Web/Events/DOMContentLoaded" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">https://developer.mozilla.org/zh-CN/docs/Web/Events/DOMContentLoaded</font></font></a></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">使用的函数是IIFE，在这种情况下非常有用，因为它在准备就绪时会触发自身：</font></font></p>

<p><a href="https://en.wikipedia.org/wiki/Immediately-invoked_function_expression" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">https://zh.wikipedia.org/wiki/立即调用功能_表达式</font></font></a></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">将它放在所有脚本的末尾显然更合适。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在ES6中，我们还可以将其编写为箭头函数： </font></font></p>

<p></p><div class="snippet" data-lang="js" data-hide="false" data-console="true" data-babel="false">
<div class="snippet-code">
<pre class="snippet-code-js lang-js prettyprint-override"><code>onload = (() =&gt; { console.log("ES6 page fully loaded!") })()</code></pre>
</div>
</div>
<p></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">最好是使用DOM元素，我们可以等待触发箭头IIFE的任何变量准备就绪。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">行为将相同，但对内存的影响较小。</font></font></p>

<p></p><div class="snippet" data-lang="js" data-hide="false" data-console="true" data-babel="false">
<div class="snippet-code">
<pre class="snippet-code-js lang-js prettyprint-override"><code>footer = (() =&gt; { console.log("Footer loaded!") })()</code></pre>
<pre class="snippet-code-html lang-html prettyprint-override"><code>&lt;div id="footer"&gt;</code></pre>
</div>
</div>
<p></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在许多情况下，</font><font style="vertical-align: inherit;">至少在我的浏览器中</font><font style="vertical-align: inherit;">，</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">文档</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">对象也会</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在就绪时</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">触发</font><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">语法非常好，但是需要进一步测试兼容性。</font></font></p>

<pre><code>document=(()=&gt;{    /*Ready*/   })()
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">古一斯丁猴子</span>
            <span class="discuss-time">2020.03.16</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">正文onLoad也可以是一种替代方法：</font></font></p>

<pre><code>&lt;html&gt;<font></font>
&lt;head&gt;&lt;title&gt;Body onLoad Exmaple&lt;/title&gt;<font></font>
<font></font>
&lt;script type="text/javascript"&gt;<font></font>
    function window_onload() {<font></font>
        //do something<font></font>
    }<font></font>
&lt;/script&gt;<font></font>
<font></font>
&lt;/head&gt;<font></font>
&lt;body onLoad="window_onload()"&gt;<font></font>
<font></font>
&lt;/body&gt;<font></font>
&lt;/html&gt;<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">逆天Jim</span>
            <span class="discuss-time">2020.03.16</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">超过90％的浏览器都支持DOMContentLoaded，</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这是一个基于标准的替代品，</font><strong><font style="vertical-align: inherit;">但IE8不支持（所以下面的代码被JQuery用于浏览器支持）</font></strong><font style="vertical-align: inherit;">：</font></font></p>

<pre><code>document.addEventListener("DOMContentLoaded", function(event) { <font></font>
  //do work<font></font>
});<font></font>
</code></pre>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">jQuery的本机功能</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">比window.onload复杂得多，如下所示。</font></font></p>

<pre><code>function bindReady(){<font></font>
    if ( readyBound ) return;<font></font>
    readyBound = true;<font></font>
<font></font>
    // Mozilla, Opera and webkit nightlies currently support this event<font></font>
    if ( document.addEventListener ) {<font></font>
        // Use the handy event callback<font></font>
        document.addEventListener( "DOMContentLoaded", function(){<font></font>
            document.removeEventListener( "DOMContentLoaded", arguments.callee, false );<font></font>
            jQuery.ready();<font></font>
        }, false );<font></font>
<font></font>
    // If IE event model is used<font></font>
    } else if ( document.attachEvent ) {<font></font>
        // ensure firing before onload,<font></font>
        // maybe late but safe also for iframes<font></font>
        document.attachEvent("onreadystatechange", function(){<font></font>
            if ( document.readyState === "complete" ) {<font></font>
                document.detachEvent( "onreadystatechange", arguments.callee );<font></font>
                jQuery.ready();<font></font>
            }<font></font>
        });<font></font>
<font></font>
        // If IE and not an iframe<font></font>
        // continually check to see if the document is ready<font></font>
        if ( document.documentElement.doScroll &amp;&amp; window == window.top ) (function(){<font></font>
            if ( jQuery.isReady ) return;<font></font>
<font></font>
            try {<font></font>
                // If IE is used, use the trick by Diego Perini<font></font>
                // http://javascript.nwbox.com/IEContentLoaded/<font></font>
                document.documentElement.doScroll("left");<font></font>
            } catch( error ) {<font></font>
                setTimeout( arguments.callee, 0 );<font></font>
                return;<font></font>
            }<font></font>
<font></font>
            // and execute any waiting functions<font></font>
            jQuery.ready();<font></font>
        })();<font></font>
    }<font></font>
<font></font>
    // A fallback to window.onload, that will always work<font></font>
    jQuery.event.add( window, "load", jQuery.ready );<font></font>
}<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">蛋蛋前端</span>
            <span class="discuss-time">2020.03.16</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">从ECMA上可以完美运行</font></font></p>

<pre><code>document.addEventListener("DOMContentLoaded", function() {<font></font>
  // code...<font></font>
});<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">之所以</font></font><code>window.onload</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">不等于JQuery，</font></font><code>$(document).ready</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">是因为</font></font><code>$(document).ready</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在</font></font><code>window.onload</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">检查所有元素（包括外部资产和图像）</font><font style="vertical-align: inherit;">时仅等待DOM树</font><font style="vertical-align: inherit;">。</font></font></p>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">编辑</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">：添加了IE8和更旧的等效版本，这要感谢</font></font><a href="https://stackoverflow.com/users/63849/jan-derk"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Jan Derk</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">的观察。</font><font style="vertical-align: inherit;">您可以</font></font><a href="https://developer.mozilla.org/en-US/docs/Web/Events/readystatechange" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">通过以下链接</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在MDN </font><a href="https://developer.mozilla.org/en-US/docs/Web/Events/readystatechange" rel="noreferrer"><font style="vertical-align: inherit;">上</font></a><font style="vertical-align: inherit;">阅读此代码的源代码</font><font style="vertical-align: inherit;">：</font></font></p>

<pre><code>// alternative to DOMContentLoaded<font></font>
document.onreadystatechange = function () {<font></font>
    if (document.readyState == "interactive") {<font></font>
        // Initialize your application or run some code.<font></font>
    }<font></font>
}<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">除了以外，还有其他选择</font></font><code>"interactive"</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">有关</font><font style="vertical-align: inherit;">详细信息，</font><font style="vertical-align: inherit;">请参见</font></font><a href="https://developer.mozilla.org/en-US/docs/Web/Events/readystatechange" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">MDN</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">链接。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">伽罗乐</span>
            <span class="discuss-time">2020.03.16</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我整理了一点</font></font></p>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">domready.js</font></font></strong></p>

<pre><code>(function(exports, d) {<font></font>
  function domReady(fn, context) {<font></font>
<font></font>
    function onReady(event) {<font></font>
      d.removeEventListener("DOMContentLoaded", onReady);<font></font>
      fn.call(context || exports, event);<font></font>
    }<font></font>
<font></font>
    function onReadyIe(event) {<font></font>
      if (d.readyState === "complete") {<font></font>
        d.detachEvent("onreadystatechange", onReadyIe);<font></font>
        fn.call(context || exports, event);<font></font>
      }<font></font>
    }<font></font>
<font></font>
    d.addEventListener &amp;&amp; d.addEventListener("DOMContentLoaded", onReady) ||<font></font>
    d.attachEvent      &amp;&amp; d.attachEvent("onreadystatechange", onReadyIe);<font></font>
  }<font></font>
<font></font>
  exports.domReady = domReady;<font></font>
})(window, document);<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如何使用它</font></font></p>

<pre><code>&lt;script src="domready.js"&gt;&lt;/script&gt;<font></font>
&lt;script&gt;<font></font>
  domReady(function(event) {<font></font>
    alert("dom is ready!");<font></font>
  });<font></font>
&lt;/script&gt;<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您还可以通过传递第二个参数来更改回调运行的上下文</font></font></p>

<pre><code>function init(event) {<font></font>
  alert("check the console");<font></font>
  this.log(event);<font></font>
}<font></font>
<font></font>
domReady(init, console);<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">TomGO小小</span>
            <span class="discuss-time">2020.03.16</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">有趣的</font></font><code>$(document).ready()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">是，它可以在之前触发</font></font><code>window.onload</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">加载功能会一直等到所有内容加载完毕，包括外部资源和图像。</font></font><code>$(document).ready</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">但是，当DOM树完成并且可以进行操作时会触发。</font><font style="vertical-align: inherit;">如果您想在没有jQuery的情况下实现DOM就绪，则可以签入此库。</font><font style="vertical-align: inherit;">有人</font></font><code>ready</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">从jQuery中</font><font style="vertical-align: inherit;">提取了</font><font style="vertical-align: inherit;">一部分。</font><font style="vertical-align: inherit;">它的大小不一，您可能会发现它很有用：</font></font></p>

<p><a href="https://code.google.com/archive/p/domready/" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">随时可以在Google Code中使用</font></font></a></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
