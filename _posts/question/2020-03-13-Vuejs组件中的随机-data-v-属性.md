---
layout: question
title:  Vue.js组件中的随机“ data-v- \*”属性
date:   2020-03-12T16:35:22.000Z
description: 使用Vue.js进行实验时，我注意到的第一件事是，我定义为单个文件组件并包含为自定义元素的组件的每个实例如何获得一个随机哈希属性，例如data-v-58f...
img: 
author: EvaGil
category: question
answer: 1
tags: vue.js Vue.js
topic: Vue.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">使用</font></font><a href="https://vuejs.org/" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Vue.js</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">进行</font><font style="vertical-align: inherit;">实验时，</font><font style="vertical-align: inherit;">我注意到的第一件事是，我定义为</font></font><a href="https://vuejs.org/v2/guide/single-file-components.html" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">单个文件组件</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">并包含为自定义元素</font><font style="vertical-align: inherit;">的组件的每个实例如何</font><font style="vertical-align: inherit;">获得一个随机哈希属性，例如</font></font><code>data-v-58fd7087=""</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">特别：</font></font></p>

<ul>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">给定组件的每个实例的每个DOM元素都会获得相同的哈希值</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">哈希独立于路由器生成</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">两次调用之间的哈希值是稳定的</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">哈希在组件名称更改之间是稳定的</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">散列未在磁盘上存储/生成</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">因此哈希是动态生成的</font></font></li>
</ul>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">它可以由</font><font style="vertical-align: inherit;">我的Vue设置中</font><font style="vertical-align: inherit;">的</font></font><a href="https://karma-runner.github.io/1.0/index.html" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Karma</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">或</font></font><a href="https://webpack.js.org" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Webpack</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">生成</font><font style="vertical-align: inherit;">吗？</font><font style="vertical-align: inherit;">如果不是，这些对我来说是一些令人惊讶的发现。</font><font style="vertical-align: inherit;">它导致两个问题：</font></font></p>

<ul>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">此哈希值（属性）何时以及如何生成？</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">为什么会生成哈希（属性）？</font></font></li>
</ul></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第1363篇《Vue.js组件中的随机“ data-v- \*”属性》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">番长前端</span>
            <span class="discuss-time">2020.03.13</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">将带</font></font><a href="https://vue-loader.vuejs.org/en/features/scoped-css.html" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">范围的CSS</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">与Vue Loader一起</font><font style="vertical-align: inherit;">使用时，会发生类似的情况</font><font style="vertical-align: inherit;">。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我使用范围化的CSS，并且具有诸如之类的属性</font></font><code>data-v-4646bc3c</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，因此我认为是这样。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果您不希望使用此功能，请尝试</font></font><code>scoped</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">从单个文件组件中</font><font style="vertical-align: inherit;">删除该</font><font style="vertical-align: inherit;">属性。</font></font></p>

<pre><code>&lt;style scoped&gt;<font></font>
/* local styles */<font></font>
&lt;/style&gt;<font></font>
</code></pre></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
