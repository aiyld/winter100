---
layout: question
title:  Co.js和bluebird.js –有什么区别？
date:   2020-04-07T10:52:40.000Z
description: 有人可以帮助我了解在ES6 Harmony中使用Koa.js和Bluebird.js的区别。具体来说，co( function \* () {  //...
img: 
author: 斯丁
category: question
answer: 2
tags: ecmascript-和谐 KoaJS
topic: KoaJS
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">有人可以帮助我了解在ES6 Harmony中使用Koa.js和Bluebird.js的区别。</font><font style="vertical-align: inherit;">具体来说，</font></font></p>

<pre><code>co( function * () {<font></font>
  //stuff<font></font>
} );<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">相比于，</font></font></p>

<pre><code>Promise.coroutine( function * () {<font></font>
  //stuff<font></font>
} );<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">似乎Koa应该使用Bluebird而不是重新创建轮子。</font><font style="vertical-align: inherit;">有什么不同？</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第4146篇《Co.js和bluebird.js –有什么区别？》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">老丝阿飞</span>
            <span class="discuss-time">2020.04.07</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">有一个</font><font style="vertical-align: inherit;">关于使用Bluebird的</font></font><a href="https://github.com/visionmedia/co/pull/134" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">请求</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">那里的评论应该使某些事情更清楚。</font><font style="vertical-align: inherit;">co依赖于0.11中提供的本机V8 Promises功能，而Bluebird的目标是也可以在0.10中很好地工作。</font><font style="vertical-align: inherit;">您可以在低于0.11的版本中使用co，但是Bluebird将是一个更好的选择。</font><font style="vertical-align: inherit;">在该链接中，您可以看到基准测试表明co不比Bluebird慢，因此该参数是错误的。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">另外，只有300行代码，坚持使用KISS通常是一个好习惯。</font><font style="vertical-align: inherit;">因此，它不是在重新创建轮子。</font><font style="vertical-align: inherit;">它正在减肥。</font><font style="vertical-align: inherit;">您可以在几分钟内阅读代码并了解它的作用。</font><font style="vertical-align: inherit;">我花了一个小时来阅读Bluebird API文档。</font><font style="vertical-align: inherit;">还提到V8的实现已</font></font><a href="https://github.com/joyent/node/issues/7714" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">中断</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，因此Bluebird可能会在过渡期内使用。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">蛋蛋猿</span>
            <span class="discuss-time">2020.04.07</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">就目前而言，不同之处在于Koa不仅可以实现承诺，而且还可以提供更多收益。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">但是，添加了一项功能，该功能不仅允许产生回调，重击等，而且还允许您想到任何随便的东西。</font><font style="vertical-align: inherit;">蓝鸟也是最快的。</font><font style="vertical-align: inherit;">因此，在此版本之后，koa应该确实只是在使用蓝鸟。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">参见</font></font><a href="https://github.com/petkaantonov/bluebird/issues/131#issuecomment-36975495" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">https://github.com/petkaantonov/bluebird/issues/131#issuecomment-36975495</font></font></a></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
