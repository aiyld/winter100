---
layout: question
title:  如何使用.css（）应用！important？
date:   2020-03-11T04:04:50.000Z
description: I am having trouble applying a style that is \!important. I’ve tried $("#ele...
img: 
author: 卡卡西十三
category: question
answer: 9
tags: JavaScript
topic: JavaScript
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p>I am having trouble applying a style that is <code>!important</code>. I’ve tried:</p>

<pre class="lang-js prettyprint-override"><code>$("#elem").css("width", "100px !important");
</code></pre>

<p>This does <strong>nothing</strong>; no width style whatsoever is applied. Is there a jQuery-ish way of applying such a style without having to overwrite <code>cssText</code> (which would mean I’d need to parse it first, etc.)?</p>

<p><strong>Edit</strong>: I should add that I have a stylesheet with an <code>!important</code> style that I am trying to override with an <code>!important</code> style inline, so using <code>.width()</code> and the like does not work since it gets overridden by my external <code>!important</code> style.</p>

<p>Also, the value that will override the previous value <strong>is computed</strong>, so I cannot simply create another external style.</p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第639篇《如何使用.css（）应用！important？》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">凯LEY</span>
            <span class="discuss-time">2020.03.11</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">最安全的解决方法是添加一个类，然后在CSS中做魔术：-)，</font></font><code>addClass()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">并</font></font><code>removeClass()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">应完成工作。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">泡芙阿飞斯丁</span>
            <span class="discuss-time">2020.03.11</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我还发现某些元素或附加组件（如Bootstrap）具有一些特殊的类情况，它们不能与</font></font><code>!important</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">或其他变通方法（如）配合使用</font></font><code>.addClass/.removeClass</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，因此您必须将它们打开/关闭。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">例如，如果您使用类似</font></font><code>&lt;table class="table-hover"&gt;</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">的方法来成功修改诸如行颜色之</font></font><code>table-hover</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">类的</font><font style="vertical-align: inherit;">元素的唯一方法是像这样切换</font><font style="vertical-align: inherit;">类的开/关</font></font></p>

<p><code>$(your_element).closest("table").toggleClass("table-hover");</code> </p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">希望这种解决方法对某人有所帮助！</font><font style="vertical-align: inherit;">:)</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">蓝染大人</span>
            <span class="discuss-time">2020.03.11</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">它可能适合您的情况，也可能不适合您，但是您可以在许多这类情况下使用CSS选择器。 </font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">例如，如果您希望.cssText的第3和第6实例具有不同的宽度，则可以编写：</font></font></p>

<pre><code>.cssText:nth-of-type(3), .cssText:nth-of-type(6) {width:100px !important;}
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">要么：</font></font></p>

<pre><code>.container:nth-of-type(3).cssText, .container:nth-of-type(6).cssText {width:100px !important;}
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">西里泡芙</span>
            <span class="discuss-time">2020.03.11</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我会假设您尝试时未添加</font></font><code>!important</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">？</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">内联CSS（这是JavaScript添加样式的方式）将覆盖样式表CSS。</font><font style="vertical-align: inherit;">我很确定，即使样式表CSS规则具有，也是如此</font></font><code>!important</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">另一个问题（也许是一个愚蠢的问题，但必须提出。）：您正在尝试处理的元素</font></font><code>display:block;</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">还是</font></font><code>display:inline-block;</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">？</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">不了解您在CSS方面的专业知识...内联元素并不总是表现出预期的效果。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">null</span>
            <span class="discuss-time">2020.03.11</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">像这样做：</font></font></p>

<pre><code>$("#elem").get(0).style.width= "100px!important";
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">小小Sam小哥</span>
            <span class="discuss-time">2020.03.11</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">仅供参考，它不起作用，因为jQuery不支持它。</font><font style="vertical-align: inherit;">在2012年提交了一张票证（</font></font><a href="https://bugs.jquery.com/ticket/11173" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">＃11173 $（elem）.css（“ property”，“ value！important”）失败</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">），最终由于WONTFIX而关闭。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">TomGil村村</span>
            <span class="discuss-time">2020.03.11</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">代替使用该</font></font><code>css()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">函数，请尝试使用该</font></font><code>addClass()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">函数：</font></font></p>

<pre><code>  &lt;script&gt;<font></font>
  $(document).ready(function() {<font></font>
    $("#example").addClass("exampleClass");<font></font>
  });<font></font>
  &lt;/script&gt;<font></font>
<font></font>
  &lt;style&gt;<font></font>
  .exampleClass{<font></font>
    width:100% !important;<font></font>
    height:100% !important;<font></font>
  }<font></font>
  &lt;/style&gt;<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">米亚Stafan</span>
            <span class="discuss-time">2020.03.11</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您可以通过两种方式实现此目的：</font></font></p>

<pre><code>$("#elem").prop("style", "width: 100px !important"); // this is not supported in chrome<font></font>
$("#elem").attr("style", "width: 100px !important");<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">凯泡芙JinJin</span>
            <span class="discuss-time">2020.03.11</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">你可以这样做：</font></font></p>

<pre><code>$("#elem").css("cssText", "width: 100px !important;");
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">使用“ cssText”作为属性名称，并使用任何要添加到CSS的值作为其名称。</font></font></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
