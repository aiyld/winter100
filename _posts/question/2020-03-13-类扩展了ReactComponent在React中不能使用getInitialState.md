---
layout: question
title:  类扩展了React.Component在React中不能使用getInitialState
date:   2020-03-13T12:12:23.000Z
description: 我正在React中调试ES6语法，并编写如下组件：export default class Loginform extends React.Compo...
img: 
author: 
category: question
answer: 2
tags: reactjs React.js
topic: React.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我正在React中调试ES6语法，并编写如下组件：</font></font></p>

<pre><code>export default class Loginform extends React.Component {<font></font>
    getInitialState() {<font></font>
        return {<font></font>
          name: '',<font></font>
          password: ''<font></font>
        };<font></font>
    };<font></font>
}<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">但是浏览器使我警惕：</font></font></p>

<blockquote>
  <p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">警告：getInitialState是在Loginform（普通的JavaScript类）上定义的。</font><font style="vertical-align: inherit;">仅使用React.createClass创建的类支持此功能。</font><font style="vertical-align: inherit;">您是要定义状态属性吗？</font></font></p>
</blockquote>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我可以使用传统语法来处理它，</font></font><code>var Loginform = React.createClass</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">但是正确的ES6语法是什么？</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">另一件事，我认为传统语法</font></font><code>React.createClass</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">是一个对象，因此其中的函数用逗号分隔，但是对于</font></font><code>extends</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">需要分号</font><font style="vertical-align: inherit;">的</font><font style="vertical-align: inherit;">类，我不太了解。</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第1527篇《类扩展了React.Component在React中不能使用getInitialState》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">小胖Itachi</span>
            <span class="discuss-time">2020.03.13</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果我们使用类字段，则以下工作正常。</font></font></p>

<pre><code>state = {<font></font>
      name: '',<font></font>
      password: ''<font></font>
}<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">可以代替 </font></font></p>

<pre><code>constructor(props, context) {<font></font>
    super(props, context);<font></font>
<font></font>
    this.state = {<font></font>
      name: '',<font></font>
      password: ''<font></font>
    };<font></font>
  };<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">十三前端Harry</span>
            <span class="discuss-time">2020.03.13</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">ES6类方法声明之间不需要分号或逗号。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">对于ES6类，</font></font><code>getInitialState</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">已弃用，而在构造函数中声明初始状态对象：</font></font></p>

<pre><code>export default class Loginform extends React.Component {<font></font>
  constructor(props, context) {<font></font>
    super(props, context);<font></font>
<font></font>
    this.state = {<font></font>
      name: '',<font></font>
      password: ''<font></font>
    };<font></font>
  };<font></font>
}<font></font>
</code></pre></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
