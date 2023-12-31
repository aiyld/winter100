---
layout: question
title:  如何在Next.js中使用webrtc-adapter npm软件包
date:   2020-03-27T12:16:58.000Z
description: 我正在用Next.js创建一个React。我的ES6导入对于我创建的.js文件工作正常，但是导入webrtc-adapter时在下一个失败，但在react...
img: 
author: 宝儿
category: question
answer: 0
tags: reactjs React.js
topic: React.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我正在用Next.js创建一个React。</font><font style="vertical-align: inherit;">我的ES6导入对于我创建的.js文件工作正常，但是导入</font></font><code>webrtc-adapter</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">时在下一个失败，但在react-app中成功：</font></font></p>

<pre><code>import {adapterFactory} from './adapter_factory.js';<font></font>
       ^<font></font>
SyntaxError: Unexpected token {<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">例如，以下是两个复制的链接：</font></font></p>

<ul>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">失败（下一个）：</font><a href="https://repl.it/repls/SafeWorseEngine" rel="nofollow noreferrer"><font style="vertical-align: inherit;">https</font></a><font style="vertical-align: inherit;"> ://repl.it/repls/SafeWorseEngine</font></font><a href="https://repl.it/repls/SafeWorseEngine" rel="nofollow noreferrer"><font style="vertical-align: inherit;"></font></a></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">作品（CRA）：</font><a href="https://stackblitz.com/edit/react-cjxz7s?file=index.js" rel="nofollow noreferrer"><font style="vertical-align: inherit;">https</font></a><font style="vertical-align: inherit;"> : </font><a href="https://stackblitz.com/edit/react-cjxz7s?file=index.js" rel="nofollow noreferrer"><font style="vertical-align: inherit;">//stackblitz.com/edit/react-cjxz7s?</font></a><font style="vertical-align: inherit;"> file </font></font><a href="https://stackblitz.com/edit/react-cjxz7s?file=index.js" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">=index.js</font></font></a> </li>
</ul>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">以下是简化的测试用例。</font><font style="vertical-align: inherit;">只需导入</font></font><code>webrtc-adapter</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">并进行控制台即可。</font><font style="vertical-align: inherit;">在CRA中可用，但在Next中不可用。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">将ES6导入我自己的文件中效果很好，但不能使用外部软件包。</font><font style="vertical-align: inherit;">有任何想法吗？</font></font></p>

<pre><code>{<font></font>
  "name": "webrtc-test",<font></font>
  "version": "0.1.0",<font></font>
  "private": true,<font></font>
  "dependencies": {<font></font>
    "next": "^7.0.2",<font></font>
    "react": "^16.8.0-alpha.0",<font></font>
    "react-dom": "^16.8.0-alpha.0",<font></font>
    "webrtc-adapter": "^7.1.1"<font></font>
  },<font></font>
  "scripts": {<font></font>
    "dev": "next",<font></font>
    "build": "next build",<font></font>
    "start": "next start"<font></font>
  }<font></font>
}<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在pages / index.js中</font></font></p>

<pre><code>import adapter from 'webrtc-adapter';<font></font>
console.log(adapter);<font></font>
export default () =&gt; &lt;div&gt;Welcome to next!&lt;/div&gt;;<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我什至尝试：</font></font></p>

<pre><code>import 'webrtc-adapter';
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">任何帮助，将不胜感激！</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第3812篇《如何在Next.js中使用webrtc-adapter npm软件包》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    
    </div>
    {% endraw %}
  </div>
<div>
