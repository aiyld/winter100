---
layout: question
title:  我如何在Node.js（Javascript）中等待，我需要暂停一段时间
date:   2020-03-18T07:23:56.000Z
description: I'm developing a console like script for personal needs. I need to be able to...
img: 
author: 达蒙乐
category: question
answer: 10
tags: JavaScript Node.js
topic: Node.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p>I'm developing a console like script for personal needs. I need to be able to pause for a extended amount of time, but, from my research, node.js has no way to stop as required. It’s getting hard to read users’ information after a period of time... I’ve seen some code out there, but I believe they have to have other code inside of them for them to work such as:</p>

<pre><code>setTimeout(function() {<font></font>
}, 3000);<font></font>
</code></pre>

<p>However, I need everything after this line of code to execute after the period of time.</p>

<p>For example, </p>

<pre><code>//start-of-code<font></font>
console.log('Welcome to My Console,');<font></font>
some-wait-code-here-for-ten-seconds..........<font></font>
console.log('Blah blah blah blah extra-blah');<font></font>
//endcode. <font></font>
</code></pre>

<p>I've also seen things like</p>

<pre><code>yield sleep(2000);
</code></pre>

<p>But node.js doesnt recognize this.</p>

<p>How can I achieve this extended pause?</p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第2006篇《我如何在Node.js（Javascript）中等待，我需要暂停一段时间》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">西里猿LEY</span>
            <span class="discuss-time">2020.03.18</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">阅读完该问题的答案后，我整理了一个简单的函数，如果需要，该函数也可以执行回调：</font></font></p>

<pre><code>function waitFor(ms, cb) {<font></font>
  var waitTill = new Date(new Date().getTime() + ms);<font></font>
  while(waitTill &gt; new Date()){};<font></font>
  if (cb) {<font></font>
    cb()<font></font>
  } else {<font></font>
   return true<font></font>
  }<font></font>
}<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">神乐猴子</span>
            <span class="discuss-time">2020.03.18</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">有关更多信息</font></font></p>

<pre><code>yield sleep(2000); 
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您应该检查</font></font><a href="https://github.com/yelouafi/redux-saga" rel="nofollow" title="Redux-Saga"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Redux-Saga</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">但这是特定于您将Redux选择为模型框架的（尽管绝对没有必要）。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">猪猪小卤蛋</span>
            <span class="discuss-time">2020.03.18</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">对于某些人来说，接受的答案无效，我找到了另一个答案，它对我也有效：</font></font><a href="https://stackoverflow.com/questions/1190642/how-can-i-pass-a-parameter-to-a-settimeout-callback"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如何将参数传递给setTimeout（）回调？</font></font></a></p>

<pre><code>var hello = "Hello World";<font></font>
setTimeout(alert, 1000, hello); <font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">“ hello”是要传递的参数，您可以在超时时间之后传递所有参数。</font><font style="vertical-align: inherit;">感谢@Fabio Phms的回答。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">卡卡西小哥</span>
            <span class="discuss-time">2020.03.18</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">很简单，我们将等待5秒钟，以便发生某些事件（这将由代码中其他位置的done变量设置为true表示），或者当超时到期时，我们将每100ms检查一次</font></font></p>

<pre><code>    var timeout=5000; //will wait for 5 seconds or untildone<font></font>
    var scope = this; //bind this to scope variable<font></font>
    (function() {<font></font>
        if (timeout&lt;=0 || scope.done) //timeout expired or done<font></font>
        {<font></font>
            scope.callback();//some function to call after we are done<font></font>
        }<font></font>
        else<font></font>
        {<font></font>
            setTimeout(arguments.callee,100) //call itself again until done<font></font>
            timeout -= 100;<font></font>
        }<font></font>
    })();<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">西门Sam</span>
            <span class="discuss-time">2020.03.18</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">有了ES6 support </font></font><code>Promise</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，我们可以在没有任何第三方帮助的情况下使用它们。</font></font></p>

<pre><code>const sleep = (seconds) =&gt; {<font></font>
    return new Promise((resolve, reject) =&gt; {<font></font>
        setTimeout(resolve, (seconds * 1000));<font></font>
    });<font></font>
};<font></font>
<font></font>
// We are not using `reject` anywhere, but it is good to<font></font>
// stick to standard signature.<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">然后像这样使用它：</font></font></p>

<pre><code>const waitThenDo(howLong, doWhat) =&gt; {<font></font>
    return sleep(howLong).then(doWhat);<font></font>
};<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">请注意，该</font></font><code>doWhat</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">函数将成为中的</font></font><code>resolve</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">回调</font></font><code>new Promise(...)</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">另请注意，这是异步睡眠。</font><font style="vertical-align: inherit;">它不会阻止事件循环。</font><font style="vertical-align: inherit;">如果需要阻止睡眠，请使用此库，该库可在C ++绑定的帮助下实现阻止睡眠。</font><font style="vertical-align: inherit;">（尽管很少需要像异步环境一样在Node中阻塞睡眠。）</font></font></p>

<p><a href="https://github.com/erikdubbelboer/node-sleep" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">https://github.com/erikdubbelboer/node-sleep</font></font></a></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">老丝猪猪小卤蛋</span>
            <span class="discuss-time">2020.03.18</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">由于javascript引擎（v8）根据事件队列中的事件序列运行代码，因此没有严格要求javascript在指定时间后准确触发执行。</font><font style="vertical-align: inherit;">就是说，当您设置几秒钟来稍后执行代码时，触发代码纯粹是基于事件队列中的顺序。</font><font style="vertical-align: inherit;">因此，触发代码执行可能要花费超过指定的时间。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">因此，Node.js跟着，</font></font></p>

<pre><code>process.nextTick()
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">以便稍后运行代码，而不是setTimeout（）。</font><font style="vertical-align: inherit;">例如，</font></font></p>

<pre><code>process.nextTick(function(){<font></font>
    console.log("This will be printed later");<font></font>
});<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">路易猴子Pro</span>
            <span class="discuss-time">2020.03.18</span>
          </div>
          <div class="discuss-comment"><h1><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">使用现代Java脚本实现简单优雅的睡眠功能</font></font></h1>

<pre><code>function sleep(millis) {<font></font>
    return new Promise(resolve =&gt; setTimeout(resolve, millis));<font></font>
}<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">没有依赖，没有回调地狱；</font><font style="vertical-align: inherit;">而已 ：-）</font></font></p>

<hr>

<p>Considering the example given in the question, this is how we would sleep between two console logs:</p>

<pre><code>async function main() {<font></font>
    console.log("Foo");<font></font>
    await sleep(2000);<font></font>
    console.log("Bar");<font></font>
}<font></font>
<font></font>
main();<font></font>
</code></pre>

<p>The "drawback" is that your main function now has to be <code>async</code> as well. But, considering you are already writing modern Javascript code, you are probably (or at least should be!) using <code>async</code>/<code>await</code> all over your code, so this is really not an issue. All modern browsers today <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/async_function#Browser_compatibility" rel="noreferrer">support</a> it.</p>

<p>Giving a little insight into the <code>sleep</code> function for those that are not used to <code>async/await</code> and fat arrow operators, this is the verbose way of writing it:</p>

<pre><code>function sleep(millis) {<font></font>
    return new Promise(function (resolve, reject) {<font></font>
        setTimeout(function () { resolve(); }, millis);<font></font>
    });<font></font>
}<font></font>
</code></pre>

<p>Using the fat arrow operator, though, makes it even smaller (and more elegant).</p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Pro神奇神奇</span>
            <span class="discuss-time">2020.03.18</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这是一种简单的阻止技术：</font></font></p>

<pre><code>var waitTill = new Date(new Date().getTime() + seconds * 1000);<font></font>
while(waitTill &gt; new Date()){}<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">只要您的脚本中没有其他任何事情（例如回调），</font><font style="vertical-align: inherit;">它就会</font></font><em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">阻塞</font></font></em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">但是，由于这是一个控制台脚本，所以也许正是您所需要的！</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">神无猪猪</span>
            <span class="discuss-time">2020.03.18</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">没有任何依赖关系的最短解决方案：</font></font></p>

<pre><code>await new Promise(resolve =&gt; setTimeout(resolve, 5000));
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">猴子飞云</span>
            <span class="discuss-time">2020.03.18</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">一个旧问题的新答案。</font><font style="vertical-align: inherit;">今天（</font></font><s><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">2017</font></font></s><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">年</font><s><font style="vertical-align: inherit;">1</font></s><font style="vertical-align: inherit;">月，2019 </font><s><font style="vertical-align: inherit;">年</font></s><font style="vertical-align: inherit;"> 6月）要容易得多。</font><font style="vertical-align: inherit;">您可以使用</font></font><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/async_function" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">新</font></font><code>async/await</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">语法</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">例如：</font></font></p>

<pre><code>async function init() {<font></font>
  console.log(1);<font></font>
  await sleep(1000);<font></font>
  console.log(2);<font></font>
}<font></font>
<font></font>
function sleep(ms) {<font></font>
  return new Promise((resolve) =&gt; {<font></font>
    setTimeout(resolve, ms);<font></font>
  });<font></font>
}   <font></font>
</code></pre>

<p><s>For using <code>async/await</code> out of the box without installing and plugins, you have to use node-v7 or node-v8, using the <code>--harmony</code> flag.</s></p>

<p><strong>Update June 2019:</strong> By using the latest versions of NodeJS you can use it out of the box. No need to provide command line arguments. Even Google Chrome support it today.</p>

<p><strong>More info:</strong></p>

<ul>
<li>Harmony Flag in Nodejs: <a href="https://nodejs.org/en/docs/es6/" rel="noreferrer">https://nodejs.org/en/docs/es6/</a></li>
<li>All NodeJS Version for download: <a href="https://nodejs.org/en/download/releases/" rel="noreferrer">https://nodejs.org/en/download/releases/</a></li>
</ul></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
