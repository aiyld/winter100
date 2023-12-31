---
layout: question
title:  Next.js将NODE_ENV传递给客户端
date:   2020-03-20T05:06:49.000Z
description: 我正在使用Next.js构建一个React SSR应用程序。我希望能够在客户端访问NODE_ENV，因为这将告诉我的应用程序要使用哪些API端点。...
img: 
author: 路易番长
category: question
answer: 1
tags: JavaScript React.js
topic: React.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我正在使用Next.js构建一个React SSR应用程序。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我希望能够在客户端访问NODE_ENV，因为这将告诉我的应用程序要使用哪些API端点。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我正在努力为此找到一个体面的方法。</font><font style="vertical-align: inherit;">我想在第一次在服务器上呈现页面时将NODE_ENV定义为窗口变量，然后在进行API调用的辅助函数中检查是否在服务器或客户端上调用了代码，并根据需要使用window或process.env变量。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">有没有人对这样的问题有好的解决方案。</font><font style="vertical-align: inherit;">这肯定是一个普遍的问题，但是我找不到任何好的解决方案。</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第2458篇《Next.js将NODE_ENV传递给客户端》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Eva神无</span>
            <span class="discuss-time">2020.03.20</span>
          </div>
          <div class="discuss-comment"><h1><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">使用Next的构建时配置</font></font></h1>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">@DarrylR已经提到了使用</font></font><code>next.config.js</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">和Next的</font></font><a href="https://github.com/zeit/next.js#runtime-configuration" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">运行时配置</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，但是您也可以使用Next的</font></font><a href="https://github.com/zeit/next.js#build-time-configuration" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">构建时配置</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这样，您就可以</font></font><code>process.env.XXXX</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在代码中添加权限（如下面的步骤3所示），而不必导入任何内容。</font><font style="vertical-align: inherit;">但是，如果在使用</font></font><a href="https://nextjs.org" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Next.js</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在</font><font style="vertical-align: inherit;">本地</font><a href="https://nextjs.org" rel="noreferrer"><font style="vertical-align: inherit;">构建</font></a><font style="vertical-align: inherit;">和部署到</font></font><a href="https://zeit.co/now" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">ZEIT Now</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">时</font><font style="vertical-align: inherit;">都应该设置env变量</font><font style="vertical-align: inherit;">，则我不知道是否可以使用此方法将它们保存在一个文件中（请参阅下面的步骤2）。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">运行时配置文档建议您通常要使用构建时配置：</font></font></p>

<blockquote>
  <p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">警告：</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">通常，您想使用构建时配置来提供您的配置。</font><font style="vertical-align: inherit;">这是因为运行时配置增加了渲染/初始化开销，并且</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">与</font></font><a href="https://github.com/zeit/next.js#automatic-prerendering" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">自动预渲染</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">不兼容</font><font style="vertical-align: inherit;">。</font></font></strong></p>
</blockquote>

<hr>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">脚步：</font></font></p>

<h2><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">1.设置</font></font><code>NODE_ENV</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">构建过程</font></font></h2>

<h3><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">1.1 </font><a href="https://zeit.co/now" rel="noreferrer"><font style="vertical-align: inherit;">立即</font></a><font style="vertical-align: inherit;">使用</font></font><a href="https://zeit.co/now" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">ZEIT</font></font></a></h3>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果部署使用现在ZEIT，您可以设置</font></font><a href="https://zeit.co/docs/v2/advanced/configuration#build.env" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在构建时使用的ENV变量</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">中</font></font><code>now.json</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">：</font></font></p>

<pre class="lang-json prettyprint-override"><code>{<font></font>
  "version": 2,<font></font>
  "build": {<font></font>
    "env": {<font></font>
      "NODE_ENV": "production"<font></font>
    }<font></font>
  }<font></font>
}<font></font>
</code></pre>

<h3><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">1.2在本地运行时（可选）</font></font></h3>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果还希望</font></font><code>NODE_ENV</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在本地运行时进行设置，则不会通过进行设置</font></font><code>now.json</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">但是，您可以通过其他方式进行设置，例如：</font></font></p>

<pre><code>$ NODE_ENV=production npm run build
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">或将构建脚本更改</font></font><code>package.json</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">为</font></font></p>

<pre><code>"build": "NODE_ENV=production next build"
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果需要，您当然也可以设置</font></font><code>NODE_ENV</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">其他脚本而不是build。</font></font></p>

<h2>2. Make Next inline value of <code>process.env.NODE_ENV</code></h2>

<p>Add this to the <code>next.config.js</code> as described <a href="https://github.com/zeit/next.js#runtime-configuration" rel="noreferrer">here</a>:</p>

<pre class="lang-js prettyprint-override"><code>module.exports = {<font></font>
  env: {<font></font>
    NODE_ENV: process.env.NODE_ENV<font></font>
  }<font></font>
};<font></font>
</code></pre>

<h2>3. Use in code</h2>

<pre class="lang-js prettyprint-override"><code>if (process.env.NODE_ENV === "production") {<font></font>
  console.log("In production")<font></font>
} else {<font></font>
  console.log("Not in production")<font></font>
}<font></font>
</code></pre></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
