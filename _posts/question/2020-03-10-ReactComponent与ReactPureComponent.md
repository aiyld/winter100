---
layout: question
title:  React.Component与React.PureComponent
date:   2020-03-10T14:23:13.000Z
description: 官方阵营文档状态“ React.PureComponent的shouldComponentUpdate()只有比较浅的对象”，并建议针对这一点，如果状态是...
img: 
author: 神无Green前端
category: question
answer: 3
tags: reactjs React.js
topic: React.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">官方</font></font><a href="https://reactjs.org/docs/react-api.html#reactpurecomponent" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">阵营文档</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">状态“ </font></font><code>React.PureComponent</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">的</font></font><code>shouldComponentUpdate()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">只有比较浅的对象”，并建议针对这一点，如果状态是‘深’。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">鉴于此，</font></font><code>React.PureComponent</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在创建React组件时，</font><font style="vertical-align: inherit;">为什么有人应该偏爱它</font><font style="vertical-align: inherit;">？</font></font></p>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">问题</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">：</font></font></p>

<ul>
<li><font style="vertical-align: inherit;"></font><code>React.Component</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我们可能会考虑</font><font style="vertical-align: inherit;">使用它对性能有什么影响</font></font><code>React.PureComponent</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">？</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我猜   </font></font><code>shouldComponentUpdate()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">的</font></font><code>PureComponent</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">执行只有浅薄的比较。</font><font style="vertical-align: inherit;">如果是这样，所述方法不能用于更深入的比较吗？</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">“此外，</font></font><code>React.PureComponent</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">会</font></font><code>shouldComponentUpdate()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">跳过整个组件子树的属性更新”-这是否意味着属性更改会被忽略？</font></font></li>
</ul>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果有帮助的话</font><font style="vertical-align: inherit;">，阅读该</font></font><a href="https://medium.com/modus-create-front-end-development/component-rendering-performance-in-react-df859b474adc#.d02ak0fwb" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">媒体博客会</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">引起疑问</font><font style="vertical-align: inherit;">。</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第518篇《React.Component与React.PureComponent》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">阿飞Harry小胖</span>
            <span class="discuss-time">2020.03.10</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">正如我所看到的，主要区别在于组件每次父组件都重新发布时都会重新发布，而不管组件的属性和状态是否已更改。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">另一方面，如果纯组件的父对象重新渲染，则不会重新渲染，除非纯组件的属性（或状态）已更改。 </font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">例如，假设我们有一个具有三级层次结构的组件树：父级，子级和孙级。 </font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">当父母的道具以仅改变一个孩子的道具的方式改变时，则：</font></font></p>

<ul>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果所有组件都是常规组件，则整个组件树将重新呈现</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果所有子孙都是纯组件，则只有一个孩子会退任，其子孙中的一个或全部将退还，这取决于他们的道具是否被更改。</font><font style="vertical-align: inherit;">如果此组件树中有很多组件，则可能意味着性能上的显着提高。</font></font></li>
</ul>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">但是，有时使用纯组件不会产生任何影响。</font><font style="vertical-align: inherit;">当父母从redux商店收到道具时，需要对孩子的道具进行复杂的计算时，我遇到了这样的情况。</font><font style="vertical-align: inherit;">父母使用平面清单来呈现其孩子。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">结果是，每当redux存储区进行很小的更改时，都会重新计算儿童数据的整个平面列表。</font><font style="vertical-align: inherit;">这意味着对于树中的每个组件，道具都是新对象，即使其值没有变化。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在这种情况下，纯组件无济于事，并且如果需要重新渲染，则只能通过使用常规组件并在shouldComponentUpdate中检入子代来实现性能提升。 </font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">理查德小卤蛋</span>
            <span class="discuss-time">2020.03.10</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">之间的主要区别</font></font><code>React.PureComponent</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，并</font></font><code>React.Component</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">为</font></font><code>PureComponent</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">做一个</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">浅浅的比较</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">上的状态变化。</font><font style="vertical-align: inherit;">这意味着在比较标量值时，它会比较它们的值，但是在比较对象时，它只会比较引用。</font><font style="vertical-align: inherit;">它有助于提高应用程序的性能。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您</font></font><code>React.PureComponent</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">可以满足以下任何条件。</font></font></p>

<ul>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">状态/道具应该是不可变的对象 </font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">状态/道具不应具有层次结构</font></font></li>
<li><font style="vertical-align: inherit;"></font><code>forceUpdate</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">数据更改时</font><font style="vertical-align: inherit;">您应该致电</font></font></li>
</ul>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果您正在使用</font></font><code>React.PureComponent</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，则应确保所有子组件也都是纯组件。</font></font></p>

<blockquote>
  <p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我们可以考虑将React.PureComponent用作React.component会对性能产生任何影响？</font></font></p>
</blockquote>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">是的，它将提高您的应用程序性能（由于比较浅）</font></font></p>

<blockquote>
  <p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我猜测Purecomponent的shouldComponentUpdate（）仅执行浅表比较。</font><font style="vertical-align: inherit;">如果是这种情况，该方法不能用于更深入的比较吗？</font></font></p>
</blockquote>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您猜对了。</font><font style="vertical-align: inherit;">如果您满足我上面提到的任何条件，则可以使用它。</font></font></p>

<blockquote>
  <p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">“此外，React.PureComponent的shouldComponentUpdate（）会跳过整个组件子树的属性更新”-这是否意味着属性更改会被忽略？</font></font></p>
</blockquote>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">是的，如果在浅层比较中找不到区别，则道具更改将被忽略。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">TomGil村村</span>
            <span class="discuss-time">2020.03.10</span>
          </div>
          <div class="discuss-comment"><h1><code>Component</code> and <code>PureComponent</code> have one difference</h1>

<p><code>PureComponent</code> is exactly the same as <code>Component</code> except that it handles the <code>shouldComponentUpdate</code> method for you.</p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">当道具或状态发生变化时，</font></font><code>PureComponent</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">将对</font><font style="vertical-align: inherit;">道具和状态</font><font style="vertical-align: inherit;">进行</font></font><strong><em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">浅浅的比较</font></font></em></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font><code>Component</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">另一方面，开箱即用时不会比较当前道具和状态。</font><font style="vertical-align: inherit;">因此，无论何时</font></font><code>shouldComponentUpdate</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">调用</font><font style="vertical-align: inherit;">，组件都会默认重新渲染</font><font style="vertical-align: inherit;">。</font></font></p>

<h3><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">浅比较</font></font></h3>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">当比较先前的道具和状态与下一个道具时，浅表比较将检查基元具有相同的值（例如1等于1或true等于true），并且在更复杂的javascript值（如对象和数组）之间引用相同。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">来源：</font><a href="https://codeburst.io/when-to-use-component-or-purecomponent-a60cfad01a81" rel="noreferrer"><font style="vertical-align: inherit;">https</font></a><font style="vertical-align: inherit;"> : </font></font><a href="https://codeburst.io/when-to-use-component-or-purecomponent-a60cfad01a81" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">//codeburst.io/when-to-use-component-or-purecomponent-a60cfad01a81</font></font></a></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
