---
layout: question
title:  如何使用Node.js解析JSON？
date:   2020-03-13T09:59:52.000Z
description: 我应该如何使用Node.js解析JSON？是否有一些模块可以安全地验证和解析JSON？...
img: 
author: 神奇Davaid
category: question
answer: 14
tags: JavaScript
topic: JavaScript
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我应该如何使用Node.js解析JSON？</font><font style="vertical-align: inherit;">是否有一些模块可以安全地验证和解析JSON？</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第1505篇《如何使用Node.js解析JSON？》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">泡芙Green</span>
            <span class="discuss-time">2020.03.13</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">很简单，您可以使用将JSON转换为字符串</font></font><code>JSON.stringify(json_obj)</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，并</font><font style="vertical-align: inherit;">使用</font><font style="vertical-align: inherit;">将字符串转换为JSON </font></font><code>JSON.parse("your json string")</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">飞云神奇</span>
            <span class="discuss-time">2020.03.13</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">无需其他模块。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">
只是使用</font></font><br>
<code>var parsedObj = JSON.parse(yourObj);</code><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">
我不认为与此有关的任何安全问题</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">小宇宙樱</span>
            <span class="discuss-time">2020.03.13</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如以上答案中所述，我们可以</font></font><code>JSON.parse()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">将字符串解析为JSON，但是在解析之前，请务必解析正确的数据，否则可能会导致整个应用程序崩溃</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这样可以安全使用</font></font></p>

<pre><code>let parsedObj = {}<font></font>
try {<font></font>
    parsedObj = JSON.parse(data);<font></font>
} catch(e) {<font></font>
    console.log("Cannot parse because data is not is proper json format")<font></font>
}<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">小卤蛋梅</span>
            <span class="discuss-time">2020.03.13</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">为了安全起见，请使用它</font></font></p>

<pre><code>var data = JSON.parse(Buffer.concat(arr).toString());
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">TomTony</span>
            <span class="discuss-time">2020.03.13</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您可以使用JSON.parse（）（这是一个内置函数，可能会迫使您使用try-catch语句包装它）。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">或使用JSON解析npm库，例如</font></font><a href="https://www.npmjs.com/package/parse-json-or" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">json-parse-or</font></font></a></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">小哥Jim</span>
            <span class="discuss-time">2020.03.13</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">始终确保在</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">try catch</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">块中</font><font style="vertical-align: inherit;">使用JSON.parse，</font><font style="vertical-align: inherit;">因为如果json中有一些损坏的数据，则节点总是会引发意外错误，因此请使用此代码代替简单的JSON.Parse</font></font></p>

<pre><code>try{<font></font>
     JSON.parse(data)<font></font>
}<font></font>
catch(e){<font></font>
   throw new Error("data is corrupted")<font></font>
  }<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">老丝村村</span>
            <span class="discuss-time">2020.03.13</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">JSON.parse无法确保您解析的json字符串的安全。</font><font style="vertical-align: inherit;">您应该查看</font></font><a href="https://www.npmjs.com/package/json-safe-parse" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">json-safe-parse之</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">类的库或类似的库。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">从json-safe-parse npm页面： </font></font></p>

<blockquote>
  <p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">JSON.parse很棒，但是它在JavaScript上下文中有一个严重的缺陷：它允许您覆盖继承的属性。</font><font style="vertical-align: inherit;">如果您要从不受信任的来源（例如，用户）解析JSON，并在其上调用您希望存在的函数，这可能会成为问题。</font></font></p>
</blockquote></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">小小理查德</span>
            <span class="discuss-time">2020.03.13</span>
          </div>
          <div class="discuss-comment"><pre><code>JSON.parse("your string");
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">就这样。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Itachi泡芙Pro</span>
            <span class="discuss-time">2020.03.13</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这里的每个人都讲过JSON.parse，所以我想说些别的。</font><font style="vertical-align: inherit;">有一个很棒的模块，可以</font><font style="vertical-align: inherit;">与许多中间件</font></font><a href="http://www.senchalabs.org/connect/" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">连接</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，以使应用程序的开发变得更轻松，更好。</font><font style="vertical-align: inherit;">中间件之一是</font></font><a href="http://www.senchalabs.org/connect/bodyParser.html" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">bodyParser</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">它解析JSON，html表单等。还有一个仅用于JSON解析</font></font><a href="http://www.senchalabs.org/connect/json.html" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">noop</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">的特定中间件</font><font style="vertical-align: inherit;">。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">看一下上面的链接，它可能对您确实有帮助。 </font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Harry小胖</span>
            <span class="discuss-time">2020.03.13</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">包括</font></font><code>node-fs</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">库。</font></font></p>

<pre><code>var fs = require("fs");<font></font>
var file = JSON.parse(fs.readFileSync("./PATH/data.json", "utf8"));<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">有关“ fs”库的更多信息，请参见位于</font><a href="http://nodejs.org/api/fs.html" rel="noreferrer"><font style="vertical-align: inherit;">http://nodejs.org/api/fs.html</font></a><font style="vertical-align: inherit;">的文档。</font></font><a href="http://nodejs.org/api/fs.html" rel="noreferrer"><font style="vertical-align: inherit;"></font></a></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">阿飞小卤蛋</span>
            <span class="discuss-time">2020.03.13</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">由于您不知道您的字符串实际上是有效的，因此我将其放在try catch中。</font><font style="vertical-align: inherit;">另外，由于try catch块未按节点进行优化，因此我会将整个内容放入另一个函数中：</font></font></p>

<pre><code>function tryParseJson(str) {<font></font>
    try {<font></font>
        return JSON.parse(str);<font></font>
    } catch (ex) {<font></font>
        return null;<font></font>
    }<font></font>
}<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">或以“异步样式”</font></font></p>

<pre><code>function tryParseJson(str, callback) {<font></font>
    process.nextTick(function () {<font></font>
      try {<font></font>
          callback(null, JSON.parse(str));<font></font>
      } catch (ex) {<font></font>
          callback(ex)<font></font>
      }<font></font>
    })<font></font>
}<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">宝儿逆天</span>
            <span class="discuss-time">2020.03.13</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我想提一下，全局JSON对象还有其他选择。
</font></font><code>JSON.parse</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">并且</font></font><code>JSON.stringify</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">都是同步的，因此如果您要处理大对象，则可能需要检出一些异步JSON模块。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">看看：</font><a href="https://github.com/joyent/node/wiki/Modules#wiki-parsers-json" rel="noreferrer"><font style="vertical-align: inherit;">https</font></a><font style="vertical-align: inherit;"> : </font></font><a href="https://github.com/joyent/node/wiki/Modules#wiki-parsers-json" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">//github.com/joyent/node/wiki/Modules#wiki-parsers-json</font></font></a></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">梅老丝</span>
            <span class="discuss-time">2020.03.13</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您可以简单地使用</font></font><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/parse" rel="noreferrer"><code>JSON.parse</code></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p>

<p><font style="vertical-align: inherit;"></font><code>JSON</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">对象</font><font style="vertical-align: inherit;">的定义</font></font><a href="http://es5.github.com/#x15.12" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">是ECMAScript 5规范的一部分</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">node.js基于Google Chrome的</font></font><a href="https://developers.google.com/v8/" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">V8</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">引擎</font><font style="vertical-align: inherit;">构建</font><font style="vertical-align: inherit;">，该引擎遵循ECMA标准。</font><font style="vertical-align: inherit;">因此，node.js也有一个全局对象</font><a href="https://developer.mozilla.org/En/Using_JSON_in_Firefox" rel="noreferrer"><sup><em><font style="vertical-align: inherit;">[docs]</font></em></sup></a><font style="vertical-align: inherit;">。</font></font><a href="https://developer.mozilla.org/En/Using_JSON_in_Firefox" rel="noreferrer"><strong><code>JSON</code></strong><sup><em><font style="vertical-align: inherit;"></font></em></sup></a><font style="vertical-align: inherit;"></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">注意- </font></font><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/parse" rel="noreferrer"><code>JSON.parse</code></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">可以占用当前线程，因为它是一种同步方法。</font><font style="vertical-align: inherit;">因此，如果您打算解析大型JSON对象，请使用流式JSON解析器。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Jim前端</span>
            <span class="discuss-time">2020.03.13</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">使用</font></font><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">JSON对象</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">：</font></font></p>

<pre><code>JSON.parse(str);
</code></pre></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
