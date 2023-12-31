---
layout: question
title:  React.js中的setState与replaceState
date:   2020-03-12T08:28:21.000Z
description: 我是React.js库的新手，我正在浏览一些教程，发现了：this.setStatethis.replaceState给出的说明不是很清楚（...
img: 
author: 猪猪Stafan小卤蛋
category: question
answer: 3
tags: JavaScript
topic: JavaScript
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我是React.js库的新手，我正在浏览一些教程，发现了：</font></font></p>

<ul>
<li><code>this.setState</code></li>
<li><code>this.replaceState</code></li>
</ul>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">给出的说明不是很清楚（IMO）。</font></font></p>

<pre><code>setState is done to 'set' the state of a value, even if its already set <font></font>
in the 'getInitialState' function.<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">同样，</font></font></p>

<pre><code>The replaceState() method is for when you want to clear out the values <font></font>
already in state, and add new ones.<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我先尝试</font></font><strong><code>this.setState({data: someArray});</code></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">然后</font></font><strong><code>this.replaceState({test: someArray});</code></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">再进行console.logging它们，发现</font></font><code>state</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">现在同时具有</font></font><code>data</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">和</font></font><code>test</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">然后，我</font></font><strong><code>this.setState({data: someArray});</code></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">依次</font><font style="vertical-align: inherit;">尝试</font></font><strong><code>this.setState({test: someArray});</code></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，然后进行console.logging它们，发现它们</font></font><code>state</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">又具有</font></font><code>data</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">和</font></font><code>test</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">那么，两者之间到底有什么区别？</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第1130篇《React.js中的setState与replaceState》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">小宇宙Itachi</span>
            <span class="discuss-time">2020.03.12</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">由于</font></font><code>replaceState</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">现已弃用，因此这是一个非常简单的解决方法。</font><font style="vertical-align: inherit;">尽管您很少/应该诉诸于此。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">删除状态：</font></font></p>

<pre><code>for (const old_key of Object.keys(this.state))<font></font>
    this.setState({ [old_key]: undefined });<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">或者，如果您不想多次拨打 </font></font><code>setState</code></p>

<pre><code>const new_state = {};<font></font>
for (const old_key of Object.keys(this.state))<font></font>
    new_state[old_key] = undefined;<font></font>
this.setState(new_state);<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">本质上，该状态下的所有先前键现在都返回</font></font><code>undefined</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，可以很容易地用一条</font></font><code>if</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">语句</font><font style="vertical-align: inherit;">过滤掉</font><font style="vertical-align: inherit;">：  </font></font></p>

<pre><code>if (this.state.some_old_key) {<font></font>
    // work with key<font></font>
} else {<font></font>
    // key is undefined (has been removed)<font></font>
}<font></font>
<font></font>
if ( ! this.state.some_old_key) {<font></font>
    // key is undefined (has been removed)<font></font>
} else {<font></font>
    // work with key<font></font>
}<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在JSX中：</font></font></p>

<pre><code>render() {<font></font>
    return &lt;div&gt;<font></font>
        { this.state.some_old_key ? "The state remains" : "The state is gone" }<font></font>
    &lt;/div&gt;<font></font>
}<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">最后，要“替换”状态，只需将新状态对象与旧状态副本合并为</font></font><code>undefined</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，然后将其设置为state即可：  </font></font></p>

<pre><code>const new_state = {new_key1: "value1", new_key2: "value2"};<font></font>
const state = this.state;<font></font>
<font></font>
for (const old_key of Object.keys(state))<font></font>
    state[old_key] = undefined;<font></font>
<font></font>
for (const new_key of Object.keys(new_state))<font></font>
    state[new_key] = new_state[new_key];<font></font>
<font></font>
this.setState(state);<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">小小Pro</span>
            <span class="discuss-time">2020.03.12</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">根据</font></font><a href="https://facebook.github.io/react/docs/component-api.html#replacestate" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">docs</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，</font></font><code>replaceState</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">可能会被弃用：</font></font></p>

<blockquote>
  <p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">此方法在扩展React.Component的ES6类组件上不可用。</font><font style="vertical-align: inherit;">在以后的React版本中可能会完全删除它。</font></font></p>
</blockquote></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">小胖Sam</span>
            <span class="discuss-time">2020.03.12</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">与</font></font><code>setState</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">当前和以前的状态合并。</font><font style="vertical-align: inherit;">使用</font></font><code>replaceState</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，它将抛出当前状态，并仅用您提供的状态替换它。</font><font style="vertical-align: inherit;">通常</font></font><code>setState</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">使用该命令，除非出于某种原因确实需要删除密钥；</font><font style="vertical-align: inherit;">但是将它们设置为false / null通常是更明确的策略。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">虽然有可能改变。</font><font style="vertical-align: inherit;">replaceState当前使用传递的对象作为状态，即</font></font><code>replaceState(x)</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，一旦被设置</font></font><code>this.state === x</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">它比轻一些</font></font><code>setState</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，因此如果成千上万的组件频繁设置其状态，则可以将其用作优化。</font></font><br>
 <sub><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我用</font></font><a href="http://jsbin.com/doqimeva/1/edit?js,output" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这个测试用例</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">断言了这</font><a href="http://jsbin.com/doqimeva/1/edit?js,output" rel="noreferrer"><font style="vertical-align: inherit;">一点</font></a><font style="vertical-align: inherit;">。</font></font></sub></p>

<hr>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果您的当前状态是</font></font><code>{a: 1}</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，并且您打电话</font></font><code>this.setState({b: 2})</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">; </font><font style="vertical-align: inherit;">当应用状态时，它将为</font></font><code>{a: 1, b: 2}</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">如果你打电话，</font></font><code>this.replaceState({b: 2})</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">你的状态将是</font></font><code>{b: 2}</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">旁注：状态不是立即设置的，因此</font></font><code>this.setState({b: 1}); console.log(this.state)</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在测试时</font><font style="vertical-align: inherit;">不要这样做</font><font style="vertical-align: inherit;">。</font></font></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
