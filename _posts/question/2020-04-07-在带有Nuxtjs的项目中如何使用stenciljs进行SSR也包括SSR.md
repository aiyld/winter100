---
layout: question
title:  在带有Nuxt.js的项目中如何使用stencil.js进行SSR（也包括SSR）
date:   2020-04-07T03:52:14.000Z
description: 我想stencil在我的nuxt项目中使用一个库。我能够使其工作，但是当vue组件在服务器端呈现时，我只能使stencil的组件在客户端呈现。我认...
img: 
author: 卡卡西
category: question
answer: 2
tags: JavaScript Vue.js
topic: Vue.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我想</font></font><code>stencil</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在我的</font></font><code>nuxt</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">项目中</font><font style="vertical-align: inherit;">使用一个</font><font style="vertical-align: inherit;">库</font><font style="vertical-align: inherit;">。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我能够使其工作，但是当</font></font><code>vue</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">组件在服务器端呈现时，我只能使</font></font><code>stencil</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">的组件在客户端呈现。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我认为最大的问题是</font></font><code>defineCustomElement</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">需要将其</font></font><code>window</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">作为参数。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我知道</font></font><code>stencil.js</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在我的理解中，它具有基本上是SSR的“ prerender”，我想将其与</font></font><code>Nuxt.js</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">SSR </font><font style="vertical-align: inherit;">一起使用</font><font style="vertical-align: inherit;">。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">所以我的问题是：如何配置</font></font><code>nuxt</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">项目以支持服务器端渲染</font></font><code>stencil.js</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">？</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第4129篇《在带有Nuxt.js的项目中如何使用stencil.js进行SSR（也包括SSR）》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Stafan</span>
            <span class="discuss-time">2020.04.07</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">确实，您有一种解决方法 </font></font></p>

<ol>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您必须以unpkg或任何其他公共（或私有）CDN发布Web组件 </font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在您的nuxt.config.js文件中，在部分脚本中添加脚本。</font><font style="vertical-align: inherit;">该脚本必须引用您的公共库（</font></font><a href="https://stenciljs.com/docs/javascript" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">https://stenciljs.com/docs/javascript</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">）</font></font></li>
</ol>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">有关如何向您的nuxt项目添加外部资源的更多信息，请阅读：</font></font><a href="https://nuxtjs.org/faq/" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">https</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> ://nuxtjs.org/faq/- </font><font style="vertical-align: inherit;">&gt;如何使用外部资源</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">干杯</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">飞云</span>
            <span class="discuss-time">2020.04.07</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">哦，是的，正如Aldarund所说，您不能，我更好地查看了</font></font><a href="https://stenciljs.com/docs/prerendering" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">prerendering页面</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，据说那里的prerender发生在构建时间上，所以这是不可能的：/太糟糕了</font></font></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
