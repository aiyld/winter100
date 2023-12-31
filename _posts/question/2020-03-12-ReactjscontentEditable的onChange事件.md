---
layout: question
title:  React.js：contentEditable的onChange事件
date:   2020-03-12T07:15:13.000Z
description: 如何监听contentEditable基于控件的更改事件？var Number = React.createClass({    render  f...
img: 
author: Near小哥西门
category: question
answer: 4
tags: JavaScript
topic: JavaScript
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如何监听</font></font><code>contentEditable</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">基于控件的</font><font style="vertical-align: inherit;">更改事件</font><font style="vertical-align: inherit;">？</font></font></p>

<pre><code>var Number = React.createClass({<font></font>
    render: function() {<font></font>
        return &lt;div&gt;<font></font>
            &lt;span contentEditable={true} onChange={this.onChange}&gt;<font></font>
                {this.state.value}<font></font>
            &lt;/span&gt;<font></font>
            =<font></font>
            {this.state.value}<font></font>
        &lt;/div&gt;;<font></font>
    },<font></font>
    onChange: function(v) {<font></font>
        // Doesn't fire :(<font></font>
        console.log('changed', v);<font></font>
    },<font></font>
    getInitialState: function() {<font></font>
        return {value: '123'}<font></font>
    }    <font></font>
});<font></font>
<font></font>
React.renderComponent(&lt;Number /&gt;, document.body);<font></font>
</code></pre>

<p><a href="http://jsfiddle.net/NV/kb3gN/1621/" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">http://jsfiddle.net/NV/kb3gN/1621/</font></font></a></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第1041篇《React.js：contentEditable的onChange事件》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">SamStafan十三</span>
            <span class="discuss-time">2020.03.12</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这是由lovasoa整合的大部分组件：</font><a href="https://github.com/lovasoa/react-contenteditable/blob/master/index.js" rel="nofollow"><font style="vertical-align: inherit;">https</font></a><font style="vertical-align: inherit;"> : </font></font><a href="https://github.com/lovasoa/react-contenteditable/blob/master/index.js" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">//github.com/lovasoa/react-contenteditable/blob/master/index.js</font></font></a></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">他在emitChange中填充事件</font></font></p>

<pre><code>emitChange: function(evt){<font></font>
    var html = this.getDOMNode().innerHTML;<font></font>
    if (this.props.onChange &amp;&amp; html !== this.lastHtml) {<font></font>
        evt.target = { value: html };<font></font>
        this.props.onChange(evt);<font></font>
    }<font></font>
    this.lastHtml = html;<font></font>
}<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我正在成功使用类似的方法</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">十三古一</span>
            <span class="discuss-time">2020.03.12</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">由于完成编辑后，总是会失去元素的焦点，因此您可以简单地使用onBlur挂钩。</font></font></p>

<pre><code>&lt;div onBlur={(e)=&gt;{console.log(e.currentTarget.textContent)}} contentEditable suppressContentEditableWarning={true}&gt;<font></font>
     &lt;p&gt;Lorem ipsum dolor.&lt;/p&gt;<font></font>
&lt;/div&gt;<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">西门樱前端</span>
            <span class="discuss-time">2020.03.12</span>
          </div>
          <div class="discuss-comment"><p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">编辑：</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">请参阅</font></font><a href="https://stackoverflow.com/questions/22677931/react-js-onchange-event-for-contenteditable/27255103#27255103"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Sebastien Lorber的答案</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，该</font><a href="https://stackoverflow.com/questions/22677931/react-js-onchange-event-for-contenteditable/27255103#27255103"><font style="vertical-align: inherit;">答案</font></a><font style="vertical-align: inherit;">修复了我的实现中的错误。</font></font></p>

<hr>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">使用onInput事件，也可以使用onBlur作为后备。</font><font style="vertical-align: inherit;">您可能需要保存以前的内容，以防止发送额外的事件。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我个人将其作为渲染功能。</font></font></p>

<pre><code>var handleChange = function(event){<font></font>
    this.setState({html: event.target.value});<font></font>
}.bind(this);<font></font>
<font></font>
return (&lt;ContentEditable html={this.state.html} onChange={handleChange} /&gt;);<font></font>
</code></pre>

<h2><a href="http://jsbin.com/vamuxayu/2/edit?js,output" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">jsbin</font></font></a></h2>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">它使用围绕contentEditable的简单包装器。</font></font></p>

<pre><code>var ContentEditable = React.createClass({<font></font>
    render: function(){<font></font>
        return &lt;div <font></font>
            onInput={this.emitChange} <font></font>
            onBlur={this.emitChange}<font></font>
            contentEditable<font></font>
            dangerouslySetInnerHTML={{__html: this.props.html}}&gt;&lt;/div&gt;;<font></font>
    },<font></font>
    shouldComponentUpdate: function(nextProps){<font></font>
        return nextProps.html !== this.getDOMNode().innerHTML;<font></font>
    },<font></font>
    emitChange: function(){<font></font>
        var html = this.getDOMNode().innerHTML;<font></font>
        if (this.props.onChange &amp;&amp; html !== this.lastHtml) {<font></font>
<font></font>
            this.props.onChange({<font></font>
                target: {<font></font>
                    value: html<font></font>
                }<font></font>
            });<font></font>
        }<font></font>
        this.lastHtml = html;<font></font>
    }<font></font>
});<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Davaid阳光</span>
            <span class="discuss-time">2020.03.12</span>
          </div>
          <div class="discuss-comment"><p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">编辑2015</font></font></strong></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">有人用我的解决方案在NPM上做了一个项目：</font><a href="https://github.com/lovasoa/react-contenteditable"><font style="vertical-align: inherit;">https</font></a><font style="vertical-align: inherit;"> : </font></font><a href="https://github.com/lovasoa/react-contenteditable"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">//github.com/lovasoa/react-contenteditable</font></font></a></p>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">编辑06/2016：</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我刚刚遇到了一个新问题，当浏览器尝试“重新格式化”刚刚给他的html时，会导致组件始终重新呈现，这会出现一个新问题。</font></font><a href="https://github.com/lovasoa/react-contenteditable/issues/18"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">看到</font></font></a></p>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">编辑07/2016：</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这是我的生产contentEditable实现。</font><font style="vertical-align: inherit;">它有一些</font></font><code>react-contenteditable</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您可能想要的</font><font style="vertical-align: inherit;">其他选项</font><font style="vertical-align: inherit;">，包括：</font></font></p>

<ul>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">锁定</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">命令式API允许嵌入html片段</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">重新格式化内容的能力 </font></font></li>
</ul>

<h1><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">摘要：</font></font></h1>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在我遇到新问题之前，FakeRainBrigand的解决方案对我来说已经工作了一段时间。</font><font style="vertical-align: inherit;">ContentEditables令人痛苦，并且很难与React轻松应对。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这个</font></font><a href="http://jsfiddle.net/kb3gN/8349/"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">JSFiddle</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">演示了这个问题。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如您所见，当您键入一些字符并单击时</font></font><code>Clear</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，不会清除内容。</font><font style="vertical-align: inherit;">这是因为我们尝试将contenteditable重置为最后一个已知的虚拟dom值。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">因此，似乎：</font></font></p>

<ul>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您需要</font></font><code>shouldComponentUpdate</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">防止插入符位置跳动</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果使用</font></font><code>shouldComponentUpdate</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这种方式，</font><font style="vertical-align: inherit;">则不能依赖React的VDOM差异算法</font><font style="vertical-align: inherit;">。</font></font></li>
</ul>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">因此，您需要额外的一行，以便每当</font></font><code>shouldComponentUpdate</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">返回yes时，就可以确保DOM内容实际上已更新。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">因此，此处的版本添加了</font></font><code>componentDidUpdate</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，变为：</font></font></p>

<pre><code>var ContentEditable = React.createClass({<font></font>
    render: function(){<font></font>
        return &lt;div id="contenteditable"<font></font>
            onInput={this.emitChange} <font></font>
            onBlur={this.emitChange}<font></font>
            contentEditable<font></font>
            dangerouslySetInnerHTML={{__html: this.props.html}}&gt;&lt;/div&gt;;<font></font>
    },<font></font>
<font></font>
    shouldComponentUpdate: function(nextProps){<font></font>
        return nextProps.html !== this.getDOMNode().innerHTML;<font></font>
    },<font></font>
<font></font>
    componentDidUpdate: function() {<font></font>
        if ( this.props.html !== this.getDOMNode().innerHTML ) {<font></font>
           this.getDOMNode().innerHTML = this.props.html;<font></font>
        }<font></font>
    },<font></font>
<font></font>
    emitChange: function(){<font></font>
        var html = this.getDOMNode().innerHTML;<font></font>
        if (this.props.onChange &amp;&amp; html !== this.lastHtml) {<font></font>
            this.props.onChange({<font></font>
                target: {<font></font>
                    value: html<font></font>
                }<font></font>
            });<font></font>
        }<font></font>
        this.lastHtml = html;<font></font>
    }<font></font>
});<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">虚拟dom仍然过时，并且它可能不是最有效的代码，但至少它确实有效:) </font></font><a href="http://jsfiddle.net/kb3gN/8352/"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我的错误已解决</font></font></a></p>

<hr>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">细节：</font></font></strong></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">1）如果放置了shouldComponentUpdate以避免插入符号跳动，则contenteditable永不放弃（至少在击键时）</font></font></p>

<p>2) If the component never rerenders on key stroke, then React keeps an outdated virtual dom for this contenteditable.</p>

<p>3) If React keeps an outdated version of the contenteditable in its virtual dom tree, then if you try to reset the contenteditable to the value outdated in the virtual dom, then during the virtual dom diff, React will compute that there are no changes to apply to the DOM!</p>

<p>This happens mostly when:</p>

<ul>
<li>you have an empty contenteditable initially (shouldComponentUpdate=true,prop="",previous vdom=N/A), </li>
<li>the user types some text and you prevent renderings (shouldComponentUpdate=false,prop=text,previous vdom="") </li>
<li>after user clicks a validation button, you want to empty that field (shouldComponentUpdate=false,prop="",previous vdom="")</li>
<li>as both the newly produced and old vdom are "", React does not touch the dom.</li>
</ul></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
