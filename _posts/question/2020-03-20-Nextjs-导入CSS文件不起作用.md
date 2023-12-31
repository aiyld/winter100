---
layout: question
title:  Next.js-导入CSS文件不起作用
date:   2020-03-20T06:15:33.000Z
description: 我正在创建一个带有react，redux和next.js的项目，并想在js中导入CSS文件。我按照next.js /＃css和next-css中的说明...
img: 
author: 猪猪
category: question
answer: 0
tags: JavaScript React.js
topic: React.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我正在创建一个带有react，redux和next.js的项目，并想在js中导入CSS文件。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我按照</font></font><a href="https://github.com/zeit/next.js/#css" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">next.js /＃css</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">和</font></font><a href="https://github.com/zeit/next-plugins/tree/master/packages/next-css" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">next-css中的说明进行操作</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，但是发现CSS样式无效。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我的代码如下：</font></font></p>

<blockquote>
  <p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">pages / index.js：</font></font></p>
</blockquote>

<pre><code>import React from 'react'<font></font>
import "../style.css"<font></font>
<font></font>
class Index extends React.Component {<font></font>
    render() {<font></font>
        return (<font></font>
            &lt;div className="example"&gt;Hello World!&lt;/div&gt;<font></font>
        );<font></font>
    }<font></font>
}<font></font>
<font></font>
export default Index<font></font>
</code></pre>

<blockquote>
  <p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">next.config.js：</font></font></p>
</blockquote>

<pre><code>const withCSS = require('@zeit/next-css')<font></font>
module.exports = withCSS()<font></font>
</code></pre>

<blockquote>
  <p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">style.css：</font></font></p>
</blockquote>

<pre><code>.example {<font></font>
    font-size: 50px;<font></font>
    color: blue;<font></font>
}<font></font>
</code></pre>

<blockquote>
  <p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">package.json：</font></font></p>
</blockquote>

<pre><code>{<font></font>
    "name": "my-app",<font></font>
    "version": "0.1.0",<font></font>
    "private": true,<font></font>
    "dependencies": {<font></font>
        "@zeit/next-css": "^0.1.5",<font></font>
        "next": "^6.0.0",<font></font>
        "react": "^16.3.2",<font></font>
        "react-dom": "^16.3.2",<font></font>
        "react-redux": "^5.0.7",<font></font>
        "react-scripts": "1.1.4",<font></font>
        "redux": "^4.0.0",<font></font>
        "redux-devtools": "^3.4.1"<font></font>
    },<font></font>
    "scripts": {<font></font>
        "test": "react-scripts test --env=jsdom",<font></font>
        "eject": "react-scripts eject",<font></font>
        "dev": "next",<font></font>
        "build": "next build",<font></font>
        "start": "next start"<font></font>
    }<font></font>
}<font></font>
</code></pre>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">问题</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">：</font></font></p>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">1.</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> Chrome中存在“未捕获的SyntaxError”错误，但似乎并不影响页面的呈现。</font><font style="vertical-align: inherit;">但是我仍然想知道原因和解决方案。</font><font style="vertical-align: inherit;">chrome中的index.js错误低于img</font></font></p>

<p><img src="https://www.samyoc.com//uploads/users/24058/images/thumbnails/1584684805911.png" data-src="https://www.samyoc.com//uploads/users/24058/images/1584684805911.png" alt=""></p>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">2.</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如Chrome中所示，没有“ example”类，这意味着未加载style.css文件。</font><font style="vertical-align: inherit;">我有什么想念的吗？</font><font style="vertical-align: inherit;">chrome中没有CSS文件</font></font></p>

<p><img src="https://www.samyoc.com//uploads/users/24058/images/thumbnails/1584684805913.png" data-src="https://www.samyoc.com//uploads/users/24058/images/1584684805913.png" alt=""></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">提前致谢。</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第2531篇《Next.js-导入CSS文件不起作用》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    
    </div>
    {% endraw %}
  </div>
<div>
