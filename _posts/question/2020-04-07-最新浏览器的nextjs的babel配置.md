---
layout: question
title:  最新浏览器的next.js的babel配置
date:   2020-04-07T03:48:21.000Z
description: Next.js的默认配置与IE11兼容。现在，我们只为最新的浏览器（Edge，Safari，Chrome和Firefox的最新版本）编写Web应用程序。因...
img: 
author: 梅
category: question
answer: 1
tags: node.js React.js
topic: React.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Next.js的默认配置与IE11兼容。</font><font style="vertical-align: inherit;">现在，我们只为最新的浏览器（Edge，Safari，Chrome和Firefox的最新版本）编写Web应用程序。</font><font style="vertical-align: inherit;">因此，我们希望babel尽可能少做一些事情。</font><font style="vertical-align: inherit;">那我怎么写“ .babelrc”呢？</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第4115篇《最新浏览器的next.js的babel配置》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">米亚</span>
            <span class="discuss-time">2020.04.07</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我认为不应该排除IE11的支持，因为唯一的polyfill是一个全局的Promise对象，它使nextJS在IE11上工作。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">但是，您可以将自定义项添加</font></font><code>.babelrc</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">到项目中。</font><font style="vertical-align: inherit;">请参阅此处的文档：</font><a href="https://nextjs.org/docs/#customizing-babel-config" rel="noreferrer"><font style="vertical-align: inherit;">https</font></a><font style="vertical-align: inherit;"> : </font></font><a href="https://nextjs.org/docs/#customizing-babel-config" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">//nextjs.org/docs/#customizing-babel-config</font></font></a></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">并使用</font></font><code>preset-env</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">插件</font><font style="vertical-align: inherit;">指定受支持的浏览器</font><font style="vertical-align: inherit;">：</font><a href="https://babeljs.io/docs/en/babel-preset-env#browserslist-integration" rel="noreferrer"><font style="vertical-align: inherit;">https</font></a><font style="vertical-align: inherit;"> : </font></font><a href="https://babeljs.io/docs/en/babel-preset-env#browserslist-integration" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">//babeljs.io/docs/en/babel-preset-env#browserslist-integration</font></font></a></p>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">.babelrc</font></font></strong></p>

<pre><code>"presets": [<font></font>
  ["next/babel", {<font></font>
    "preset-env": {<font></font>
      "useBuiltIns": "entry" //tells the preset to look for browserslist config source<font></font>
    },<font></font>
  ]<font></font>
]<font></font>
</code></pre>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">package.json</font></font></strong></p>

<p><code>"browserslist": "&gt; 0.25%, not dead"</code></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
