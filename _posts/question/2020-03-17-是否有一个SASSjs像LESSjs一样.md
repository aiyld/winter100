---
layout: question
title:  是否有一个SASS.js？像LESS.js一样？
date:   2020-03-17T10:14:17.000Z
description: 我已经使用LESS.js之前。易于使用，类似<link rel="stylesheet/less" href="main.less" type="te...
img: 
author: Davaid神无
category: question
answer: 6
tags: css CSS
topic: CSS
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我已经使用</font></font><a href="https://github.com/cloudhead/less.js/tree/" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">LESS.js</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">之前。</font><font style="vertical-align: inherit;">易于使用，类似</font></font></p>

<pre><code>&lt;link rel="stylesheet/less" href="main.less" type="text/css"&gt;<font></font>
&lt;script src="less.js" type="text/javascript"&gt;&lt;/script&gt;<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我看到</font></font><a href="https://github.com/visionmedia/sass.js/tree/" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">SASS.js</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">如何以类似方式使用它？</font><font style="vertical-align: inherit;">解析SASS文件以立即在HTML中使用。</font><font style="vertical-align: inherit;">似乎SASS.js更适合与</font></font><a href="http://en.wikipedia.org/wiki/Node.js" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Node.js</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">一起使用</font><font style="vertical-align: inherit;">？</font></font></p>

<pre><code>var sass = require('sass')<font></font>
sass.render('... string of sass ...')<font></font>
// =&gt; '... string of css ...'<font></font>
<font></font>
sass.collect('... string of sass ...')<font></font>
// =&gt; { selectors: [...], variables: { ... }, mixins: { ... }}<font></font>
</code></pre></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第1974篇《是否有一个SASS.js？像LESS.js一样？》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Pro泡芙猿</span>
            <span class="discuss-time">2020.03.17</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您绝对不应该让所有用户都编译样式表，但是javascript实现也可以在服务器上运行。</font><font style="vertical-align: inherit;">我也在寻找javascript sass实现-在node.js应用程序中使用。</font><font style="vertical-align: inherit;">这是Sass团队正在考虑的事情吗？</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">凯泡芙JinJin</span>
            <span class="discuss-time">2020.03.17</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"></font><a href="http://en.wikipedia.org/wiki/GitHub" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">GitHub上</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">有一个尝试</font><font style="vertical-align: inherit;">，</font></font><a href="https://github.com/bmavity/scss-js" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">scss-js</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">但是，它不完整，并且在五个月内没有任何提交。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">村村理查德</span>
            <span class="discuss-time">2020.03.17</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我刚刚发现了一个有趣的Sass.js游乐场。</font><font style="vertical-align: inherit;">这些年来，有些事情可能已经改变。</font><font style="vertical-align: inherit;">看一下这个：</font></font></p>

<p><a href="http://medialize.github.io/playground.sass.js/" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">http://medialize.github.io/playground.sass.js/</font></font></a></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">樱猿</span>
            <span class="discuss-time">2020.03.17</span>
          </div>
          <div class="discuss-comment"><p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">是</font></font></strong></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">正如我们所期望的，在用</font></font><a href="https://github.com/sass/libsass" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">C ++</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">重写之后</font><font style="vertical-align: inherit;">，可以通过</font></font><a href="https://github.com/kripken/emscripten" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Emscripten</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在Javascript中对其进行编译</font><font style="vertical-align: inherit;">。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这是浏览器版本：</font><a href="https://github.com/medialize/sass.js/" rel="nofollow noreferrer"><font style="vertical-align: inherit;">https</font></a><font style="vertical-align: inherit;"> : </font></font><a href="https://github.com/medialize/sass.js/" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">//github.com/medialize/sass.js/</font></font></a></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">按照他们的建议，对于节点，您可以使用以下命令：</font><a href="https://github.com/sass/node-sass" rel="nofollow noreferrer"><font style="vertical-align: inherit;">https</font></a><font style="vertical-align: inherit;"> : </font></font><a href="https://github.com/sass/node-sass" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">//github.com/sass/node-sass</font></font></a></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Jim十三</span>
            <span class="discuss-time">2020.03.17</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">没有官方批准的sass或scss JavaScript实现。</font><font style="vertical-align: inherit;">我看到了一些正在实施的实现，但是目前我不推荐使用这些实现。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">但是，请注意以下几点：</font></font></p>

<ol>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">当您一次可以对所有用户进行编译时，为什么要让所有用户编译样式表。</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果禁用JavaScript，您的网站会是什么样子。</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果您决定将来更改为服务器端实现，则必须相应地更改所有模板。</font></font></li>
</ol>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">因此，尽管需要更多设置才能开始，但我们（sass核心团队）认为服务器端编译是最好的长期方法。</font><font style="vertical-align: inherit;">同样，较少的开发人员更喜欢将服务器端编译用于生产样式表。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">猿JinJin</span>
            <span class="discuss-time">2020.03.17</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">由于visionmeda / sass.js不再可用，并且scss-js两年内都没有更新，所以我可能对</font></font><a href="https://github.com/medialize/sass.js/"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">sass.js</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">感兴趣</font><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">这是</font><font style="vertical-align: inherit;">使用Emscripten编译为JavaScript </font><font style="vertical-align: inherit;">的C ++库</font></font><a href="https://github.com/hcatlin/libsass/"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">libsass</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（也由</font></font><a href="https://github.com/andrew/node-sass"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">node-sass</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">使用）。</font><font style="vertical-align: inherit;">可以在</font></font><a href="https://github.com/mgreter/sass.link.js"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">sass.link.js中</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">找到编译以html链接或内联的scss样式表的实现</font><font style="vertical-align: inherit;">。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">使用</font><a href="http://medialize.github.io/playground.sass.js/"><font style="vertical-align: inherit;">交互式游乐场</font></a><font style="vertical-align: inherit;">尝试sass.js</font></font><a href="http://medialize.github.io/playground.sass.js/"><font style="vertical-align: inherit;"></font></a></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
