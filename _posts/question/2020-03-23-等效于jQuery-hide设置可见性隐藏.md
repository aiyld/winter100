---
layout: question
title:  等效于jQuery .hide（）设置可见性：隐藏
date:   2020-03-23T02:04:52.000Z
description: 在jQuery中，有.hide()和.show()方法设置CSS display  none设置。是否有可以设置visibility  hidden设...
img: 
author: Eva飞云
category: question
answer: 2
tags: JavaScript CSS
topic: CSS
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在jQuery中，有</font></font><code>.hide()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">和</font></font><code>.show()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">方法设置CSS </font></font><code>display: none</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">设置。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">是否有可以设置</font></font><code>visibility: hidden</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">设置</font><font style="vertical-align: inherit;">的等效功能</font><font style="vertical-align: inherit;">？</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我知道我可以使用，</font></font><code>.css()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">但是我喜欢某些类似的功能</font></font><code>.hide()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">谢谢。</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第2633篇《等效于jQuery .hide（）设置可见性：隐藏》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">蛋蛋猿</span>
            <span class="discuss-time">2020.03.23</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">没有内置的，但是您可以很容易地编写自己的：</font></font></p>

<pre><code>(function($) {<font></font>
    $.fn.invisible = function() {<font></font>
        return this.each(function() {<font></font>
            $(this).css("visibility", "hidden");<font></font>
        });<font></font>
    };<font></font>
    $.fn.visible = function() {<font></font>
        return this.each(function() {<font></font>
            $(this).css("visibility", "visible");<font></font>
        });<font></font>
    };<font></font>
}(jQuery));<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">然后可以这样调用：</font></font></p>

<pre><code>$("#someElem").invisible();<font></font>
$("#someOther").visible();<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这是一个</font></font><a href="http://jsfiddle.net/nGhjQ/" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">有效的例子</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">梅泡芙</span>
            <span class="discuss-time">2020.03.23</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">一个更简单的方法是使用jQuery的</font></font><a href="http://jqueryui.com/toggleClass/" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">toggleClass（）</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">方法</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">的CSS</font></font></p>

<pre><code>.newClass{visibility: hidden}
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">的HTML</font></font></p>

<pre><code>&lt;a href="#" class=trigger&gt;Trigger Element &lt;/a&gt;<font></font>
&lt;div class="hidden_element"&gt;Some Content&lt;/div&gt;<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">JS</font></font></p>

<pre><code>$(document).ready(function(){<font></font>
    $(".trigger").click(function(){<font></font>
        $(".hidden_element").toggleClass("newClass");<font></font>
    });<font></font>
});<font></font>
</code></pre></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
