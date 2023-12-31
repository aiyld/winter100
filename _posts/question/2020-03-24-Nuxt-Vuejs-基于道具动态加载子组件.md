---
layout: question
title:  Nuxt / Vue.js-基于道具动态加载子组件
date:   2020-03-24T08:01:07.000Z
description: 我有一个sectionHeader.vue要在许多不同页面上使用的组件。在里面sectionHeader.vue是一个<canvas>元素（我正在使用一些...
img: 
author: 卡卡西Near
category: question
answer: 0
tags: JavaScript Vue.js
topic: Vue.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我有一个</font></font><code>sectionHeader.vue</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">要在许多不同页面上使用</font><font style="vertical-align: inherit;">的</font><font style="vertical-align: inherit;">组件。</font><font style="vertical-align: inherit;">在里面</font></font><code>sectionHeader.vue</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">是一个</font></font><code>&lt;canvas&gt;</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">元素（我正在使用一些健壮的three.js动画），我希望通过props动态地在每个标头内部进行更改。</font><font style="vertical-align: inherit;">我想使这项工作能够充分利用Vue固有的代码拆分功能，以便每个页面都不会加载其他所有页面的动画js代码，而只会加载与其相关的代码。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我正在尝试使用</font></font><a href="https://vuejs.org/v2/guide/components.html#Dynamic-Components" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">动态组件</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">来动态加载此内容，</font><font style="vertical-align: inherit;">但我认为这不是我想要的...</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我的文件夹结构：</font></font></p>

<pre><code>components<font></font>
  animations<font></font>
    robust-animation-1.vue<font></font>
    robust-animation-2.vue<font></font>
    maybe-like-15-more-of-these.vue<font></font>
  headings<font></font>
    heading2.vue<font></font>
  SectionHeader.vue<font></font>
pages<font></font>
  index.vue<font></font>
<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">pages / index.vue：</font></font></p>

<pre class="lang-js prettyprint-override"><code>&lt;sectionHeader post-title="Menu" class-name="menu" canvas="./animations/robust-animation-1"&gt;&lt;/sectionHeader&gt;
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">组件/SectionHeader.vue：</font></font></p>

<pre class="lang-js prettyprint-override"><code>&lt;template&gt;<font></font>
    &lt;section class="intro section-intro" :class="className"&gt;<font></font>
        &lt;heading2 :post-title="postTitle"&gt;&lt;/heading2&gt;<font></font>
        &lt;component v-bind:is="canvas"&gt;&lt;/component&gt; &lt;!-- this is what i am dynamically trying to load --&gt; <font></font>
        {{canvas}} &lt;!-- this echos out ./animations/robust-animation-1 --&gt;<font></font>
    &lt;/section&gt;<font></font>
&lt;/template&gt;<font></font>
<font></font>
&lt;script&gt;<font></font>
import heading2 from './headings/heading2';<font></font>
<font></font>
export default {<font></font>
    components: {<font></font>
        heading2<font></font>
    },<font></font>
    props: [<font></font>
        'postTitle', 'className', 'canvas'<font></font>
    ]<font></font>
}<font></font>
&lt;/script&gt;<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">组件/动画/健壮动画-1.vue：</font></font></p>

<pre class="lang-js prettyprint-override"><code>&lt;template&gt;<font></font>
    &lt;div&gt;<font></font>
        &lt;canvas class="prowork-canvas" width="960" height="960"&gt;&lt;/canvas&gt;<font></font>
    &lt;/div&gt;<font></font>
&lt;/template&gt;<font></font>
<font></font>
&lt;script&gt;<font></font>
// 200 lines of js here that manipulates the above canvas<font></font>
&lt;/script&gt;<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我的</font></font><code>heading2</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">组件效果很好，但是无论如何尝试，我都无法弄清楚如何动态引入动画组件。</font><font style="vertical-align: inherit;">我得到不同程度的以下错误：</font></font></p>

<pre><code>client.js 76 DOMException: Failed to execute 'createElement' on 'Document': The tag name provided ('./animations/robust-animation-1') is not a valid name.
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我查看了作用域内的插槽，它看上去与我需要的位置很接近，但不完全相同。</font><font style="vertical-align: inherit;">有没有更好的方法来做我正在尝试的事情？</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第3492篇《Nuxt / Vue.js-基于道具动态加载子组件》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    
    </div>
    {% endraw %}
  </div>
<div>
