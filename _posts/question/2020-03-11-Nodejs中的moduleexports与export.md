---
layout: question
title:  Node.js中的module.exports与export
date:   2020-03-11T04:10:02.000Z
description: 我在Node.js模块中找到了以下合同：module.exports = exports = nano = function database_mod...
img: 
author: Tony樱番长
category: question
answer: 11
tags: JavaScript
topic: JavaScript
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我在Node.js模块中找到了以下合同：</font></font></p>

<pre><code>module.exports = exports = nano = function database_module(cfg) {...}
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我不知道什么之间的不同</font></font><code>module.exports</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">和</font></font><code>exports</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">为什么都被用在这里。</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第644篇《Node.js中的module.exports与export》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">小卤蛋卡卡西A</span>
            <span class="discuss-time">2020.03.11</span>
          </div>
          <div class="discuss-comment"><p><code>module.exports</code><font style="vertical-align: inherit;"></font><code>exports</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在评估模块之前</font><font style="vertical-align: inherit;">，</font><font style="vertical-align: inherit;">它们都指向同一对象。</font></font></p>

<p><font style="vertical-align: inherit;"></font><code>module.exports</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">  当您的模块在另一个模块中使用using </font></font><code>require</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">语句</font><font style="vertical-align: inherit;">使用时，</font><font style="vertical-align: inherit;">添加到</font><font style="vertical-align: inherit;">对象的</font><font style="vertical-align: inherit;">任何属性</font><font style="vertical-align: inherit;">都将可用</font><font style="vertical-align: inherit;">。</font></font><code>exports</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">是可用于同一事物的快捷方式。</font><font style="vertical-align: inherit;">例如：</font></font></p>

<pre class="lang-js prettyprint-override"><code>module.exports.add = (a, b) =&gt; a+b
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">相当于写：</font></font></p>

<pre class="lang-js prettyprint-override"><code>exports.add = (a, b) =&gt; a+b
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">因此，只要您不为</font></font><code>exports</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">变量</font><font style="vertical-align: inherit;">分配新值就可以</font><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">当您执行以下操作时：</font></font></p>

<pre class="lang-js prettyprint-override"><code>exports = (a, b) =&gt; a+b 
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">由于您正在为其分配新值，</font></font><code>exports</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">因此不再引用导出的对象，因此将保留在模块本地。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果您打算为分配一个新值，</font></font><code>module.exports</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">而不是向可用的初始对象添加新属性，则可能应该考虑执行以下操作：</font></font></p>

<pre class="lang-js prettyprint-override"><code>module.exports = exports = (a, b) =&gt; a+b
</code></pre>

<p><a href="https://nodejs.org/api/modules.html#modules_exports" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Node.js网站对此有很好的解释。</font></font></a></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">小小Green</span>
            <span class="discuss-time">2020.03.11</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">1.exports-&gt;用作单例实用程序</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">
2. module- </font><font style="vertical-align: inherit;">exports-&gt; </font><font style="vertical-align: inherit;">用作逻辑对象，如service，model等</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">LEYAItachi</span>
            <span class="discuss-time">2020.03.11</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">“如果您希望模块导出的根是一个函数（例如构造函数），或者想一次导出一个完整的对象而不是一次构建一个属性，则将其分配给module.exports而不是出口。” </font><font style="vertical-align: inherit;">- </font></font><a href="http://nodejs.org/api/modules.html" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">http://nodejs.org/api/modules.html</font></font></a></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">神奇古一</span>
            <span class="discuss-time">2020.03.11</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这展示了如何</font></font><code>require()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">以最简单的形式工作（摘自</font></font><a href="http://eloquentjavascript.net/" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Eloquent JavaScript）</font></font></a></p>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">问题</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> 
模块无法直接导出导出对象以外的值，例如函数。</font><font style="vertical-align: inherit;">例如，一个模块可能只想导出其定义的对象类型的构造函数。</font><font style="vertical-align: inherit;">目前，它无法执行此操作，因为require始终将</font></font><code>exports</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">其创建</font><font style="vertical-align: inherit;">的</font><font style="vertical-align: inherit;">对象用作导出值。</font></font></p>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">解决方案</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> 
为模块提供另一个变量，</font></font><code>module</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">该</font><font style="vertical-align: inherit;">变量</font><font style="vertical-align: inherit;">是具有属性的对象</font></font><code>exports</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">此属性最初指向由require创建的空对象，但可以用另一个值覆盖以导出其他内容。</font></font></p>

<pre><code>function require(name) {<font></font>
  if (name in require.cache)<font></font>
    return require.cache[name];<font></font>
  var code = new Function("exports, module", readFile(name));<font></font>
  var exports = {}, module = {exports: exports};<font></font>
  code(exports, module);<font></font>
  require.cache[name] = module.exports;<font></font>
  return module.exports;<font></font>
}<font></font>
require.cache = Object.create(null);<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">凯樱</span>
            <span class="discuss-time">2020.03.11</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">来自</font></font><a href="https://nodejs.org/docs/latest/api/modules.html" rel="nofollow noreferrer" title="文件资料"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">文档</font></font></a></p>

<blockquote>
  <p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">导出变量在模块的文件级范围内可用，并在评估模块之前为其指定了module.exports的值。</font></font></p>
  
  <p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">它允许使用快捷方式，以便module.exports.f = ...可以更简洁地编写为exports.f =...。</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">但是，请注意，与任何变量一样，如果将新值分配给exports，不再绑定到module.exports：</font></font></p>
</blockquote>

<p><em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">它只是指向module.exports的变量。</font></font></em> </p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Sam飞云</span>
            <span class="discuss-time">2020.03.11</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我发现此链接对于回答上述问题很有用。</font></font></p>

<p><a href="http://timnew.me/blog/2012/04/20/exports-vs-module-exports-in-node-js/" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">http://timnew.me/blog/2012/04/20/exports-vs-module-exports-in-node-js/</font></font></a></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">添加到其他帖子节点中的模块系统执行    </font></font></p>

<pre><code>var exports = module.exports 
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在执行代码之前。</font><font style="vertical-align: inherit;">因此，当您要exports = foo时，可能要执行module.exports = exports = foo，但使用exports.foo = foo应该没问题。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">卡卡西逆天十三</span>
            <span class="discuss-time">2020.03.11</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这是结果 </font></font></p>

<pre><code>console.log("module:");<font></font>
console.log(module);<font></font>
<font></font>
console.log("exports:");<font></font>
console.log(exports);<font></font>
<font></font>
console.log("module.exports:");<font></font>
console.log(module.exports);<font></font>
</code></pre>

<p><a href="https://i.stack.imgur.com/0cy3Q.png" rel="nofollow noreferrer"><img src="https://i.stack.imgur.com/0cy3Q.png" alt="在此处输入图片说明"></a></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">也：</font></font></p>

<pre><code>if(module.exports === exports){<font></font>
    console.log("YES");<font></font>
}else{<font></font>
    console.log("NO");<font></font>
}<font></font>
<font></font>
//YES<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">注意：CommonJS规范仅允许使用exports变量来公开公共成员。</font><font style="vertical-align: inherit;">因此，命名的导出模式是唯一与CommonJS规范真正兼容的模式。</font><font style="vertical-align: inherit;">module.exports的使用是Node.js提供的扩展，以支持更广泛的模块定义模式。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">番长樱梅</span>
            <span class="discuss-time">2020.03.11</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这是</font><strong><font style="vertical-align: inherit;">Manning</font></strong><font style="vertical-align: inherit;">出版的</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">操作</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">手册</font><font style="vertical-align: inherit;">中有关</font><strong><font style="vertical-align: inherit;">node.js中的</font></strong><font style="vertical-align: inherit;">节点模块的良好描述</font><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">
最终在您的应用程序中导出的是</font><i><font style="vertical-align: inherit;">module.exports。</font></i><i><font style="vertical-align: inherit;">可以将exports</font></i><font style="vertical-align: inherit;">设置为对</font><i><font style="vertical-align: inherit;">module.exports</font></i><font style="vertical-align: inherit;">的全局引用</font><font style="vertical-align: inherit;">，该模块最初定义为可以向其添加属性的空对象。</font><font style="vertical-align: inherit;">所以</font><i><font style="vertical-align: inherit;">exports.myFunc</font></i><font style="vertical-align: inherit;">是刚刚速记</font><i><font style="vertical-align: inherit;">module.exports.myFunc</font></i><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">
其结果是，如果</font><i><font style="vertical-align: inherit;">出口</font></i><font style="vertical-align: inherit;">被设置为别的，它打破了</font><b><font style="vertical-align: inherit;">基准</font></b><font style="vertical-align: inherit;">之间
 </font><i><font style="vertical-align: inherit;">module.exports</font></i><font style="vertical-align: inherit;">和</font><i><font style="vertical-align: inherit;">出口</font></i><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">因为</font><i><font style="vertical-align: inherit;">module.exports</font></i></font><strong><font style="vertical-align: inherit;"></font></strong><font style="vertical-align: inherit;"></font><br><font style="vertical-align: inherit;"></font><i><font style="vertical-align: inherit;"></font><br><font style="vertical-align: inherit;"></font></i><font style="vertical-align: inherit;"></font><i><font style="vertical-align: inherit;"></font></i><font style="vertical-align: inherit;"></font><i><font style="vertical-align: inherit;"></font></i><font style="vertical-align: inherit;"></font><i><font style="vertical-align: inherit;"></font></i><font style="vertical-align: inherit;"></font><br><br><font style="vertical-align: inherit;"></font><i><font style="vertical-align: inherit;"></font></i><font style="vertical-align: inherit;"></font><b><font style="vertical-align: inherit;"></font></b><font style="vertical-align: inherit;"></font><i><font style="vertical-align: inherit;"></font></i><font style="vertical-align: inherit;"></font><i><font style="vertical-align: inherit;"></font></i><font style="vertical-align: inherit;"></font><i><font style="vertical-align: inherit;"></font></i><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">是真正要导出的内容，</font></font><i><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">导出</font></font></i><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">将不再按预期方式工作-它不再引用</font></font><i><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">.exports模块</font></font></i><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">如果要维护该链接，可以使</font></font><i><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">module.exports</font></font></i><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">再次</font><font style="vertical-align: inherit;">
引用</font></font><i><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">导出</font></font></i><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，如下所示：</font></font></p>

<pre><code>module.exports = exports = db;
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">番长西里神无</span>
            <span class="discuss-time">2020.03.11</span>
          </div>
          <div class="discuss-comment"><h2><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">JavaScript通过引用的副本传递对象</font></font></h2>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在JavaScript中通过引用传递对象的方式有微妙的区别。</font></font></p>

<p><code>exports</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">和</font></font><code>module.exports</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">都指向同一个对象。</font></font><code>exports</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">是变量，</font></font><code>module.exports</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">是模块对象的属性。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">说我写这样的东西：</font></font></p>

<pre><code>exports = {a:1};<font></font>
module.exports = {b:12};<font></font>
</code></pre>

<p><code>exports</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">而</font></font><code>module.exports</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">现在指向不同的对象。</font><font style="vertical-align: inherit;">修改导出不再修改module.exports。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">导入功能检查</font></font><code>module.exports</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">时得到</font></font><code>{b:12}</code></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">飞云前端西门</span>
            <span class="discuss-time">2020.03.11</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">最初，</font></font><code>module.exports=exports</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">和</font></font><code>require</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">函数会返回所</font></font><code>module.exports</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">引用</font><font style="vertical-align: inherit;">的对象</font><font style="vertical-align: inherit;">。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果我们</font><font style="vertical-align: inherit;">向对象</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">添加属性</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，例如</font></font><code>exports.a=1</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，则module.exports和export </font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">仍</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">引用同一对象。</font><font style="vertical-align: inherit;">因此，如果我们调用require并将模块分配给变量，则该变量具有a属性，其值为1；</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">但是，如果我们</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">覆盖</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">其中的一个，例如，</font></font><code>exports=function(){}</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">则它们现在</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">有所不同</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">：export指向一个新对象，而module.exports指向原始对象。</font><font style="vertical-align: inherit;">如果我们需要该文件，它将不会返回新对象，因为module.exports没有引用新对象。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">对我而言，我将继续添加新属性，或将它们都覆盖到新对象中。</font><font style="vertical-align: inherit;">仅仅覆盖一个是不对的。</font><font style="vertical-align: inherit;">并记住那</font></font><code>module.exports</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">才是真正的老板。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">神无</span>
            <span class="discuss-time">2020.03.11</span>
          </div>
          <div class="discuss-comment"><p><code>exports</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">并且</font></font><code>module.exports</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">是相同的，除非你重新分配</font></font><code>exports</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">你的模块中。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">考虑这一点的最简单方法是认为此行隐式位于每个模块的顶部。</font></font></p>

<pre><code>var exports = module.exports = {};
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果您在模块中重新分配</font></font><code>exports</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，则在模块中重新分配它，而不再等于</font></font><code>module.exports</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">这就是为什么如果要导出功能，必须执行以下操作的原因：</font></font></p>

<pre><code>module.exports = function() { ... }
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果您只是将您的分配</font></font><code>function() { ... }</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">给</font></font><code>exports</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，那么您将被重新分配</font></font><code>exports</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">以不再指向</font></font><code>module.exports</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果不想</font></font><code>module.exports</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">每次都</font><font style="vertical-align: inherit;">引用函数</font><font style="vertical-align: inherit;">，可以执行以下操作：</font></font></p>

<pre><code>module.exports = exports = function() { ... }
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">注意，这</font></font><code>module.exports</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">是最左边的参数。</font></font></p>

<p><font style="vertical-align: inherit;"></font><code>exports</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">由于没有重新分配</font><font style="vertical-align: inherit;">属性，</font><font style="vertical-align: inherit;">因此</font><font style="vertical-align: inherit;">将属性附加到的属性</font><font style="vertical-align: inherit;">是不同的。</font><font style="vertical-align: inherit;">这就是为什么这样</font></font></p>

<pre><code>exports.foo = function() { ... }
</code></pre></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
