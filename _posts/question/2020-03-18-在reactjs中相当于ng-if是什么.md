---
layout: question
title:  在react.js中相当于ng-if是什么？
date:   2020-03-18T07:48:51.000Z
description: 我开始对使用angular做出反应，并尝试找出我可以根据条件渲染或不渲染元素的Ang- ng-if指令的替代方法。以下面的代码为例。我正在使用TypeScript（ts...
img: 
author: 卡卡西达蒙
category: question
answer: 8
tags: reactjs React.js
topic: React.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我开始对使用angular做出反应，并尝试找出我可以根据条件渲染或不渲染元素的Ang- ng-if指令的替代方法。</font><font style="vertical-align: inherit;">以下面的代码为例。</font><font style="vertical-align: inherit;">我正在使用TypeScript（tsx）btw，但这没什么大不了的。</font></font></p>

<pre><code>"use strict";<font></font>
<font></font>
import * as React from 'react';<font></font>
<font></font>
interface MyProps {showMe: Boolean}<font></font>
interface MyState {}<font></font>
<font></font>
class Button extends React.Component &lt;MyProps, MyState&gt;{<font></font>
  constructor(props){<font></font>
    super(props);<font></font>
    this.state = {};<font></font>
  }<font></font>
<font></font>
  render(){<font></font>
    let button;<font></font>
    if (this.props.showMe === true){<font></font>
       button = (<font></font>
        &lt;button type="submit" className="btn nav-btn-red"&gt;SIGN UP&lt;/button&gt;<font></font>
      )<font></font>
    } else {<font></font>
      button = null;<font></font>
    }<font></font>
    return button;<font></font>
<font></font>
}<font></font>
}<font></font>
export default Button;<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">此解决方案有效，但是通常还有另一种方法可以达到这种效果吗？</font><font style="vertical-align: inherit;">我只是在猜测</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第2038篇《在react.js中相当于ng-if是什么？》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">SamItachi</span>
            <span class="discuss-time">2020.03.18</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我不喜欢代码中有很多三元运算符。</font><font style="vertical-align: inherit;">这就是为什么我制作了一个包含几个有用组件的库的原因。</font><font style="vertical-align: inherit;">“ RcIf”</font></font></p>

<pre><code>  &lt;RcIf if={condition} &gt;<font></font>
    &lt;h1&gt;I no longer miss ngif&lt;/h1&gt;<font></font>
  &lt;/RcIf&gt;<font></font>
  &lt;RcIf if={othercondition} &gt;<font></font>
    &lt;h1&gt;I no longer miss v-if&lt;/h1&gt;<font></font>
    &lt;RcElse&gt;<font></font>
      &lt;h1&gt;I love react&lt;/h1&gt;<font></font>
    &lt;/RcElse&gt;<font></font>
  &lt;/RcIf&gt;<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您可以从npm安装它</font></font></p>

<p><a href="https://www.npmjs.com/package/rc-if" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">https://www.npmjs.com/package/rc-if</font></font></a></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">神无梅</span>
            <span class="discuss-time">2020.03.18</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我是Tersus-jsx.macro的创建者，我认为该模块提供了此问题的确切条件。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">无需混合JSX表达式和ES6来实现ng-if或ng-repeat，此宏允许执行与AngularJS for React JSX中相同的操作，例如ng-if：</font></font></p>

<pre><code>&lt;div&gt;<font></font>
  &lt;button<font></font>
    tj-if={a === 0}<font></font>
    id="gotoA"<font></font>
    className="link"<font></font>
    onClick={clicking}<font></font>
  /&gt;<font></font>
&lt;/div&gt;<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">相当于</font></font></p>

<pre><code>&lt;div&gt;<font></font>
  {(a === 0) &amp;&amp; (<font></font>
    &lt;button<font></font>
      id="gotoA"<font></font>
      className="link"<font></font>
      onClick={clicking}<font></font>
    /&gt;<font></font>
  )}<font></font>
&lt;/div&gt;<font></font>
</code></pre>

<p>Given that the latest version of create-react-app support Babel-Macro out of the box, all you need to do is npm install this module, wrap the render return with "tersus" and start assigning those props.</p>

<p>You can install this from:
<a href="https://www.npmjs.com/package/tersus-jsx.macro" rel="nofollow noreferrer">https://www.npmjs.com/package/tersus-jsx.macro</a></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">小小卡卡西小卤蛋</span>
            <span class="discuss-time">2020.03.18</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我也来自一个有角度的背景，并且正在寻找一种简单的衬纸来显示变量是否包含任何元素的标签。</font><font style="vertical-align: inherit;">这为我工作：</font></font></p>

<pre><code>&lt;div className="comic_creators"&gt;<font></font>
    {c.creators.available &gt; 0 ? &lt;h4&gt;Creators&lt;/h4&gt; : null }<font></font>
    {c.creators.items.map((creator,key) =&gt;<font></font>
        &lt;Creator creator={creator} key={key}&gt;&lt;/Creator&gt;<font></font>
    )}<font></font>
&lt;/div&gt;<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Davaid十三樱</span>
            <span class="discuss-time">2020.03.18</span>
          </div>
          <div class="discuss-comment"><blockquote>
  <p><code>false</code>, <code>null</code>, <code>undefined</code>, and <code>true</code> are valid children. They simply don’t
  render. These JSX expressions will all render to the same thing:</p>
</blockquote>

<p>So you can try this </p>

<pre><code>const conditional=({condition,someArray})=&gt;{<font></font>
     return(<font></font>
        &lt;div&gt;<font></font>
          {condition &amp;&amp; &lt;Header /&gt; // condition being boolean} <font></font>
          {someArray.length&gt;0 &amp;&amp; &lt;Content /&gt;}<font></font>
        &lt;/div&gt;<font></font>
      )<font></font>
}<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这对于有条件地渲染React元素很有用。</font><font style="vertical-align: inherit;">此JSX仅呈现if条件为true，并且仅在someArray.length&gt; 0时呈现</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">MandyTony</span>
            <span class="discuss-time">2020.03.18</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我只是想补充一点，</font></font><code>*ngIf</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在angular中不会实例化它所连接的组件。</font><font style="vertical-align: inherit;">在React中，如果您在语句中使用if语句，</font></font><code>return</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">则即使未显示该组件，它仍将实例化该组件。</font><font style="vertical-align: inherit;">为了</font></font><code>*ngIf</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在React中</font><font style="vertical-align: inherit;">实现真正的</font><font style="vertical-align: inherit;">类型行为，您必须创建一个变量，该变量将条件组件保留在</font></font><code>return</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">语句</font><font style="vertical-align: inherit;">之外</font><font style="vertical-align: inherit;">：</font></font></p>

<pre><code>render() {<font></font>
<font></font>
  const show = false<font></font>
<font></font>
  return (<font></font>
    if (show) {<font></font>
       &lt;AwesomeComponent /&gt;   //still instantiated<font></font>
    }<font></font>
  )<font></font>
}<font></font>
<font></font>
render() {<font></font>
<font></font>
  let c = null<font></font>
  const show = false<font></font>
<font></font>
  if (show) {<font></font>
    c = &lt;AwesomeComponent /&gt;   //not instantiated<font></font>
  }<font></font>
  return (<font></font>
    c<font></font>
  )<font></font>
}<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Tony路易</span>
            <span class="discuss-time">2020.03.18</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如何</font></font><a href="https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Operators/Conditional_Operator" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">三元运算符</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">？</font></font></p>

<pre><code>render() {<font></font>
  return (<font></font>
    this.props.showMe ? &lt;button type="submit" className="btn nav-btn-red"&gt;SIGN UP&lt;/button&gt; : null<font></font>
  );<font></font>
}<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Itachi猿</span>
            <span class="discuss-time">2020.03.18</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果您还有其他元素，则可以像这样包装条件：</font></font></p>

<pre><code>render() {<font></font>
  return (<font></font>
    &lt;div&gt;Stuff&lt;/div&gt;<font></font>
    {this.props.showMe &amp;&amp; (<font></font>
      &lt;button type="submit" className="btn nav-btn-red"&gt;SIGN UP&lt;/button&gt;<font></font>
    )}<font></font>
    &lt;div&gt;More stuff&lt;/div&gt;<font></font>
  );<font></font>
}<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">猿前端猿</span>
            <span class="discuss-time">2020.03.18</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">更好一点：</font></font></p>

<pre><code>render() {<font></font>
  return (<font></font>
    this.props.showMe &amp;&amp; &lt;button type="submit" className="btn nav-btn-red"&gt;SIGN UP&lt;/button&gt;<font></font>
  );<font></font>
}<font></font>
</code></pre></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
