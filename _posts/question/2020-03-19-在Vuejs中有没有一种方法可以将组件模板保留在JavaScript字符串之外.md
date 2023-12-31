---
layout: question
title:  在Vue.js中，有没有一种方法可以将组件模板保留在JavaScript字符串之外？
date:   2020-03-19T03:50:02.000Z
description: 我刚刚浏览了Vue.js网站上的指南，对组件模板感觉很不好。在字符串中指定它们对我来说似乎很奇怪。当然，这可能适用于非常短的模板，但是一旦您进入多行模板，...
img: 
author: 梅
category: question
answer: 1
tags: JavaScript Vue.js
topic: Vue.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我刚刚浏览了Vue.js网站上的指南，对组件模板感觉很不好。</font><font style="vertical-align: inherit;">在字符串中指定它们对我来说似乎很奇怪。</font><font style="vertical-align: inherit;">当然，这可能适用于非常短的模板，但是一旦您进入多行模板，就需要开始转义新行，而将</font><font style="vertical-align: inherit;">javascript字符串中的html开头</font><font style="vertical-align: inherit;">就感觉</font></font><em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">不对</font></font></em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">更不用说语法高亮或其他任何不错的IDE功能对于JS字符串中的HTML都是没有用的。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">文档中详细介绍了两种选择，它们使用</font></font><a href="http://vuejs.org/v2/guide/components.html#Inline-Templates"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">内联模板</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">或</font></font><a href="http://vuejs.org/v2/guide/components.html#X-Templates"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">X-templates</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，但是不建议使用这两种方法。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">唯一的其他选择似乎是“ </font></font><a href="https://vuejs.org/v2/guide/single-file-components.html"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">单个文件组件”</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，这似乎是一个不错的选择，但是它们位于“ </font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">高级”</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">部分和文档中，据说对于中小型应用程序，只需使用</font></font><code>Vue.component</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">就足够了。</font><font style="vertical-align: inherit;">此外，单个文件组件看起来更难以集成到项目中，因此需要利用项目的构建系统（文档讨论Webpack和Browserify）。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">所以我很困惑。</font><font style="vertical-align: inherit;">我是否只需要接受我的组件代码看起来像直接从文档中拉出来的这个例子一样混乱？</font></font></p>

<pre><code>Vue.component('currency-input', {<font></font>
  template: '\<font></font>
    &lt;span&gt;\<font></font>
      $\<font></font>
      &lt;input\<font></font>
        ref="input"\<font></font>
        v-bind:value="value"\<font></font>
        v-on:input="updateValue($event.target.value)"\<font></font>
      &gt;\<font></font>
    &lt;/span&gt;\<font></font>
  ',<font></font>
......<font></font>
</code></pre></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第2329篇《在Vue.js中，有没有一种方法可以将组件模板保留在JavaScript字符串之外？》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">古一泡芙猴子</span>
            <span class="discuss-time">2020.03.19</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">根据我的经验，如果模板很短，则使用</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">内联</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">模式就可以了。</font><font style="vertical-align: inherit;">如果不是这样，</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">x模板</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">还可以使您摆脱转义的换行符。</font><font style="vertical-align: inherit;">我不明白您为什么不鼓励使用这些方法。</font><font style="vertical-align: inherit;">您能否提供更多信息？</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">但是，如果您坚持要嵌入较长的模板内联，则仍然可以进行此操作而无需转义。</font><font style="vertical-align: inherit;">答案是ES6 </font></font><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">模板文字</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> -包含在其中的字符串</font></font><code>``</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">：</font></font></p>

<pre><code>template: `<font></font>
  &lt;span&gt;<font></font>
    $<font></font>
    &lt;input<font></font>
      ref="input"<font></font>
      v-bind:value="value"<font></font>
      v-on:input="updateValue($event.target.value)"<font></font>
    &gt;<font></font>
  &lt;/span&gt;<font></font>
`,<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">另一方面，我真的认为vue-cli是一个很好的工具。</font><font style="vertical-align: inherit;">Webpack是值得学习的东西。</font></font></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
