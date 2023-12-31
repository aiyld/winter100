---
layout: question
title:  是否可以将Vue.js模板编译为静态HTML和CSS文件？
date:   2020-03-19T03:49:39.000Z
description: 最近，我爱上了Vue.js的单个文件组件。组件的模板和样式彼此接近会更好，而且我发现我现在编写的bug更少了，因为很容易将页面的一部分组成并在多个位置使用...
img: 
author: L西里
category: question
answer: 3
tags: webpack Vue.js
topic: Vue.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">最近，我爱上了Vue.js的</font></font><a href="https://vuejs.org/v2/guide/single-file-components.html" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">单个文件组件</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">组件的模板和样式彼此接近会更好，而且我发现我现在编写的bug更少了，因为很容易将页面的一部分组成并在多个位置使用它。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我想知道是否可以将这种单文件组件结构扩展到生成静态HTML页面，而不涉及Vue。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">例如，假设我要创建一个页面，该页面具有一个主要的“内容” div，其中包含一个页眉，一个节和一个页脚。</font><font style="vertical-align: inherit;">使用Vue.js，我可以创建“页眉”，“部分”和“页脚”组件，并使用JavaScript在页面加载后实例化它们。</font><font style="vertical-align: inherit;">因为页面的每个部分都在其自己的组件中，所以一个组件中的CSS不会影响另一个组件，并且我有一个更加整洁的文件树可编辑。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">但是，这似乎有点浪费，因为这些组件实际上不是交互式的：我没有使用</font></font><code>v-model</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">or </font></font><code>v-bind</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">或or </font></font><code>v-on</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，我只是使用Vue.js，因为它使我可以分离出页面的一部分。</font><font style="vertical-align: inherit;">这也意味着如果禁用JavaScript，我的页面将根本无法工作，因为每个元素（保存主要内容div）都取决于Vue是否可用。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">那么，有什么方法可以编译.vue文件，而不是编译到使用Vue.js在运行时加载这些组件的页面，而是将没有JavaScript呈现的HTML和CSS文件分开？</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">理想情况下，我有一个组件“ greeting.vue”：</font></font></p>

<pre><code>&lt;template&gt;<font></font>
    &lt;p class="greeting"&gt;Hello!&lt;/p&gt;<font></font>
&lt;/template&gt;<font></font>
&lt;style scoped&gt;<font></font>
    .greeting { color: red; }<font></font>
&lt;/style&gt;<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在页面内使用：</font></font></p>

<pre><code>&lt;html&gt;<font></font>
    &lt;body&gt;<font></font>
        &lt;greeting&gt;&lt;/greeting&gt;<font></font>
    &lt;/body&gt;<font></font>
&lt;/html&gt;<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这些文件将被编译成两个文件：一个带有已编译和预渲染模板的HTML页面，以及一个包含所有组件样式的CSS文件。</font><font style="vertical-align: inherit;">然后，我可以在页面中包含生成的样式表，然后对所有组件进行样式化。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我看过</font></font><a href="https://github.com/vuejs/vue-loader" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">vue-loader</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">和</font></font><a href="https://github.com/vuejs/vueify" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">vueify</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，但是由于我没有足够使用Webpack或Browserify，所以我不明白它们在做什么。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我想做的事可能吗？</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第2328篇《是否可以将Vue.js模板编译为静态HTML和CSS文件？》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">null</span>
            <span class="discuss-time">2020.03.19</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我会说您不能这样做，因为</font></font><code>Vue</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">使用虚拟DOM，它不会将模板编译</font></font><code>HTML</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">为JavaScript </font></font><code>render functions</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，</font><font style="vertical-align: inherit;">而是将</font><font style="vertical-align: inherit;">模板编译</font><font style="vertical-align: inherit;">为JavaScript </font><font style="vertical-align: inherit;">，这是在更新数据时有效修补DOM所必需的。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我确信可以用一些</font></font><code>node</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">魔术来解析和输出文件</font><font style="vertical-align: inherit;">来完成您想做的事情</font><font style="vertical-align: inherit;">，但这对于只产生最小影响的事情来说将是一笔很大的工作。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">小宇宙猪猪</span>
            <span class="discuss-time">2020.03.19</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您正在寻找的是服务器端渲染。</font><font style="vertical-align: inherit;">我建议您看看Nuxt.js。</font></font></p>

<p><a href="https://vuejs.org/v2/guide/ssr.html#Nuxt-js" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">从VueJS文档：</font></font></a></p>

<blockquote>
  <p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">正确配置生产就绪的服务器呈现的应用程序的所有讨论方面可能是一项艰巨的任务。</font><font style="vertical-align: inherit;">幸运的是，有一个出色的社区项目旨在使所有这些变得更容易：Nuxt.js。</font><font style="vertical-align: inherit;">Nuxt.js是基于Vue生态系统构建的高级框架，该框架为编写通用Vue应用程序提供了极其简化的开发体验。</font><font style="vertical-align: inherit;">更好的是，您甚至可以将其用作静态站点生成器（页面被编写为单文件Vue组件）！</font><font style="vertical-align: inherit;">我们强烈建议您尝试一下。</font></font></p>
</blockquote>

<p><font style="vertical-align: inherit;"></font><a href="https://nuxtjs.org/guide/installation" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">入门</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">非常简单</font><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">如果您使用</font></font><code>vue-cli</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">：</font></font></p>

<pre><code>$ vue init nuxt/starter &lt;project-name&gt;
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">它带有您通常需要的所有资源（Vuex，路由器等）。</font><font style="vertical-align: inherit;">请记住，它强制执行某些文件夹结构，您必须遵循。</font></font></p>

<p><a href="https://nuxtjs.org/guide/commands" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">是启动器中包含的命令列表。</font></font></p>

<pre><code>"scripts": {<font></font>
  "dev": "nuxt",<font></font>
  "build": "nuxt build",<font></font>
  "start": "nuxt start",<font></font>
  "generate": "nuxt generate"<font></font>
}<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">你可能会被大部分iterested的</font></font><code>generate</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，因为它</font></font></p>

<blockquote>
  <p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">构建应用程序，并将每个路由生成为HTML文件（用于静态托管）。</font></font></p>
</blockquote>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">还需要注意的很酷的事情是，该项目似乎（在撰写本文时）</font></font><a href="https://github.com/nuxt/nuxt.js" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">正在积极开发中</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，我们可以期待更多出色的功能！</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">斯丁Gil</span>
            <span class="discuss-time">2020.03.19</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">从官方的vuejs指南：</font></font></p>

<blockquote>
  <p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果您使用的是Webpack，则可以使用</font></font><a href="https://github.com/chrisvfritz/prerender-spa-plugin" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">prerender-spa-plugin</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">轻松添加预</font><a href="https://github.com/chrisvfritz/prerender-spa-plugin" rel="noreferrer"><font style="vertical-align: inherit;">渲染</font></a><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">它已经通过Vue应用程序进行了广泛的测试-实际上，创建者是Vue核心团队的成员。</font></font></p>
</blockquote></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
