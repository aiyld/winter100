---
layout: question
title:  Node.js module.exports的用途是什么，如何使用它？
date:   2020-03-09T12:59:52.000Z
description: Node.js module.exports的用途是什么，如何使用它？我似乎找不到任何相关信息，但是正如我在源代码中经常看到的那样，它似乎是Node....
img: 
author: 小小Eva
category: question
answer: 5
tags: JavaScript
topic: JavaScript
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Node.js module.exports的用途是什么，如何使用它？</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我似乎找不到任何相关信息，但是正如我在源代码中经常看到的那样，它似乎是Node.js的重要组成部分。  </font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">根据</font></font><a href="http://nodejs.org/docs/v0.4.2/api/globals.html#module" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Node.js文档</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">：</font></font></p>

<blockquote>
  <p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">模组</font></font></strong> </p>
  
  <p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">对当前的引用
   </font></font><code>module</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">特别</font></font><code>module.exports</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">
  是与导出对象相同。</font><font style="vertical-align: inherit;">请参阅
   </font></font><code>src/node.js</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">以获取更多信息。</font></font></p>
</blockquote>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">但这并没有真正的帮助。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">究竟是</font></font><code>module.exports</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">做什么的，一个简单的例子是什么？</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第265篇《Node.js module.exports的用途是什么，如何使用它？》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">斯丁阳光</span>
            <span class="discuss-time">2020.03.09</span>
          </div>
          <div class="discuss-comment"><pre><code>let test = function() {<font></font>
    return "Hello world"<font></font>
};<font></font>
exports.test = test;<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">理查德飞云</span>
            <span class="discuss-time">2020.03.09</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">模块将相关代码封装到单个代码单元中。</font><font style="vertical-align: inherit;">创建模块时，这可以解释为将所有相关功能移动到文件中。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">假设有一个文件Hello.js，其中包含两个函数</font></font></p>

<pre><code>sayHelloInEnglish = function() {<font></font>
  return "Hello";<font></font>
};<font></font>
sayHelloInSpanish = function() {<font></font>
  return "Hola";<font></font>
};<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我们仅在代码的效用超过一个调用时才编写函数。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">假设我们想将该功能的实用性增加到另一个文件，例如World.js，在这种情况下，导出文件就可以通过module.exports获取。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您可以通过下面给出的代码导出两个函数</font></font></p>

<pre><code>var anyVariable={<font></font>
 sayHelloInEnglish = function() {<font></font>
      return "Hello";<font></font>
    };<font></font>
  sayHelloInSpanish = function() {<font></font>
      return "Hola";<font></font>
    }; <font></font>
}<font></font>
module.export=anyVariable;<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">现在，您只需要在World.js中输入文件名即可使用这些功能</font></font></p>

<pre><code>var world= require("./hello.js");
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">神无</span>
            <span class="discuss-time">2020.03.09</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">将程序代码划分为多个文件时，</font></font><code>module.exports</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">用于将变量和函数发布给模块的使用者。</font></font><code>require()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">源文件中</font><font style="vertical-align: inherit;">的</font><font style="vertical-align: inherit;">调用将替换为</font></font><code>module.exports</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">从模块中加载的</font><font style="vertical-align: inherit;">相应文件</font><font style="vertical-align: inherit;">。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在编写模块时记住</font></font></p>

<ul>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">模块加载被缓存，只有初始调用评估JavaScript。</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">可以在模块内使用局部变量和函数，而不需要导出所有内容。</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">该</font></font><code>module.exports</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">对象也可用作</font></font><code>exports</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">速记。</font><font style="vertical-align: inherit;">但是，当返回唯一函数时，请始终使用</font></font><code>module.exports</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></li>
</ul>

<blockquote>
  <p><img src="https://bytearcher.com/articles/writing_modules/diagram-require-call-replaced-by-module-exports-400.png" alt="模块出口图"></p>
</blockquote>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">根据：</font></font><a href="http://bytearcher.com/articles/writing_modules/" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">“模块第2部分-编写模块”</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">前端飞云</span>
            <span class="discuss-time">2020.03.09</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果您将对新对象的引用分配给</font></font><code>exports</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">和/或，</font><font style="vertical-align: inherit;">则必须注意一些事项</font></font><code>modules.exports</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">：</font></font></p>

<h3><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">1.以前附加到原始属性的所有属性/方法，</font></font><code>exports</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">或者</font></font><code>module.exports</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">当然会丢失，因为导出的对象现在将引用另一个新</font><font style="vertical-align: inherit;">属性/方法</font></font></h3>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这很明显，但是</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果您在现有模块的开头添加导出的方法，请确保本机导出的对象在末尾没有引用另一个对象</font></font></strong></p>

<pre><code>exports.method1 = function () {}; // exposed to the original exported object<font></font>
exports.method2 = function () {}; // exposed to the original exported object<font></font>
<font></font>
module.exports.method3 = function () {}; // exposed with method1 &amp; method2<font></font>
<font></font>
var otherAPI = {<font></font>
    // some properties and/or methods<font></font>
}<font></font>
<font></font>
exports = otherAPI; // replace the original API (works also with module.exports)<font></font>
</code></pre>

<h3><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">2.如果一个</font></font><code>exports</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">或</font></font><code>module.exports</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">引用一个新值，则它们不再引用同一对象</font></font></h3>

<pre><code>exports = function AConstructor() {}; // override the original exported object<font></font>
exports.method2 = function () {}; // exposed to the new exported object<font></font>
<font></font>
// method added to the original exports object which not exposed any more<font></font>
module.exports.method3 = function () {}; <font></font>
</code></pre>

<h3><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">3.棘手的结果。</font><font style="vertical-align: inherit;">如果您同时更改对</font></font><code>exports</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">和</font><font style="vertical-align: inherit;">的引用</font></font><code>module.exports</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，则很难说公开了哪个API（看起来很成功</font></font><code>module.exports</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">）。</font></font></h3>

<pre><code>// override the original exported object<font></font>
module.exports = function AConstructor() {};<font></font>
<font></font>
// try to override the original exported object<font></font>
// but module.exports will be exposed instead<font></font>
exports = function AnotherConstructor() {}; <font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Mandy古一</span>
            <span class="discuss-time">2020.03.09</span>
          </div>
          <div class="discuss-comment"><p>the module.exports property or the exports object allows a module to select what should be shared with the application</p>

<p><img src="https://i.stack.imgur.com/vI2Hm.jpg" alt="在此处输入图片说明"></p>

<p>I have a video on module_export available <a href="https://www.youtube.com/watch?v=qLc29euevzc&amp;index=14&amp;list=PLrUFyg1unBb88J0r7gvJ1T01WN_pp83Lz" rel="noreferrer">here</a></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
