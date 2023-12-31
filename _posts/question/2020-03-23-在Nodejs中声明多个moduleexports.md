---
layout: question
title:  在Node.js中声明多个module.exports
date:   2020-03-23T02:37:15.000Z
description: 我要实现的目标是创建一个包含多个功能的模块。module.js：module.exports = function(firstParam) { c...
img: 
author: Stafan樱
category: question
answer: 7
tags: node.js Node.js
topic: Node.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我要实现的目标是创建一个包含多个功能的模块。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">module.js：</font></font></p>

<pre><code>module.exports = function(firstParam) { console.log("You did it"); },<font></font>
module.exports = function(secondParam) { console.log("Yes you did it"); }, <font></font>
// This may contain more functions<font></font>
</code></pre>

<p><code>main.js:</code></p>

<pre><code>var foo = require('module.js')(firstParam);<font></font>
var bar = require('module.js')(secondParam);<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我的问题是，这</font></font><code>firstParam</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">是一个对象类型，而这</font></font><code>secondParam</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">是一个URL字符串，但是当我遇到</font><font style="vertical-align: inherit;">该问题</font><font style="vertical-align: inherit;">时，它总是抱怨该类型是错误的。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在这种情况下，如何声明多个module.exports？</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第2660篇《在Node.js中声明多个module.exports》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">西门卡卡西</span>
            <span class="discuss-time">2020.03.23</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您也可以使用这种方法</font></font></p>

<pre><code>module.exports.func1 = ...<font></font>
module.exports.func2 = ...<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">要么</font></font></p>

<pre><code>exports.func1 = ...<font></font>
exports.func2 = ...<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Mandy村村</span>
            <span class="discuss-time">2020.03.23</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果在模块文件而不是简单对象中声明一个类 </font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">文件：UserModule.js</font></font></p>

<pre><code>//User Module    <font></font>
class User {<font></font>
  constructor(){<font></font>
    //enter code here<font></font>
  }<font></font>
  create(params){<font></font>
    //enter code here<font></font>
  }<font></font>
}<font></font>
class UserInfo {<font></font>
  constructor(){<font></font>
    //enter code here<font></font>
  }<font></font>
  getUser(userId){<font></font>
    //enter code here<font></font>
    return user;<font></font>
  }<font></font>
}<font></font>
<font></font>
// export multi<font></font>
module.exports = [User, UserInfo];<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">主文件：index.js</font></font></p>

<pre><code>// import module like<font></font>
const { User, UserInfo } = require("./path/to/UserModule");<font></font>
User.create(params);<font></font>
UserInfo.getUser(userId);<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">卡卡西</span>
            <span class="discuss-time">2020.03.23</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">用这个 </font></font></p>

<pre><code>(function()<font></font>
{<font></font>
  var exports = module.exports = {};<font></font>
  exports.yourMethod =  function (success)<font></font>
  {<font></font>
<font></font>
  }<font></font>
  exports.yourMethod2 =  function (success)<font></font>
  {<font></font>
<font></font>
  }<font></font>
<font></font>
<font></font>
})();<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">达蒙</span>
            <span class="discuss-time">2020.03.23</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">你也可以像这样导出它 </font></font></p>

<pre><code>const func1 = function (){some code here}<font></font>
const func2 = function (){some code here}<font></font>
exports.func1 = func1;<font></font>
exports.func2 = func2;<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">或像这样的匿名函数</font></font></p>

<pre><code>    const func1 = ()=&gt;{some code here}<font></font>
    const func2 = ()=&gt;{some code here}<font></font>
    exports.func1 = func1;<font></font>
    exports.func2 = func2;<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Jim西门</span>
            <span class="discuss-time">2020.03.23</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您可以编写一个在其他功能之间手动委派的功能：</font></font></p>

<pre><code>module.exports = function(arg) {<font></font>
    if(arg instanceof String) {<font></font>
         return doStringThing.apply(this, arguments);<font></font>
    }else{<font></font>
         return doObjectThing.apply(this, arguments);<font></font>
    }<font></font>
};<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">小胖十三</span>
            <span class="discuss-time">2020.03.23</span>
          </div>
          <div class="discuss-comment"><p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">两种类型的模块导入和导出。</font></font></strong></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">类型1（module.js）：</font></font></p>

<pre><code>// module like a webpack config<font></font>
const development = {<font></font>
  // ...<font></font>
};<font></font>
const production = {<font></font>
  // ...<font></font>
};<font></font>
<font></font>
// export multi<font></font>
module.exports = [development, production];<font></font>
// export single<font></font>
// module.exports = development;<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">类型1（main.js）：</font></font></p>

<pre><code>// import module like a webpack config<font></font>
const { development, production } = require("./path/to/module");<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">类型2（module.js）：</font></font></p>

<pre><code>// module function no param<font></font>
const module1 = () =&gt; {<font></font>
  // ...<font></font>
};<font></font>
// module function with param<font></font>
const module2 = (param1, param2) =&gt; {<font></font>
  // ...<font></font>
};<font></font>
<font></font>
// export module<font></font>
module.exports = {<font></font>
  module1,<font></font>
  module2<font></font>
}<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">类型2（main.js）：</font></font></p>

<pre><code>// import module function<font></font>
const { module1, module2 } = require("./path/to/module");<font></font>
</code></pre>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如何使用导入模块？</font></font></strong></p>

<pre><code>const importModule = {<font></font>
  ...development,<font></font>
  // ...production,<font></font>
  // ...module1,<font></font>
  ...module2("param1", "param2"),<font></font>
};<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">村村</span>
            <span class="discuss-time">2020.03.23</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">要导出多个功能，您可以像这样列出它们：</font></font></p>

<pre><code>module.exports = {<font></font>
   function1,<font></font>
   function2,<font></font>
   function3<font></font>
}<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">然后在另一个文件中访问它们：</font></font></p>

<pre><code>var myFunctions = require("./lib/file.js")
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">然后，您可以通过调用以下命令来调用每个函数：</font></font></p>

<pre><code>myFunctions.function1<font></font>
myFunctions.function2<font></font>
myFunctions.function3<font></font>
</code></pre></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
