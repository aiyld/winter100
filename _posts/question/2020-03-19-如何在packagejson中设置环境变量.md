---
layout: question
title:  如何在package.json中设置环境变量
date:   2020-03-19T03:19:09.000Z
description: 如何从内部设置一些环境变量package.json以与npm start类似命令一起使用？这是我目前所拥有的package.json：{  .....
img: 
author: 梅米亚
category: question
answer: 9
tags: node.js Node.js
topic: Node.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如何从内部设置一些环境变量</font></font><code>package.json</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">以与</font></font><code>npm start</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">类似命令</font><font style="vertical-align: inherit;">一起使用</font><font style="vertical-align: inherit;">？</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这是我目前所拥有的</font></font><code>package.json</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">：</font></font></p>

<pre class="lang-json prettyprint-override"><code>{<font></font>
  ...<font></font>
  "scripts": {<font></font>
    "help": "tagove help",<font></font>
    "start": "tagove start"<font></font>
  }<font></font>
  ...<font></font>
}<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我想</font></font><code>NODE_ENV</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在启动脚本中</font><font style="vertical-align: inherit;">设置环境变量（例如</font><font style="vertical-align: inherit;">），同时仍然能够仅通过一个命令来启动应用程序</font></font><code>npm start</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第2290篇《如何在package.json中设置环境变量》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">ItachiA</span>
            <span class="discuss-time">2020.03.19</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这将在</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Windows控制台中运行</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">：</font></font></p>

<pre><code>"scripts": {<font></font>
  "aaa": "set TMP=test &amp;&amp; npm run bbb",<font></font>
  "bbb": "echo %TMP%"<font></font>
}<font></font>
</code></pre>

<p><code>npm run aaa</code></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">输出：
</font></font><code>test</code></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">有关</font><font style="vertical-align: inherit;">详细信息，</font><font style="vertical-align: inherit;">请参</font></font><a href="https://stackoverflow.com/a/55238291/1844247"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">见此答案</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Itachi达蒙Green</span>
            <span class="discuss-time">2020.03.19</span>
          </div>
          <div class="discuss-comment"><pre class="lang-json prettyprint-override"><code>{<font></font>
  ...<font></font>
  "scripts": {<font></font>
    "start": "ENV NODE_ENV=production someapp --options"<font></font>
  }<font></font>
  ...<font></font>
}<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">西里GO</span>
            <span class="discuss-time">2020.03.19</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您不应在中设置ENV变量</font></font><code>package.json</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">actionhero用于</font></font><code>NODE_ENV</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">允许您更改从中的文件加载的配置选项</font></font><code>./config</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">检出</font></font><a href="https://github.com/evantahler/actionhero/blob/master/config/redis.js" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">redis配置文件</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，并查看如何使用NODE_ENV更改以下版本中的数据库选项</font></font><code>NODE_ENV=test</code></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果您想使用其他ENV变量来设置内容（也许是HTTP端口），则仍然无需更改中的任何内容</font></font><code>package.json</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">例如，如果您</font></font><code>PORT=1234</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在ENV中进行</font><font style="vertical-align: inherit;">设置</font><font style="vertical-align: inherit;">并想将其用作中的HTTP端口</font></font><code>NODE_ENV=production</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，则只需在相关的配置文件IE中引用它即可：</font></font></p>

<pre><code># in config/servers/web.js<font></font>
exports.production = { <font></font>
  servers: {<font></font>
    web: function(api){<font></font>
      return {<font></font>
       port: process.env.PORT<font></font>
      }<font></font>
    }<font></font>
  }<font></font>
}<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">理查德神无Mandy</span>
            <span class="discuss-time">2020.03.19</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">对于较大的环境变量集或要重用它们时，可以使用</font></font><a href="https://github.com/toddbluhm/env-cmd" rel="nofollow noreferrer"><code>env-cmd</code></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p>

<p><code>./.env</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> 文件：</font></font></p>

<pre><code># This is a comment<font></font>
ENV1=THANKS<font></font>
ENV2=FOR ALL<font></font>
ENV3=THE FISH<font></font>
</code></pre>

<p><code>./package.json</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">：</font></font></p>

<pre><code>{<font></font>
  "scripts": {<font></font>
    "test": "env-cmd mocha -R spec"<font></font>
  }<font></font>
}<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">十三西里GO</span>
            <span class="discuss-time">2020.03.19</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">因为我经常发现自己使用多个环境变量，所以我发现将它们保存在单独的</font></font><code>.env</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">文件中</font><font style="vertical-align: inherit;">很有用</font><font style="vertical-align: inherit;">（请确保从源代码管理中忽略它）。</font></font></p>

<pre><code>VAR_A=Hello World<font></font>
VAR_B=format the .env file like this with new vars separated by a line break<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">然后</font></font><code>export $(cat .env | xargs) &amp;&amp;</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在脚本命令之前添加。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">例：</font></font></p>

<pre class="lang-json prettyprint-override"><code>{<font></font>
  ...<font></font>
  "scripts": {<font></font>
    ...<font></font>
    "start": "export $(cat .env | xargs) &amp;&amp; echo do your thing here",<font></font>
    "env": "export $(cat .env | xargs) &amp;&amp; env",<font></font>
    "env-windows": "export $(cat .env | xargs) &amp;&amp; set"<font></font>
  }<font></font>
  ...<font></font>
}<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">对于测试，您可以通过运行</font></font><code>npm run env</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（linux）或</font></font><code>npm run env-windows</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（windows）</font><font style="vertical-align: inherit;">查看env变量</font><font style="vertical-align: inherit;">。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">LSam</span>
            <span class="discuss-time">2020.03.19</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在Windows上尝试通过替换以下方法</font></font><code>YOURENV</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">：</font></font></p>

<pre class="lang-json prettyprint-override"><code>  {<font></font>
    ...<font></font>
     "scripts": {<font></font>
       "help": "set NODE_ENV=YOURENV &amp;&amp; tagove help",<font></font>
       "start": "set NODE_ENV=YOURENV &amp;&amp; tagove start"<font></font>
     }<font></font>
    ...<font></font>
  }<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">宝儿米亚飞云</span>
            <span class="discuss-time">2020.03.19</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我只是想在这里加两分钱，供将来的Node-explorer使用。</font><font style="vertical-align: inherit;">在我的Ubuntu 14.04上</font></font><code>NODE_ENV=test</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">无法正常工作，我不得不使用</font></font><code>export NODE_ENV=test</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">之后也</font></font><code>NODE_ENV=test</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">开始正常工作，很奇怪。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如前所述，您必须在Windows上使用，</font></font><code>set NODE_ENV=test</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">但是对于跨平台解决方案，cross-env库似乎无法解决问题，您确实需要一个库来执行此操作：</font></font></p>

<pre class="lang-js prettyprint-override"><code>export NODE_ENV=test || set NODE_ENV=test&amp;&amp; yadda yadda
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">需要竖线，否则Windows会在无法识别的</font></font><code>export NODE_ENV</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">命令：D </font><font style="vertical-align: inherit;">上崩溃</font><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">邓诺（Dunno）关于尾随的空间，但只是要确保我也将其移开了。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">乐小小猪猪</span>
            <span class="discuss-time">2020.03.19</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">只需使用NPM包</font></font><a href="https://www.npmjs.com/package/cross-env" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">cross-env即可</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">超级容易。</font><font style="vertical-align: inherit;">适用于Windows，Linux和所有环境。</font><font style="vertical-align: inherit;">请注意，您没有使用&amp;&amp;转到下一个任务。</font><font style="vertical-align: inherit;">您只需设置环境，然后开始下一个任务。</font><font style="vertical-align: inherit;">感谢</font></font><a href="https://stackoverflow.com/users/2130585/mikekidder"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">@mikekidder</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在建议</font></font><a href="https://stackoverflow.com/questions/25112510/how-to-set-environment-variables-from-within-package-json-node-js#comment57929242_27090755"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">的意见，一个</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在这里。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">从文档：</font></font></p>

<pre class="lang-json prettyprint-override"><code>{<font></font>
  "scripts": {<font></font>
    "build": "cross-env NODE_ENV=production OTHERFLAG=myValue webpack --config build/webpack.config.js"<font></font>
  }<font></font>
}<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">请注意，如果要设置多个全局变量，则只需依次声明它们，然后执行命令即可。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">最终，执行的命令（使用spawn）是：</font></font></p>

<pre><code>webpack --config build/webpack.config.js
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">该</font></font><code>NODE_ENV</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">环境变量将通过交ENV被设置</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">飞云Pro猴子</span>
            <span class="discuss-time">2020.03.19</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在脚本命令中设置环境变量：</font></font></p>

<pre class="lang-json prettyprint-override"><code>...<font></font>
"scripts": {<font></font>
  "start": "node app.js",<font></font>
  "test": "env NODE_ENV=test mocha --reporter spec"<font></font>
},<font></font>
...<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">然后</font></font><code>process.env.NODE_ENV</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在您的应用中</font><font style="vertical-align: inherit;">使用</font><font style="vertical-align: inherit;">。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">注意：</font></font><code>env</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">确保它可以跨平台使用。</font><font style="vertical-align: inherit;">如果只关心Mac / Linux，则可以忽略它。</font></font></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
