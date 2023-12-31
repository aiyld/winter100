---
layout: question
title:  如何对需要其他模块的Node.js模块进行单元测试，以及如何模拟全局require函数？
date:   2020-03-24T11:10:39.000Z
description: This is a trivial example that illustrates the crux of my problem var inner...
img: 
author: 神乐
category: question
answer: 3
tags: JavaScript Node.js
topic: Node.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p>This is a trivial example that illustrates the crux of my problem:</p>

<pre><code>var innerLib = require('./path/to/innerLib');<font></font>
<font></font>
function underTest() {<font></font>
    return innerLib.doComplexStuff();<font></font>
}<font></font>
<font></font>
module.exports = underTest;<font></font>
</code></pre>

<p>I am trying to write a unit test for this code. How can I mock out the requirement for the <code>innerLib</code> without mocking out the <code>require</code> function entirely?</p>

<p>So this is me trying to mock out the global <code>require</code> and finding out that it won’t work even to do that:</p>

<pre><code>var path = require('path'),<font></font>
    vm = require('vm'),<font></font>
    fs = require('fs'),<font></font>
    indexPath = path.join(__dirname, './underTest');<font></font>
<font></font>
var globalRequire = require;<font></font>
<font></font>
require = function(name) {<font></font>
    console.log('require: ' + name);<font></font>
    switch(name) {<font></font>
        case 'connect':<font></font>
        case indexPath:<font></font>
            return globalRequire(name);<font></font>
            break;<font></font>
    }<font></font>
};<font></font>
</code></pre>

<p>The problem is that the <code>require</code> function inside the <code>underTest.js</code> file has actually not been mocked out. It still points to the global <code>require</code> function. So it seems that I can only mock out the <code>require</code> function within the same file I’m doing the mocking in. If I use the global <code>require</code> to include anything, even after I’ve overridden the local copy, the files being required will still have the global <code>require</code> reference.</p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第3710篇《如何对需要其他模块的Node.js模块进行单元测试，以及如何模拟全局require函数？》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">小小</span>
            <span class="discuss-time">2020.03.24</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果您曾经使用过jest，那么您可能对jest的模拟功能很熟悉。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">使用“ jest.mock（...）”，您可以简单地在代码中的某处的需求语句中指定将出现的字符串，并且每当需要使用该字符串的模块时，都将返回一个模拟对象。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">例如 </font></font></p>

<pre><code>jest.mock("firebase-admin", () =&gt; {<font></font>
    const a = require("mocked-version-of-firebase-admin");<font></font>
    a.someAdditionalMockedMethod = () =&gt; {}<font></font>
    return a;<font></font>
})<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">会用您从该“工厂”功能返回的对象完全替换“ firebase-admin”的所有导入/要求。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">好吧，您可以在使用jest时执行此操作，因为jest会在它运行的每个模块周围创建一个运行时，并将“挂钩”版本的require注入到模块中，但是如果没有jest，您将无法执行此操作。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我试图通过</font></font><a href="https://www.npmjs.com/package/mock-require" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">模拟需求</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">来实现这一点，</font><font style="vertical-align: inherit;">但对我而言，它不适用于源代码中的嵌套级别。</font><font style="vertical-align: inherit;">看看github上的以下问题：</font></font><a href="https://github.com/boblauer/mock-require/issues/14" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">并非总是用Mocha调用mock-require</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">为了解决这个问题，我创建了两个npm模块，您可以使用它们来实现所需的功能。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您需要一个babel插件和一个模块模拟程序。</font></font></p>

<ul>
<li><a href="https://www.npmjs.com/package/babel-plugin-mock-require" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">babel-plugin-mock-require</font></font></a></li>
<li><a href="https://www.npmjs.com/package/jestlike-mock" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">玩笑</font></font></a></li>
</ul>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在您的.babelrc中，使用带有以下选项的babel-plugin-mock-require插件：</font></font></p>

<pre><code>...<font></font>
"plugins": [<font></font>
        ["babel-plugin-mock-require", { "moduleMocker": "jestlike-mock" }],<font></font>
        ...<font></font>
]<font></font>
...<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">并在测试文件中使用jestlike-mock模块，如下所示：</font></font></p>

<pre><code>import {jestMocker} from "jestlike-mock";<font></font>
...<font></font>
jestMocker.mock("firebase-admin", () =&gt; {<font></font>
            const firebase = new (require("firebase-mock").MockFirebaseSdk)();<font></font>
            ...<font></font>
            return firebase;<font></font>
});<font></font>
...<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">该</font></font><code>jestlike-mock</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">模块仍然非常初级，并且没有很多文档，但是也没有太多代码。</font><font style="vertical-align: inherit;">我感谢任何PR提供了更完整的功能集。</font><font style="vertical-align: inherit;">目标是重新创建整个“ jest.mock”功能。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">为了了解jest如何实现，可以在“ jest-runtime”包中查找代码。</font><font style="vertical-align: inherit;">例如，</font><font style="vertical-align: inherit;">请参见</font></font><a href="https://github.com/facebook/jest/blob/master/packages/jest-runtime/src/index.js#L734" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">https://github.com/facebook/jest/blob/master/packages/jest-runtime/src/index.js#L734</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，此处它们生成模块的“自动模拟”。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">希望能有所帮助;）</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">小胖Mandy</span>
            <span class="discuss-time">2020.03.24</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">你现在可以！</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我发布了</font></font><a href="https://npmjs.org/package/proxyquire"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">proxyquire</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，它将在测试模块时覆盖模块内部的全局需求。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这意味着您无需</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">更改代码</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">即可为所需模块注入模拟。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Proxyquire有一个非常简单的api，它可以解析您要测试的模块，并通过一个简单的步骤传递其所需模块的模拟/存根。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">@Raynos是正确的，传统上，您必须诉诸不太理想的解决方案才能实现该目标或进行自下而上的开发</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这就是我创建proxyquire的主要原因-允许自上而下的测试驱动开发而无任何麻烦。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">请查看文档和示例，以判断它是否适合您的需求。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">古一</span>
            <span class="discuss-time">2020.03.24</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我使用</font></font><a href="https://github.com/boblauer/mock-require" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">模拟需求</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">确保</font></font><code>require</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在测试模块</font><font style="vertical-align: inherit;">之前定义</font><font style="vertical-align: inherit;">了模拟。</font></font></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
