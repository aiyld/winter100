---
layout: question
title:  如何在Node.js的console.log（）中获得完整的对象，而不是“ \[Object\]”？
date:   2020-03-10T04:11:40.000Z
description: 使用进行调试时console.log()，如何获取完整的对象？const myObject = {   "a" "a",   "b" {    ...
img: 
author: GreenSamA
category: question
answer: 10
tags: JavaScript
topic: JavaScript
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">使用进行调试时</font></font><code>console.log()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，如何获取完整的对象？</font></font></p>

<pre><code>const myObject = {<font></font>
   "a":"a",<font></font>
   "b":{<font></font>
      "c":"c",<font></font>
      "d":{<font></font>
         "e":"e",<font></font>
         "f":{<font></font>
            "g":"g",<font></font>
            "h":{<font></font>
               "i":"i"<font></font>
            }<font></font>
         }<font></font>
      }<font></font>
   }<font></font>
};    <font></font>
console.log(myObject);<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">输出：</font></font></p>

<pre><code>{ a: 'a', b: { c: 'c', d: { e: 'e', f: [Object] } } }
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">但我也想看看财产的内容</font></font><code>f</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第465篇《如何在Node.js的console.log（）中获得完整的对象，而不是“ \[Object\]”？》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">小卤蛋宝儿</span>
            <span class="discuss-time">2020.03.10</span>
          </div>
          <div class="discuss-comment"><h1><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">JSON.stringify（）</font></font></h1>

<pre><code>let myVar = {a: {b: {c: 1}}};<font></font>
console.log(JSON.stringify( myVar, null, 4 ))<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">非常适合深度检查数据对象。</font><font style="vertical-align: inherit;">这种方法适用于嵌套数组和带有数组的嵌套对象。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">猪猪卡卡西西里</span>
            <span class="discuss-time">2020.03.10</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">REPL节点具有一个内置的解决方案，用于覆盖对象的显示方式，请参见</font></font><a href="https://nodejs.org/dist/latest-v5.x/docs/api/repl.html#repl_customizing_object_displays_in_the_repl" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">此处</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p>

<blockquote>
  <p><font style="vertical-align: inherit;"></font><code>util.inspect()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在打印值时</font><font style="vertical-align: inherit;">，REPL模块内部使用</font><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">但是，</font></font><code>util.inspect</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">将调用委托给对象的</font></font><code>inspect()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">
  函数（如果有）。</font></font></p>
</blockquote></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">前端Pro</span>
            <span class="discuss-time">2020.03.10</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您可以简单地</font></font><code>inspect()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">向您的对象</font><font style="vertical-align: inherit;">添加一个</font><font style="vertical-align: inherit;">方法，</font><font style="vertical-align: inherit;">该</font><font style="vertical-align: inherit;">方法将覆盖</font></font><code>console.log</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">消息</font><font style="vertical-align: inherit;">中对象的表示形式</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">例如：</font></font></p>

<pre><code>var myObject = {<font></font>
   "a":"a",<font></font>
   "b":{<font></font>
      "c":"c",<font></font>
      "d":{<font></font>
         "e":"e",<font></font>
         "f":{<font></font>
            "g":"g",<font></font>
            "h":{<font></font>
               "i":"i"<font></font>
            }<font></font>
         }<font></font>
      }<font></font>
   }<font></font>
};<font></font>
myObject.inspect = function(){ return JSON.stringify( this, null, ' ' ); }<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">然后，您的对象将在console.log和节点shell中按需要表示</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Eva千羽</span>
            <span class="discuss-time">2020.03.10</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">检查对象的一种好方法是在</font><strong><font style="vertical-align: inherit;">Chrome DevTools for Node中</font></strong><font style="vertical-align: inherit;">使用node </font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">--inspect</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">选项</font><font style="vertical-align: inherit;">。</font></font><strong><font style="vertical-align: inherit;"></font></strong><font style="vertical-align: inherit;"></font></p>

<pre><code>node.exe --inspect www.js
</code></pre>

<p><font style="vertical-align: inherit;"></font><code>chrome://inspect/#devices</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在chrome中</font><font style="vertical-align: inherit;">打开</font><font style="vertical-align: inherit;">，然后点击</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">打开Node专用的DevTools</font></font></strong></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">现在，每个检查到的对象都可以在检查器中使用，就像在chrome中运行的常规JS一样。 </font></font></p>

<p><a href="https://i.stack.imgur.com/cBoMu.jpg" rel="noreferrer"><img src="https://i.stack.imgur.com/cBoMu.jpg" alt="在此处输入图片说明"></a></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">无需重新打开检查器，它会在节点启动或重新启动后立即自动连接到节点。</font><font style="vertical-align: inherit;">无论</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">--inspect</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">并</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">为节点的Chrome DevTools</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">可能无法在旧版本的节点和Chrome浏览器使用。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">JinJin米亚</span>
            <span class="discuss-time">2020.03.10</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">你也可以</font></font></p>

<pre><code>console.log(JSON.stringify(myObject, null, 3));
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">米亚番长</span>
            <span class="discuss-time">2020.03.10</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这两种用法都可以应用</font></font></p>

<pre><code>// more compact and colour can be applied (better for process managers logging)<font></font>
<font></font>
console.dir(queryArgs, { depth: null, colors: true });<font></font>
<font></font>
// clear list of actual values<font></font>
<font></font>
console.log(JSON.stringify(queryArgs, undefined, 2));<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Stafan神乐</span>
            <span class="discuss-time">2020.03.10</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">也许</font></font><code>console.dir</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">就是您所需要的。</font></font></p>

<p><a href="http://nodejs.org/api/console.html#console_console_dir_obj"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">http://nodejs.org/api/console.html#console_console_dir_obj</font></font></a></p>

<blockquote>
  <p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在obj上使用util.inspect并将结果字符串输出到stdout。</font></font></p>
</blockquote>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果需要更多控制，请使用util选项。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">飞云卡卡西</span>
            <span class="discuss-time">2020.03.10</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">尝试这个：</font></font></p>

<pre><code>console.dir(myObject,{depth:null})
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">泡芙阿飞斯丁</span>
            <span class="discuss-time">2020.03.10</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">从Node.js 6.4.0开始，可以使用以下方法优雅地解决此问题</font></font><a href="https://nodejs.org/api/util.html#util_util_inspect_defaultoptions" rel="noreferrer"><code>util.inspect.defaultOptions</code></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">：</font></font></p>

<pre><code>require("util").inspect.defaultOptions.depth = null;<font></font>
console.log(myObject);<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">樱L</span>
            <span class="discuss-time">2020.03.10</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您可以使用</font></font><code>JSON.stringify</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，获得一些不错的缩进以及可能更容易记住的语法。</font></font></p>

<pre><code>console.log(JSON.stringify(myObject, null, 4));
</code></pre>

<hr>

<pre><code>{<font></font>
    "a": "a",<font></font>
    "b": {<font></font>
        "c": "c",<font></font>
        "d": {<font></font>
            "e": "e",<font></font>
            "f": {<font></font>
                "g": "g",<font></font>
                "h": {<font></font>
                    "i": "i"<font></font>
                }<font></font>
            }<font></font>
        }<font></font>
    }<font></font>
}<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">第三个参数设置缩进级别，因此您可以根据需要进行调整。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果需要，请在此处提供更多详细信息：</font></font></p>

<p><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/stringify"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/JSON/stringify</font></font></a></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
