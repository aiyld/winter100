---
layout: question
title:  登录nuxt.js后重定向到先前的URL
date:   2020-03-26T08:11:04.000Z
description: 我基本上想在用户成功登录后重定向到先前的URL。我使用先前的网址（例如）重定向到登录页面/login?redirect=/page1/page2。...
img: 
author: DavaidTony宝儿
category: question
answer: 1
tags: vue.js Vue.js
topic: Vue.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我基本上想在用户成功登录后重定向到先前的URL。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我使用先前的网址（例如）重定向到登录页面</font></font><code>/login?redirect=/page1/page2</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">而且我想在用户身份验证时将其重定向回该URL。</font><font style="vertical-align: inherit;">我在</font></font><code>auth-module</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这里</font><font style="vertical-align: inherit;">使用</font><font style="vertical-align: inherit;">：</font><a href="https://auth.nuxtjs.org/" rel="nofollow noreferrer"><font style="vertical-align: inherit;">https</font></a><font style="vertical-align: inherit;"> : </font></font><a href="https://auth.nuxtjs.org/" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">//auth.nuxtjs.org/</font></font></a></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我如何登录用户。</font></font></p>

<pre><code>methods: {<font></font>
    async submit() {<font></font>
      await this.$auth.loginWith('local', {<font></font>
        data: this.form<font></font>
      })<font></font>
    }<font></font>
}<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我在文档中可以找到的唯一东西是：</font><a href="https://auth.nuxtjs.org/getting-started/options#redirect" rel="nofollow noreferrer"><font style="vertical-align: inherit;">https</font></a><font style="vertical-align: inherit;"> : </font></font><a href="https://auth.nuxtjs.org/getting-started/options#redirect" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">//auth.nuxtjs.org/getting-started/options#redirect</font></font></a></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">但是，它仅重定向到特定页面而不是查询中的上一页。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">关于如何实现这一目标的任何想法？</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第3754篇《登录nuxt.js后重定向到先前的URL》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">西里神奇</span>
            <span class="discuss-time">2020.03.26</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">你可以这样做</font></font></p>

<pre><code>  this.$router.back()
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">然后返回到最后一条路线。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">程序导航| </font><font style="vertical-align: inherit;">Vue路由器
 </font></font><a href="https://router.vuejs.org/guide/essentials/navigation.html" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">https://router.vuejs.org/guide/essentials/navigation.html</font></font></a></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">谢谢。</font></font></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
