---
layout: question
title:  window.onload与$（document）.ready（）
date:   2020-03-09T14:26:08.000Z
description: JavaScript window.onload和jQuery $(document).ready()方法之间有什么区别？...
img: 
author: 樱泡芙
category: question
answer: 10
tags: JavaScript
topic: JavaScript
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">JavaScript </font></font><a href="https://developer.mozilla.org/en/docs/Web/API/GlobalEventHandlers/onload" rel="noreferrer"><code>window.onload</code></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">和jQuery </font></font><a href="https://api.jquery.com/ready/" rel="noreferrer"><code>$(document).ready()</code></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">方法</font><font style="vertical-align: inherit;">之间有什么区别</font><font style="vertical-align: inherit;">？</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第305篇《window.onload与$（document）.ready（）》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">伽罗卡卡西</span>
            <span class="discuss-time">2020.03.09</span>
          </div>
          <div class="discuss-comment"><p>window.onload is provided by DOM api and it says " the load event fires when a given resource has loaded".</p>

<p>"The load event fires at the end of the document loading process. At this point, <strong>all of the objects</strong> in the document are in the DOM, and all the images, scripts, links and sub-frames have finished loading."
<a href="https://developer.mozilla.org/en-US/docs/Web/API/GlobalEventHandlers/onload" rel="nofollow noreferrer">DOM onload</a></p>

<p>But in jQuery $(document).ready() will only run once the page Document Object Model (DOM) is ready for JavaScript code to execute. This does not include images, scripts, iframes etc. <a href="https://learn.jquery.com/using-jquery-core/document-ready/" rel="nofollow noreferrer">jquery ready event</a></p>

<p>So the jquery ready method will run <strong>earlier</strong> than the the dom onload event.</p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">十三凯</span>
            <span class="discuss-time">2020.03.09</span>
          </div>
          <div class="discuss-comment"><p><code>Document.ready</code> (a jQuery event) will fire when all the elements are in place, and they can be referenced in the JavaScript code, but the content is not necessarily loaded. <code>Document.ready</code> executes when the HTML document is loaded.</p>

<pre><code>$(document).ready(function() {<font></font>
<font></font>
    // Code to be executed<font></font>
    alert("Document is ready");<font></font>
});<font></font>
</code></pre>

<p>The <code>window.load</code> however will wait for the page to be fully loaded. This includes inner frames, images, etc.</p>

<pre><code>$(window).load(function() {<font></font>
<font></font>
    //Fires when the page is loaded completely<font></font>
    alert("window is loaded");<font></font>
});<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">蛋蛋伽罗猿</span>
            <span class="discuss-time">2020.03.09</span>
          </div>
          <div class="discuss-comment"><p>The document.ready event occurs when the HTML document has been loaded, and the <code>window.onload</code> event occurs always later, when all content (images, etc) has been loaded.</p>

<p>You can use the <code>document.ready</code> event if you want to intervene "early" in the rendering process, without waiting for the images to load.
If you need the images (or any other "content") ready before your script "does something", you need to wait until <code>window.onload</code>.</p>

<p>For instance, if you are implementing a "Slide Show" pattern, and you need to perform calculations based on image sizes, you may want to wait until <code>window.onload</code>. Otherwise, you might experience some random problems, depending on how fast the images will get loaded. Your script would be running concurrently with the thread that loads images. If your script is long enough, or the server is fast enough, you may not notice a problem, if images happen to arrive in time. But the safest practice would be allowing for images to get loaded.</p>

<p><code>document.ready</code> could be a nice event for you to show some "loading..." sign to users, and upon <code>window.onload</code>, you can complete any scripting that needed resources loaded, and then finally remove the "Loading..." sign.</p>

<p>Examples :-</p>

<pre><code>// document ready events<font></font>
$(document).ready(function(){<font></font>
     alert("document is ready..");<font></font>
})<font></font>
<font></font>
// using JQuery<font></font>
$(function(){<font></font>
   alert("document is ready..");<font></font>
})<font></font>
<font></font>
// window on load event<font></font>
function myFunction(){<font></font>
  alert("window is loaded..");<font></font>
}<font></font>
window.onload = myFunction;<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Mandy猴子</span>
            <span class="discuss-time">2020.03.09</span>
          </div>
          <div class="discuss-comment"><p><code>window.onload</code> is a JavaScript inbuilt function. <code>window.onload</code> trigger when the HTML page loaded. <code>window.onload</code> can be written only once.</p>

<p><code>document.ready</code> is a function of the jQuery library. <code>document.ready</code> triggers when HTML and all JavaScript code, CSS, and images which are included in the HTML file are completely loaded.
<code>document.ready</code> can be written multiple times according to requirements.</p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">梅卡卡西Eva</span>
            <span class="discuss-time">2020.03.09</span>
          </div>
          <div class="discuss-comment"><p><strong>window.onload:</strong> <em>A normal JavaScript event.</em></p>

<p><strong>document.ready:</strong> <em>A specific jQuery event when the entire HTML has been loaded.</em></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">TomTom乐</span>
            <span class="discuss-time">2020.03.09</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">一个</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Windows负载</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">事件触发时，所有的页面上的内容满载包括DOM（文档对象模型）的内容和</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">异步的JavaScript</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">框架和图像</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">您还可以使用body onload =。</font><font style="vertical-align: inherit;">两者是相同的；</font></font><code>window.onload = function(){}</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">并且</font></font><code>&lt;body onload="func();"&gt;</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">是使用同一事件的不同方式。</font></font></p>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">jQuery</font></font><code>$document.ready</code></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">函数事件的执行时间比</font></font><code>window.onload</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">DOM（文档对象模型）加载到您的页面上的时间要</font><font style="vertical-align: inherit;">早一些</font><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">它不会等待</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">图像和框架完全加载</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">摘自以下文章：与...
 </font></font><a href="http://www.dotnetbull.com/2013/08/document-ready-vs-window-onload.html" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">有何</font></font><code>$document.ready()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">不同</font></font><code>window.onload()</code></a></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">番长西里神无</span>
            <span class="discuss-time">2020.03.09</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在</font></font><code>$(document).ready()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Internet Explorer </font><font style="vertical-align: inherit;">上使用</font><font style="vertical-align: inherit;">时</font><font style="vertical-align: inherit;">要小心</font><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">如果</font><font style="vertical-align: inherit;">在整个文档加载</font></font><em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">之前</font></font></em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> HTTP请求被中断</font><font style="vertical-align: inherit;">（例如，当页面流向浏览器时，单击了另一个链接），IE将触发该</font></font><code>$(document).ready</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">事件。  </font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果</font></font><code>$(document).ready()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">事件中的</font><font style="vertical-align: inherit;">任何代码</font><font style="vertical-align: inherit;">引用DOM对象，则可能找不到这些对象，并且可能会发生Javascript错误。</font><font style="vertical-align: inherit;">要么保护您对那些对象的引用，要么延迟将那些对象引用到window.load事件的代码。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我无法在其他浏览器（特别是Chrome和Firefox）中重现此问题</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">老丝</span>
            <span class="discuss-time">2020.03.09</span>
          </div>
          <div class="discuss-comment"><p></p><div class="snippet" data-lang="js" data-hide="false" data-console="true" data-babel="false">
<div class="snippet-code">
<pre class="snippet-code-js lang-js prettyprint-override"><code>$(document).ready(function() {<font></font>
<font></font>
    // Executes when the HTML document is loaded and the DOM is ready<font></font>
    alert("Document is ready");<font></font>
});<font></font>
<font></font>
// .load() method deprecated from jQuery 1.8 onward<font></font>
$(window).on("load", function() {<font></font>
<font></font>
     // Executes when complete page is fully loaded, including<font></font>
     // all frames, objects and images<font></font>
     alert("Window is loaded");<font></font>
});</code></pre>
<pre class="snippet-code-html lang-html prettyprint-override"><code>&lt;script src="https://ajax.googleapis.com/ajax/libs/jquery/1.7.2/jquery.min.js"&gt;&lt;/script&gt;</code></pre>
</div>
</div>
<p></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">斯丁Green</span>
            <span class="discuss-time">2020.03.09</span>
          </div>
          <div class="discuss-comment"><p><code>$(document).ready()</code> is a jQuery event.  JQuery’s <code>$(document).ready()</code> method gets called as soon as the DOM is ready (which means that the browser has parsed the HTML and built the DOM tree). This allows you to run code as soon as the document is ready to be manipulated.  </p>

<p>For example, if a browser supports the DOMContentLoaded event (as many non-IE browsers do), then it will fire on that event. (Note that the DOMContentLoaded event was only added to IE in IE9+.)</p>

<p>Two syntaxes can be used for this: </p>

<pre><code>$( document ).ready(function() {<font></font>
   console.log( "ready!" );<font></font>
});<font></font>
</code></pre>

<p>Or the shorthand version:</p>

<pre><code>$(function() {<font></font>
   console.log( "ready!" );<font></font>
});<font></font>
</code></pre>

<p>Main points for <code>$(document).ready()</code>:</p>

<ul>
<li>It will not wait for the images to be loaded. </li>
<li>Used to execute JavaScript when the DOM is completely loaded. Put event handlers here.</li>
<li>Can be used multiple times.</li>
<li>Replace <code>$</code> with <code>jQuery</code> when you receive "$ is not defined."</li>
<li>Not used if you want to manipulate images. Use <code>$(window).load()</code> instead.  </li>
</ul>

<p><code>window.onload()</code> is a native JavaScript function. The <code>window.onload()</code> event fires when all the content on your page has loaded, including the DOM (document object model), banner ads and images. Another difference between the two is that, while we can have more than one <code>$(document).ready()</code> function, we can only have one <code>onload</code> function.</p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">null</span>
            <span class="discuss-time">2020.03.09</span>
          </div>
          <div class="discuss-comment"><p><code>window.onload</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">是内置的JavaScript事件，但是由于其实现在</font><font style="vertical-align: inherit;">浏览器（Firefox，Internet Explorer 6，Internet Explorer 8和</font><a href="http://en.wikipedia.org/wiki/Opera_%28web_browser%29" rel="noreferrer"><font style="vertical-align: inherit;">Opera</font></a><font style="vertical-align: inherit;">）</font><font style="vertical-align: inherit;">之间</font><font style="vertical-align: inherit;">存在</font></font><em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">细微的</font></font></em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">怪癖</font><font style="vertical-align: inherit;">，因此jQuery提供了</font><font style="vertical-align: inherit;">，可以将这些抽象化，并在页面DOM准备就绪后立即触发（不等待图像等）。</font></font><a href="http://en.wikipedia.org/wiki/Opera_%28web_browser%29" rel="noreferrer"><font style="vertical-align: inherit;"></font></a><font style="vertical-align: inherit;"></font><code>document.ready</code><font style="vertical-align: inherit;"></font></p>

<p><code>$(document).ready</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（请注意，</font></font><em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">不是</font></font></em> <code>document.ready</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，它是未定义的）是一个jQuery函数，它包装并为</font><font style="vertical-align: inherit;">以下事件</font><font style="vertical-align: inherit;">提供了</font></font><em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">一致性</font></font></em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">：</font></font></p>

<ul>
<li><code>document.ondomcontentready</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">// </font></font><code>document.ondomcontentloaded</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">-一个新事件，该事件在加载文档的DOM时触发（可能在</font><font style="vertical-align: inherit;">加载图像等</font></font><em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">之前</font></font></em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">的</font><font style="vertical-align: inherit;">一段时间</font><font style="vertical-align: inherit;">）；</font><font style="vertical-align: inherit;">再次，在Internet Explorer和世界其他地方略有不同</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">和</font></font><code>window.onload</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（即使在旧的浏览器中也实现了），并在加载整个页面（图像，样式等）时触发</font></font></li>
</ul></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
