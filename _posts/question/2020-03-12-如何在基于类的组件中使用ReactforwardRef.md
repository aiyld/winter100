---
layout: question
title:  如何在基于类的组件中使用React.forwardRef？
date:   2020-03-12T09:01:11.000Z
description: 我正在尝试使用React.forwardRef，但在如何使它在基于类的组件（而不是HOC）中工作方面遇到了麻烦。文档示例使用元素和功能组件，甚至将类包...
img: 
author: 凯泡芙JinJin
category: question
answer: 4
tags: JavaScript
topic: JavaScript
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我正在尝试使用React.forwardRef，但在如何使它在基于类的组件（而不是HOC）中工作方面遇到了麻烦。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">文档示例使用元素和功能组件，甚至将类包装在函数中以用于更高阶的组件。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">因此，从像</font></font><a href="https://codesandbox.io/s/p5q8y5m86x" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这样</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在他们的</font></font><code>ref.js</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">文件：</font></font></p>

<pre><code>const TextInput = React.forwardRef(<font></font>
    (props, ref) =&gt; (&lt;input type="text" placeholder="Hello World" ref={ref} /&gt;)<font></font>
);<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">而是将其定义如下：</font></font></p>

<pre><code>class TextInput extends React.Component {<font></font>
  render() {<font></font>
    let { props, ref } = React.forwardRef((props, ref) =&gt; ({ props, ref }));<font></font>
    return &lt;input type="text" placeholder="Hello World" ref={ref} /&gt;;<font></font>
  }<font></font>
}<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">要么</font></font></p>

<pre><code>class TextInput extends React.Component {<font></font>
  render() { <font></font>
    return (<font></font>
      React.forwardRef((props, ref) =&gt; (&lt;input type="text" placeholder="Hello World" ref={ref} /&gt;))<font></font>
    );<font></font>
  }<font></font>
}<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">只能工作：/</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">另外，我知道我知道，裁判不是反应方式。</font><font style="vertical-align: inherit;">我正在尝试使用第三方画布库，并希望将它们的一些工具添加到单独的组件中，因此我需要事件侦听器，因此需要生命周期方法。</font><font style="vertical-align: inherit;">稍后可能会走不同的路线，但是我想尝试一下。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">文档说这是可能的！</font></font></p>

<blockquote>
  <p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">引用转发不限于DOM组件。</font><font style="vertical-align: inherit;">您也可以将引用转发到类组件实例。</font></font></p>
</blockquote>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">从</font><a href="https://reactjs.org/docs/forwarding-refs.html#forwarding-refs-to-dom-components" rel="noreferrer"><font style="vertical-align: inherit;">本节</font></a><font style="vertical-align: inherit;">的</font></font><a href="https://reactjs.org/docs/forwarding-refs.html#forwarding-refs-to-dom-components" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">注释中。</font></font></a></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">但是随后他们继续使用HOC，而不仅仅是类。</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第1167篇《如何在基于类的组件中使用React.forwardRef？》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">StafanMandy</span>
            <span class="discuss-time">2020.03.12</span>
          </div>
          <div class="discuss-comment"><pre><code>class BeautifulInput extends React.Component {<font></font>
  const { innerRef, ...props } = this.props;<font></font>
  render() (<font></font>
    return (<font></font>
      &lt;div style={{backgroundColor: "blue"}}&gt;<font></font>
        &lt;input ref={innerRef} {...props} /&gt;<font></font>
      &lt;/div&gt;<font></font>
    )<font></font>
  )<font></font>
}<font></font>
<font></font>
const BeautifulInputForwardingRef = React.forwardRef((props, ref) =&gt; (<font></font>
  &lt;BeautifulInput {...props} innerRef={ref}/&gt;<font></font>
));<font></font>
<font></font>
const App = () =&gt; (<font></font>
  &lt;BeautifulInputForwardingRef ref={ref =&gt; ref &amp;&amp; ref.focus()} /&gt;<font></font>
)<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您需要使用其他道具名称来将引用转发到类。</font></font><code>innerRef</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在许多库中常用。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">小小Itachi</span>
            <span class="discuss-time">2020.03.12</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">基本上，这只是一个HOC函数。</font><font style="vertical-align: inherit;">如果您想在课堂上使用它，则可以自己做，并使用常规道具。</font></font></p>

<pre><code>class TextInput extends React.Component {<font></font>
    render() {<font></font>
        &lt;input ref={this.props.forwardRef} /&gt;<font></font>
    }<font></font>
}<font></font>
<font></font>
const ref = React.createRef();<font></font>
&lt;TextInput forwardRef={ref} /&gt;<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">例如，在中使用此模式，</font></font><code>styled-components</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">并</font><font style="vertical-align: inherit;">在</font><font style="vertical-align: inherit;">其中调用</font></font><code>innerRef</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">它。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">蛋蛋L西里</span>
            <span class="discuss-time">2020.03.12</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果您需要在许多不同的组件中重复使用此功能，则可以将此功能导出为类似 </font></font><code>withForwardingRef</code></p>

<pre><code>const withForwardingRef = &lt;Props extends {[_: string]: any}&gt;(BaseComponent: React.ReactType&lt;Props&gt;) =&gt;<font></font>
    React.forwardRef((props, ref) =&gt; &lt;BaseComponent {...props} forwardedRef={ref} /&gt;);<font></font>
<font></font>
export default withForwardingRef;<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">用法：</font></font></p>

<pre><code>const Comp = ({forwardedRef}) =&gt; (<font></font>
 &lt;input ref={forwardedRef} /&gt;<font></font>
)<font></font>
const EnhanceComponent = withForwardingRef&lt;Props&gt;(Comp);  // Now Comp has a prop called forwardedRef<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">MandyJinJin</span>
            <span class="discuss-time">2020.03.12</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">始终使用相同道具的想法</font></font><code>ref</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">可以通过使用帮助程序代理类导出来实现。</font></font></p>

<pre><code>class ElemComponent extends Component {<font></font>
  render() {<font></font>
    return (<font></font>
      &lt;div ref={this.props.innerRef}&gt;<font></font>
        Div has ref<font></font>
      &lt;/div&gt;<font></font>
    )<font></font>
  }<font></font>
}<font></font>
<font></font>
export default React.forwardRef((props, ref) =&gt; &lt;ElemComponent <font></font>
  innerRef={ref} {...props}<font></font>
/&gt;);<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">因此，基本上，是的，我们被迫具有其他支持转发引用的道具，但可以在中心下完成。</font><font style="vertical-align: inherit;">公众将其用作常规参考非常重要。</font></font></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
