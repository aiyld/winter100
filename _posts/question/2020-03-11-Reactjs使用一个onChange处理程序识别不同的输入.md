---
layout: question
title:  React.js：使用一个onChange处理程序识别不同的输入
date:   2020-03-11T07:37:20.000Z
description: 好奇解决此问题的正确方法是：var Hello = React.createClass({getInitialState  function() {...
img: 
author: 凯神无
category: question
answer: 3
tags: JavaScript
topic: JavaScript
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">好奇解决此问题的正确方法是：</font></font></p>

<pre><code>var Hello = React.createClass({<font></font>
getInitialState: function() {<font></font>
    return {total: 0, input1:0, input2:0};<font></font>
},<font></font>
render: function() {<font></font>
    return (<font></font>
        &lt;div&gt;{this.state.total}&lt;br/&gt;<font></font>
            &lt;input type="text" value={this.state.input1} onChange={this.handleChange} /&gt;<font></font>
            &lt;input type="text" value={this.state.input2} onChange={this.handleChange} /&gt;<font></font>
        &lt;/div&gt;<font></font>
    );<font></font>
},<font></font>
handleChange: function(e){<font></font>
    this.setState({ ??? : e.target.value});<font></font>
    t = this.state.input1 + this.state.input2;<font></font>
    this.setState({total: t});<font></font>
}<font></font>
});<font></font>
<font></font>
React.renderComponent(&lt;Hello /&gt;, document.getElementById('content'));<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">显然，您可以创建单独的handleChange函数来处理每个不同的输入，但这不是很好。</font><font style="vertical-align: inherit;">同样，您可以只为单个输入创建一个组件，但是我想看看是否有办法做到这一点。</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第739篇《React.js：使用一个onChange处理程序识别不同的输入》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Green小宇宙伽罗</span>
            <span class="discuss-time">2020.03.11</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您可以</font></font><code>input</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">通过创建一个单独的</font></font><code>InputField</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">组件来管理单个</font><font style="vertical-align: inherit;">孩子的价值来跟踪每个孩子</font><font style="vertical-align: inherit;">的价值</font></font><code>input</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">例如，</font></font><code>InputField</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">可能是：</font></font></p>

<pre><code>var InputField = React.createClass({<font></font>
  getInitialState: function () {<font></font>
    return({text: this.props.text})<font></font>
  },<font></font>
  onChangeHandler: function (event) {<font></font>
     this.setState({text: event.target.value})<font></font>
  }, <font></font>
  render: function () {<font></font>
    return (&lt;input onChange={this.onChangeHandler} value={this.state.text} /&gt;)<font></font>
  }<font></font>
})<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">现在，</font></font><code>input</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">可以在该</font></font><code>InputField</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">组件</font><font style="vertical-align: inherit;">的单独实例内跟踪</font><font style="vertical-align: inherit;">每个</font><font style="vertical-align: inherit;">组件的值，而无需在父级状态下创建单独的值来监视每个子组件。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">宝儿Davaid</span>
            <span class="discuss-time">2020.03.11</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">@Vigril Disgr4ce</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">对于多字段表单，使用React的关键功能（组件）是有意义的。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在我的项目中，我创建了TextField组件，该组件至少具有一个值道具，并且它负责处理输入文本字段的常见行为。</font><font style="vertical-align: inherit;">这样，您在更新值状态时不必担心跟踪字段名称。</font></font></p>

<pre><code>[...]<font></font>
<font></font>
handleChange: function(event) {<font></font>
  this.setState({value: event.target.value});<font></font>
},<font></font>
render: function() {<font></font>
  var value = this.state.value;<font></font>
  return &lt;input type="text" value={value} onChange={this.handleChange} /&gt;;<font></font>
}<font></font>
<font></font>
[...]<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">小宇宙飞云</span>
            <span class="discuss-time">2020.03.11</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">该</font></font><code>onChange</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">事件冒泡......所以，你可以这样做：</font></font></p>

<pre><code>// A sample form<font></font>
render () {<font></font>
  &lt;form onChange={setField}&gt;<font></font>
    &lt;input name="input1" /&gt;<font></font>
    &lt;input name="input2" /&gt;<font></font>
  &lt;/form&gt;<font></font>
}<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">而且您的setField方法可能看起来像这样（假设您使用的是ES2015或更高版本：</font></font></p>

<pre><code>setField (e) {<font></font>
  this.setState({[e.target.name]: e.target.value})<font></font>
}<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我在几个应用程序中都使用了类似的东西，这非常方便。</font></font></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
