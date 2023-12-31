---
layout: question
title:  Node.js-SyntaxError：意外的令牌导入
date:   2020-03-16T07:16:04.000Z
description: 我不明白怎么了。节点v5.6.0 NPM v3.10.6代码：function (exports, require, module, __fil...
img: 
author: 小小
category: question
answer: 6
tags: JavaScript
topic: JavaScript
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我不明白怎么了。</font><font style="vertical-align: inherit;">节点v5.6.0 NPM v3.10.6</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">代码：
</font></font></p>

<pre><code>function (exports, require, module, __filename, __dirname) {<font></font>
    import express from 'express'<font></font>
};<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">错误：</font></font></p>

<pre><code>SyntaxError: Unexpected token import<font></font>
    at exports.runInThisContext (vm.js:53:16)<font></font>
    at Module._compile (module.js:387:25)<font></font>
    at Object.Module._extensions..js (module.js:422:10)<font></font>
    at Module.load (module.js:357:32)<font></font>
    at Function.Module._load (module.js:314:12)<font></font>
    at Function.Module.runMain (module.js:447:10)<font></font>
    at startup (node.js:140:18)<font></font>
    at node.js:1001:3<font></font>
</code></pre></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第1785篇《Node.js-SyntaxError：意外的令牌导入》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Tony小胖</span>
            <span class="discuss-time">2020.03.16</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">就我而言，它是在照管</font></font><code>.babelrc</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">文件，并且应包含以下内容：</font></font></p>

<pre><code>{<font></font>
  "presets": ["es2015-node5", "stage-3"],<font></font>
  "plugins": []<font></font>
}<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">JinJinDavaid卡卡西</span>
            <span class="discuss-time">2020.03.16</span>
          </div>
          <div class="discuss-comment"><p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">babel 7提案</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> 
可以添加开发依赖吗</font></font></p>

<pre><code>npm i -D @babel/core @babel/preset-env @babel/register
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">并在根目录中添加.babelrc</font></font></p>

<pre><code>{<font></font>
"presets": [<font></font>
  [<font></font>
    "@babel/preset-env",<font></font>
    {<font></font>
      "targets": {<font></font>
        "node": "current"<font></font>
     }<font></font>
    }<font></font>
  ]<font></font>
 ]<font></font>
}<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">并添加到.js文件</font></font></p>

<pre><code>require("@babel/register")
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">或者，如果您在cli中运行它，则可以将require钩子用作-r @ babel / register，例如。</font></font></p>

<pre><code>$node -r @babel/register executeMyFileWithESModules.js
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">梅JinJin十三</span>
            <span class="discuss-time">2020.03.16</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果可以使用“ babel”，请尝试在package.json（-presets = es2015）中添加构建脚本，如下所示。</font><font style="vertical-align: inherit;">它可以将导入代码预编译到es2015</font></font></p>

<pre><code>"build": "babel server --out-dir build --presets=es2015 &amp;&amp; webpack"
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Mandy</span>
            <span class="discuss-time">2020.03.16</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我</font></font><code>esm</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">没有被提及</font><font style="vertical-align: inherit;">感到震惊</font><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">这个小巧但功能强大的软件包允许您使用</font></font><code>import</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">或</font></font><code>require</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在您的项目中安装esm</font></font></strong></p>

<p><code>$ npm install --save esm</code></p>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">更新您的节点启动脚本以使用esm</font></font></strong></p>

<p><code>node -r esm app.js</code></p>

<p><code>esm</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">正常工作。</font><font style="vertical-align: inherit;">我浪费的时间TON与</font></font><code>.mjs</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">和</font></font><code>--experimental-modules</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">只找出一个</font></font><code>.mjs</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">文件无法导入文件使用</font></font><code>require</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">或</font></font><code>module.exports</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">这是一个巨大的问题，但是</font></font><code>esm</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">允许您混合搭配，只是弄清楚了…… </font></font><code>esm</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">就可以了。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Eva阿飞</span>
            <span class="discuss-time">2020.03.16</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">随着Node.js的V12的（这是现在可能还算稳定，但仍标有“实验性”），你有两个选择使用ESM（</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">ē</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> CMA </font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">小号</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> CRIPT </font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">中号</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在Node.js的odules）（的文件，有一个逃避字符串的第三种方法），这就是</font></font><a href="https://nodejs.org/api/esm.html" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">文档</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">所说的内容：</font></font></p>

<blockquote>
<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">该</font></font><code>--experimental-modules</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">标志可用于启用对ECMAScript模块（ES模块）的支持。</font></font></p>
<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">启用后，Node.js在</font></font><code>node</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">作为初始输入</font><font style="vertical-align: inherit;">传递给ES模块时</font><font style="vertical-align: inherit;">，或</font></font><code>import</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在ES模块代码内</font><font style="vertical-align: inherit;">的</font><font style="vertical-align: inherit;">语句</font><font style="vertical-align: inherit;">引用</font><font style="vertical-align: inherit;">时，会将以下模块
 </font><font style="vertical-align: inherit;">视为</font><font style="vertical-align: inherit;">ES模块：</font></font></p>
<ul>
<li>
<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">以结尾的文件</font></font><code>.mjs</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p>
</li>
<li>
<p><font style="vertical-align: inherit;"></font><code>.js</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">当最近的父</font></font><code>package.json</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">文件包含</font></font><code>"type"</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">值为的</font><font style="vertical-align: inherit;">顶级字段时</font><font style="vertical-align: inherit;">，以
 </font><font style="vertical-align: inherit;">结尾的</font><font style="vertical-align: inherit;">文件或无扩展名的文件
 </font></font><code>"module"</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p>
</li>
<li>
<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">带有标志的</font><font style="vertical-align: inherit;">字符串作为参数传递给</font></font><code>--eval</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">或</font><font style="vertical-align: inherit;">通过</font></font><code>--print</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">管道传递给
 </font></font><code>node</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">via </font><font style="vertical-align: inherit;">。</font></font><code>STDIN</code><font style="vertical-align: inherit;"></font><code>--input-type=module</code><font style="vertical-align: inherit;"></font></p>
</li>
</ul>
<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Node.js将所有其他形式的输入视为CommonJS，例如，</font></font><code>.js</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">最近的父</font></font><code>package.json</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">文件不包含顶级</font></font><code>"type"</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">
字段的文件，或者不带flag的字符串输入</font></font><code>--input-type</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">此行为是为了保持向后兼容性。</font><font style="vertical-align: inherit;">但是，既然Node.js同时支持CommonJS和ES模块，那么最好在可能的情况下使其明确。</font><font style="vertical-align: inherit;">当</font></font><code>node</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">作为初始输入</font><font style="vertical-align: inherit;">传递</font><font style="vertical-align: inherit;">或被</font></font><code>import</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">ES模块代码中的语句</font><font style="vertical-align: inherit;">引用时，</font><font style="vertical-align: inherit;">Node.js将把以下内容视为CommonJS </font><font style="vertical-align: inherit;">：</font></font></p>
<ul>
<li>
<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">以结尾的文件</font></font><code>.cjs</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p>
</li>
<li>
<p><font style="vertical-align: inherit;"></font><code>.js</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">当最近的父</font></font><code>package.json</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">文件包含</font></font><code>"type"</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">值为的</font><font style="vertical-align: inherit;">顶级字段时</font><font style="vertical-align: inherit;">，以
 </font><font style="vertical-align: inherit;">结尾的</font><font style="vertical-align: inherit;">文件或无扩展名的文件
 </font></font><code>"commonjs"</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p>
</li>
<li>
<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">带有标志的</font><font style="vertical-align: inherit;">字符串作为参数传递给</font></font><code>--eval</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">或</font><font style="vertical-align: inherit;">通过</font></font><code>--print</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">管道传递给
 </font></font><code>node</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">via </font><font style="vertical-align: inherit;">。</font></font><code>STDIN</code><font style="vertical-align: inherit;"></font><code>--input-type=commonjs</code><font style="vertical-align: inherit;"></font></p>
</li>
</ul>
</blockquote></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">村村凯</span>
            <span class="discuss-time">2020.03.16</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">不幸的是，Node.js尚不支持ES6 </font></font><code>import</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">要完成您要尝试执行的操作（导入Express模块​​），此代码就足够了</font></font></p>

<pre><code>var express = require("express");
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">另外，请确保通过运行安装了Express</font></font></p>

<pre><code>$ npm install express
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">有关学习Node.js的更多信息，</font><font style="vertical-align: inherit;">请参见</font></font><a href="https://nodejs.org/en/docs/" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Node.js文档</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
