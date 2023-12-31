---
layout: question
title:  如何在webpack.config.js中使用ES6？
date:   2020-05-28T07:00:56.000Z
description: 如何在webpack.config中使用ES6？像这个仓库  https //github.com/kriasoft/react-starter-kit...
img: 
author: 村村
category: question
answer: 8
tags: 网络包 Webpack
topic: Webpack
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如何在webpack.config中使用ES6？</font><font style="vertical-align: inherit;">像这个仓库 
 </font></font><a href="https://github.com/kriasoft/react-starter-kit"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">https://github.com/kriasoft/react-starter-kit</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> 
可以吗？</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">例如：</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">使用这个</font></font></p>



<pre class="lang-javascript prettyprint prettyprinted" style=""><code><span class="kwd">import</span><span class="pln"> webpack </span><span class="kwd">from</span><span class="pln"> </span><span class="str">'webpack'</span><span class="pun">;</span></code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">代替</font></font></p>

<pre class="lang-javascript prettyprint prettyprinted" style=""><code><span class="kwd">var</span><span class="pln"> webpack </span><span class="pun">=</span><span class="pln"> require</span><span class="pun">(</span><span class="str">'webpack'</span><span class="pun">);</span></code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这是一种好奇而不是需要。</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第4210篇《如何在webpack.config.js中使用ES6？》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">伽罗</span>
            <span class="discuss-time">2020.05.28</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">大量文件之后...</font></font></p>

<ol>
<li><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">只需安装es2015预设（而不是env !!!）并将其添加到 </font></font></p>

<pre><code>.babelrc:<font></font>
{<font></font>
    "presets": [<font></font>
         ["es2015", { "modules": false }]<font></font>
    ]<font></font>
}<font></font>
</code></pre></li>
<li><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">重命名</font></font><code>webpack.config.js</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">为</font></font><code>webpack.config.babel.js</code></p></li>
</ol></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">阿飞</span>
            <span class="discuss-time">2020.05.28</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我最好的方法与npm脚本一起是 </font></font></p>

<pre><code>node -r babel-register ./node_modules/webpack/bin/webpack
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">并根据您对</font><a href="https://github.com/babel/" rel="nofollow noreferrer"><font style="vertical-align: inherit;">Babel</font></a><font style="vertical-align: inherit;">的要求配置其余脚本</font></font><a href="https://github.com/babel/" rel="nofollow noreferrer"><font style="vertical-align: inherit;"></font></a></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Gil伽罗小宇宙</span>
            <span class="discuss-time">2020.05.28</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">没有足够的代表评论，但我想为所有TypeScript用户添加与上面的@Sandrik类似的解决方案</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我有两个脚本用于指向包含ES6语法的webpack配置（JS文件）。 </font></font></p>

<p><code>"start-dev": "./node_modules/.bin/ts-node ./node_modules/webpack-dev-server/bin/webpack-dev-server.js --config ./webpack/webpack.config.dev.js"</code></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">和</font></font></p>

<p><code>"build": "./node_modules/.bin/ts-node ./node_modules/webpack/bin/webpack.js --config webpack/webpack.config.js"</code></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">神乐</span>
            <span class="discuss-time">2020.05.28</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">另一种方法是对节点使用require参数：</font></font></p>

<p><code>node -r babel-register ./node_modules/webpack/bin/webpack</code></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">发现这样的</font></font><a href="https://github.com/chentsulin/electron-react-boilerplate/blob/master/package.json" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">电子反应，样板</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，看看</font></font><code>build-main</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">和</font></font><code>build-renderer</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">脚本。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">西里神奇</span>
            <span class="discuss-time">2020.05.28</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这就是使用webpack 4对我有用的。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在</font></font><code>package.json</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">：</font></font></p>

<pre><code>"scripts": {<font></font>
    "dev": "cross-env APP_ENV=dev webpack-serve --require @babel/register"<font></font>
},<font></font>
<font></font>
"devDependencies": {<font></font>
    "@babel/core": "^7.0.0-rc.1",<font></font>
    "@babel/register": "^7.0.0-rc.1",<font></font>
    "@babel/preset-env": "^7.0.0-rc.1",<font></font>
    "babel-plugin-transform-es2015-modules-commonjs": "^6.26.2"<font></font>
},<font></font>
<font></font>
"babel": {<font></font>
  "presets": [<font></font>
    ["@babel/preset-env", {<font></font>
      "targets": {<font></font>
        "node": "current"<font></font>
      }<font></font>
    }]<font></font>
  ],<font></font>
  "plugins": [<font></font>
    "transform-es2015-modules-commonjs"<font></font>
  ]<font></font>
}<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您可以清楚地看到每个依赖项的使用方式，因此不要感到意外。</font></font></p>

<p><em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">注意我正在使用</font></font><a href="https://github.com/webpack-contrib/webpack-serve" rel="nofollow noreferrer"><code>webpack-serve</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">--require</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，但是如果您想使用该</font></font><code>webpack</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">命令，请将其替换为</font></font><code>webpack --config-register</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">无论哪种情况，</font></font><code>@babel/register</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">都需要进行这项工作。</font></font></em></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">就是这样！</font></font></p>

<p><code>yarn dev</code></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">而且您可以</font></font><code>es6</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在配置中</font><font style="vertical-align: inherit;">使用</font><font style="vertical-align: inherit;">！</font></font></p>

<hr>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">对于</font></font><code>webpack-dev-server</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，请使用</font></font><code>--config-register</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">与</font></font><code>webpack</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">命令</font><font style="vertical-align: inherit;">相同</font><font style="vertical-align: inherit;">的</font><font style="vertical-align: inherit;">选项</font></font></p>

<hr>

<h3><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">注意：</font></font></h3>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">无需将配置文件重命名为</font></font><code>webpack.config.babel.js</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（如已接受的答案所建议）。</font></font><code>webpack.config.js</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">会很好。</font></font></strong></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">GO</span>
            <span class="discuss-time">2020.05.28</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">尝试将您的配置命名为</font></font><code>webpack.config.babel.js</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">您应该</font><font style="vertical-align: inherit;">在项目中包含</font></font><a href="https://www.npmjs.com/package/babel-register"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">babel-register</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">在</font></font><a href="https://github.com/react-bootstrap/react-router-bootstrap"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">react-router-bootstrap的</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">示例</font><font style="vertical-align: inherit;">。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Webpack依靠</font><font style="vertical-align: inherit;">内部</font></font><a href="https://www.npmjs.com/package/interpret"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">解释</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">来完成这项工作。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">阿飞</span>
            <span class="discuss-time">2020.05.28</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">另一种方法是使用npm脚本，例如：</font></font><code>"webpack": "babel-node ./node_modules/webpack/bin/webpack"</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，然后像这样运行：</font></font><code>npm run webpack</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Itachi</span>
            <span class="discuss-time">2020.05.28</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这确实很容易，但是从任何答案中对我来说都不是很明显，所以如果其他人像我一样困惑： </font></font></p>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">只需</font></font><code>.babel</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在扩展名之前</font><font style="vertical-align: inherit;">附加</font><font style="vertical-align: inherit;">到文件名的一部分</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（假设您已将其</font></font><code>babel-register</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">安装为依赖项）即可。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">例：</font></font></p>

<pre><code>mv webpack.config.js webpack.config.babel.js
</code></pre></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
