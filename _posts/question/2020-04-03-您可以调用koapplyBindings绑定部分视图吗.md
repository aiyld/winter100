---
layout: question
title:  您可以调用ko.applyBindings绑定部分视图吗？
date:   2020-04-03T04:06:35.000Z
description: 我正在使用KnockoutJS并具有主视图和视图模型。我想要一个对话框（jQuery UI一个）弹出，而另一个视图绑定到一个单独的子视图模型。对话框内...
img: 
author: 番长樱梅
category: question
answer: 4
tags: 的Ajax HTML
topic: HTML
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我正在使用KnockoutJS并具有主视图和视图模型。</font><font style="vertical-align: inherit;">我想要一个对话框（jQuery UI一个）弹出，而另一个视图绑定到一个单独的子视图模型。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">对话框内容的HTML使用AJAX检索，因此我希望能够</font></font><code>ko.applyBindings</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在请求完成后</font><font style="vertical-align: inherit;">立即调用</font><font style="vertical-align: inherit;">，并且我希望将子视图模型绑定到对话框div中通过Ajax加载的HTML的一部分。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这实际上可行吗，还是在页面最初加载后调用</font></font><code>ko.applyBindings</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">一次</font><font style="vertical-align: inherit;">时需要加载所有视图和视图模型</font><font style="vertical-align: inherit;">？</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第4002篇《您可以调用ko.applyBindings绑定部分视图吗？》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">凯西里</span>
            <span class="discuss-time">2020.04.03</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您应该查看</font></font><code>with</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">绑定以及</font></font><code>controlsDescendantBindings</code> <a href="http://knockoutjs.com/documentation/custom-bindings-controlling-descendant-bindings.html" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">http://knockoutjs.com/documentation/custom-bindings-controlling-descendant-bindings.html</font></font></a></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">凯西里</span>
            <span class="discuss-time">2020.04.03</span>
          </div>
          <div class="discuss-comment"><p><code>ko.applyBindings</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> 接受第二个参数，该参数是要用作根的DOM元素。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这会让您执行以下操作：</font></font></p>

<pre class="lang-html prettyprint-override"><code>&lt;div id="one"&gt;<font></font>
  &lt;input data-bind="value: name" /&gt;<font></font>
&lt;/div&gt;<font></font>
<font></font>
&lt;div id="two"&gt;<font></font>
  &lt;input data-bind="value: name" /&gt;<font></font>
&lt;/div&gt;<font></font>
<font></font>
&lt;script type="text/javascript"&gt;<font></font>
  var viewModelA = {<font></font>
     name: ko.observable("Bob")<font></font>
  };<font></font>
<font></font>
  var viewModelB = {<font></font>
     name: ko.observable("Ted")<font></font>
  };<font></font>
<font></font>
  ko.applyBindings(viewModelA, document.getElementById("one"));<font></font>
  ko.applyBindings(viewModelB, document.getElementById("two"));<font></font>
&lt;/script&gt;<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">因此，可以使用此技术将viewModel绑定到加载到对话框中的动态内容。</font><font style="vertical-align: inherit;">总体而言，您只需要注意不要</font></font><code>applyBindings</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在同一元素上多次</font><font style="vertical-align: inherit;">调用</font><font style="vertical-align: inherit;">，因为您将获得多个事件处理程序。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">阿飞</span>
            <span class="discuss-time">2020.04.03</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我设法在运行时将自定义模型绑定到元素。</font><font style="vertical-align: inherit;">代码在这里：</font><a href="http://jsfiddle.net/ZiglioNZ/tzD4T/457/" rel="noreferrer"><font style="vertical-align: inherit;">http</font></a><font style="vertical-align: inherit;"> : </font></font><a href="http://jsfiddle.net/ZiglioNZ/tzD4T/457/" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">//jsfiddle.net/ZiglioNZ/tzD4T/457/</font></font></a></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">有趣的一点是，我将data-bind属性应用于未定义的元素：</font></font></p>

<pre><code>    var handle = slider.slider().find(".ui-slider-handle").first();<font></font>
    $(handle).attr("data-bind", "tooltip: viewModel.value");<font></font>
    ko.applyBindings(viewModel.value, $(handle)[0]);<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">猪猪猿小哥</span>
            <span class="discuss-time">2020.04.03</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">尽管Niemeyer的答案是对该问题的更正确答案，但您</font></font><em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">也</font></font></em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">可以执行以下操作：</font></font></p>



<pre class="lang-html prettyprint-override"><code>&lt;div&gt;<font></font>
  &lt;input data-bind="value: VMA.name" /&gt;<font></font>
&lt;/div&gt;<font></font>
<font></font>
&lt;div&gt;<font></font>
  &lt;input data-bind="value: VMB.name" /&gt;<font></font>
&lt;/div&gt;<font></font>
<font></font>
&lt;script type="text/javascript"&gt;<font></font>
  var viewModels = {<font></font>
     VMA: {name: ko.observable("Bob")},<font></font>
     VMB: {name: ko.observable("Ted")}<font></font>
  };<font></font>
<font></font>
  ko.applyBindings(viewModels);<font></font>
&lt;/script&gt;<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这意味着您不必指定DOM元素，甚至可以将多个模型绑定到同一元素，如下所示：</font></font></p>

<pre class="lang-html prettyprint-override"><code>&lt;div&gt;<font></font>
  &lt;input data-bind="value: VMA.name() + ' and ' + VMB.name()" /&gt;<font></font>
&lt;/div&gt;<font></font>
</code></pre></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
