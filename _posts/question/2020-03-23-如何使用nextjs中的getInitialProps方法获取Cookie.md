---
layout: question
title:  如何使用next.js中的getInitialProps方法获取Cookie？
date:   2020-03-23T03:56:44.000Z
description: 我面临next.js的问题 当我向提出要求时，我无法获得Cookie async static getInitialProps。我得到undefine...
img: 
author: 樱小胖Mandy
category: question
answer: 1
tags: node.js React.js
topic: React.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我面临next.js的问题 </font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">当我向提出要求时，我无法获得Cookie </font></font><code>async static getInitialProps</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">我得到</font></font><code>undefined</code></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">但是，当我将其放入</font></font><code>componentWillMount</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">时没有问题。</font><font style="vertical-align: inherit;">不幸的是，为时已晚，因为我需要在调用组件之前获取cookie信息。</font><font style="vertical-align: inherit;">所以我需要把它拿进去</font></font><code>getInitialProps</code></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在这里，我已经尝试过但没有成功的事情：</font></font></p>

<p></p><div class="snippet" data-lang="js" data-hide="false" data-console="true" data-babel="false">
<div class="snippet-code">
<pre class="snippet-code-js lang-js prettyprint-override"><code>static async getInitialProps () {<font></font>
      const res = await axios.get('http://mybackend/getCookie');<font></font>
      return {data : res.data}<font></font>
    }<font></font>
    <font></font>
    //res.data = undefined</code></pre>
</div>
</div>
<p></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">有什么建议吗？</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第2773篇《如何使用next.js中的getInitialProps方法获取Cookie？》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">理查德理查德</span>
            <span class="discuss-time">2020.03.23</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果使用isomorphic-fetch api，并且路由需要身份验证，则在服务器端渲染（即首页加载）时，这将发送客户端cookie。</font></font></p>

<pre><code>import fetch from "isomorphic-fetch";<font></font>
<font></font>
static async getInitialProps(ctx) {<font></font>
<font></font>
  let clients = await fetch(<font></font>
  `<font></font>
  ${API_SERVER}/client/clients`,<font></font>
    ctx.req ? {<font></font>
      withCredentials: true,<font></font>
      headers: {<font></font>
        cookie: ctx.req.headers.cookie<font></font>
      }<font></font>
    } : {}<font></font>
  );<font></font>
}<font></font>
</code></pre></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
