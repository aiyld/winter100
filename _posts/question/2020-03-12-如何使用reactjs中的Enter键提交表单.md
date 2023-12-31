---
layout: question
title:  如何使用react.js中的Enter键提交表单？
date:   2020-03-12T09:33:53.000Z
description: 这是我的表单和onClick方法。我想在按下键盘的Enter按钮时执行此方法。怎么样 ？注意：没有jquery被赞赏。 comment  func...
img: 
author: 小宇宙前端
category: question
answer: 2
tags: reactjs React.js
topic: React.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这是我的表单和onClick方法。</font><font style="vertical-align: inherit;">我想在按下键盘的Enter按钮时执行此方法。</font><font style="vertical-align: inherit;">怎么样 ？</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">注意：</font></font><em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">没有jquery被赞赏。</font></font></em></p>

<pre><code> comment: function (e) {<font></font>
        e.preventDefault();<font></font>
        this.props.comment({comment: this.refs.text.getDOMNode().value, userPostId:this.refs.userPostId.getDOMNode().value})<font></font>
    },<font></font>
<font></font>
<font></font>
 &lt;form className="commentForm"&gt;<font></font>
     &lt;textarea rows="2" cols="110" placeholder="****Comment Here****" ref="text"  /&gt;&lt;br /&gt;<font></font>
    &lt;input type="text" placeholder="userPostId" ref="userPostId" /&gt; &lt;br /&gt;<font></font>
     &lt;button type="button" className="btn btn-success" onClick={this.comment}&gt;Comment&lt;/button&gt;<font></font>
    &lt;/form&gt;<font></font>
</code></pre></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第1221篇《如何使用react.js中的Enter键提交表单？》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">JimHarry</span>
            <span class="discuss-time">2020.03.12</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">更改</font></font><code>&lt;button type="button"</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">为</font></font><code>&lt;button type="submit"</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">删除</font></font><code>onClick</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">相反</font></font><code>&lt;form className="commentForm" onSubmit={this.onFormSubmit}&gt;</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">这应该可以单击按钮并按回车键。</font></font></p>

<pre><code>onFormSubmit = e =&gt; {<font></font>
  e.preventDefault();<font></font>
  const { name, email } = this.state;<font></font>
  // send to server with e.g. `window.fetch`<font></font>
}<font></font>
<font></font>
...<font></font>
<font></font>
&lt;form onSubmit={this.onFormSubmit}&gt;<font></font>
  ...<font></font>
  &lt;button type="submit"&gt;Submit&lt;/button&gt;<font></font>
&lt;/form&gt;<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">乐米亚</span>
            <span class="discuss-time">2020.03.12</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">自上次回答此问题以来已有好几年了。</font><font style="vertical-align: inherit;">React在2017年推出了“ Hooks”，而“ keyCode”已被弃用。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">现在我们可以这样写：</font></font></p>

<pre><code>  useEffect(() =&gt; {<font></font>
    const listener = event =&gt; {<font></font>
      if (event.code === "Enter" || event.code === "NumpadEnter") {<font></font>
        console.log("Enter key was pressed. Run your function.");<font></font>
        // callMyFunction();<font></font>
      }<font></font>
    };<font></font>
    document.addEventListener("keydown", listener);<font></font>
    return () =&gt; {<font></font>
      document.removeEventListener("keydown", listener);<font></font>
    };<font></font>
  }, []);<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"></font><code>keydown</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">首次加载组件时，</font><font style="vertical-align: inherit;">它将在</font><font style="vertical-align: inherit;">事件</font><font style="vertical-align: inherit;">上注册一个侦听器</font><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">销毁组件后，它将删除事件侦听器。</font></font></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
