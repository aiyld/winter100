---
layout: question
title:  node.js require（）缓存-可能无效？
date:   2020-03-18T09:55:39.000Z
description: 从node.js文档中：  第一次加载模块后将对其进行缓存。这意味着（除其他事项外）每次对require（'foo'）的调用都将获得与返回的对象完全...
img: 
author: 伽罗Tony小卤蛋
category: question
answer: 5
tags: node.js Node.js
topic: Node.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">从node.js文档中：</font></font></p>

<blockquote>
  <p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">第一次加载模块后将对其进行缓存。</font><font style="vertical-align: inherit;">这意味着（除其他事项外）每次对require（'foo'）的调用都将获得与返回的对象完全相同的对象（如果它将解析为相同的文件）。</font></font></p>
</blockquote>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">有没有办法使该缓存无效？</font><font style="vertical-align: inherit;">即对于单元测试，我希望每个测试都可以在一个新对象上进行。</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第2130篇《node.js require（）缓存-可能无效？》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">阳光前端</span>
            <span class="discuss-time">2020.03.18</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果用于单元测试，则另一个好的工具是</font></font><a href="https://github.com/thlorenz/proxyquire" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">proxyquire</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">每次您代理查询模块时，它将使模块缓存无效并缓存一个新的模块。</font><font style="vertical-align: inherit;">它还允许您修改要测试的文件所需的模块。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">小哥凯小小</span>
            <span class="discuss-time">2020.03.18</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我会再向luff的答案添加一行，并更改参数名称：</font></font></p>

<pre><code>function requireCached(_module){<font></font>
    var l = module.children.length;<font></font>
    for (var i = 0; i &lt; l; i++)<font></font>
    {<font></font>
        if (module.children[i].id === require.resolve(_module))<font></font>
        {<font></font>
            module.children.splice(i, 1);<font></font>
            break;<font></font>
        }<font></font>
    }<font></font>
    delete require.cache[require.resolve(_module)];<font></font>
    return require(_module)<font></font>
}<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">小卤蛋LEY</span>
            <span class="discuss-time">2020.03.18</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我不能100％地确定“无效”是什么意思，但是您可以在</font></font><code>require</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">语句</font><font style="vertical-align: inherit;">上方添加以下内容</font><font style="vertical-align: inherit;">以清除缓存：</font></font></p>

<pre><code>Object.keys(require.cache).forEach(function(key) { delete require.cache[key] })
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">从@ Dancrumb的评论采取</font></font><a href="https://stackoverflow.com/a/23686122/1461850"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这里</font></font></a></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">猪猪小宇宙</span>
            <span class="discuss-time">2020.03.18</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">对于使用Jest的任何人，因为Jest进行自己的模块缓存，所以有一个内置函数-只需确保</font></font><code>jest.resetModules</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">运行例如。</font><font style="vertical-align: inherit;">在每个测试之后：</font></font></p>

<pre><code>afterEach( function() {<font></font>
  jest.resetModules();<font></font>
});<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">尝试使用</font></font><a href="https://www.npmjs.com/package/decache" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">decache</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">就像建议另一个答案</font><font style="vertical-align: inherit;">后，发现了这一点</font><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">感谢</font></font><a href="https://github.com/dwyl/decache/issues/27#issuecomment-275871860" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Anthony Garvan</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">功能文档</font></font><a href="https://facebook.github.io/jest/docs/en/configuration.html#resetmodules-boolean" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在这里</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">小卤蛋卡卡西</span>
            <span class="discuss-time">2020.03.18</span>
          </div>
          <div class="discuss-comment"><p><a href="https://github.com/jhnns/rewire"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">rewire</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">非常适合此用例，每次调用都会获得一个新实例。</font><font style="vertical-align: inherit;">轻松的依赖注入，用于node.js单元测试。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">rewire在模块中添加了一个特殊的setter和getter，因此您可以修改它们的行为以进行更好的单元测试。</font><font style="vertical-align: inherit;">你可以</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">为其他模块或全局变量（例如进程泄漏专用变量）注入模拟，将覆盖模块内的变量。</font><font style="vertical-align: inherit;">rewire不会加载文件并评估内容以模拟节点的require机制。</font><font style="vertical-align: inherit;">实际上，它使用节点自身的要求来加载模块。</font><font style="vertical-align: inherit;">因此，您的模块在测试环境中的行为与常规情况下完全一样（修改除外）。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">对所有咖啡因上瘾者来说是个好消息：rewire也可以在Coffee-Script中使用。</font><font style="vertical-align: inherit;">请注意，在这种情况下，需要在devDependencies中列出CoffeeScript。</font></font></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
