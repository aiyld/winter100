---
layout: question
title:  我什么时候应该使用React.cloneElement和this.props.children？
date:   2020-03-12T04:46:55.000Z
description: 我仍然是React的菜鸟，在互联网上的许多示例中，我看到了渲染子元素时出现的这种变化，我感到困惑。通常我看到以下内容：class Users exte...
img: 
author: Jim西门
category: question
answer: 3
tags: reactjs React.js
topic: React.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我仍然是React的菜鸟，在互联网上的许多示例中，我看到了渲染子元素时出现的这种变化，我感到困惑。</font><font style="vertical-align: inherit;">通常我看到以下内容：</font></font></p>

<pre><code>class Users extends React.Component {<font></font>
  render() {<font></font>
    return (<font></font>
      &lt;div&gt;<font></font>
        &lt;h2&gt;Users&lt;/h2&gt;<font></font>
        {this.props.children}<font></font>
      &lt;/div&gt;<font></font>
    )<font></font>
  }<font></font>
}<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">但是然后我看到一个这样的例子：</font></font></p>

<pre><code>&lt;ReactCSSTransitionGroup<font></font>
     component="div"<font></font>
     transitionName="example"<font></font>
     transitionEnterTimeout={500}<font></font>
     transitionLeaveTimeout={500}<font></font>
     &gt;<font></font>
     {React.cloneElement(this.props.children, {<font></font>
       key: this.props.location.pathname<font></font>
      })}<font></font>
&lt;/ReactCSSTransitionGroup&gt;<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">现在，我了解了api，但是</font></font><a href="https://reactjs.org/docs/react-api.html#cloneelement" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">文档</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">并未确切说明我何时应该使用它。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">那么，一个人做什么却另一个人不能做什么呢？</font><font style="vertical-align: inherit;">有人可以用更好的例子向我解释吗？</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第960篇《我什么时候应该使用React.cloneElement和this.props.children？》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">蛋蛋猴子</span>
            <span class="discuss-time">2020.03.12</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">其实</font></font><code>React.cloneElement</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">并没有严格的关联</font></font><code>this.props.children</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">每当您需要克隆react elements（</font></font><code>PropTypes.element</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">）以添加/覆盖prop而不希望父级不了解有关这些组件内部的知识（例如，附加事件处理程序或分配</font></font><code>key</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">/ </font></font><code>ref</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">属性）时</font><font style="vertical-align: inherit;">，此方法就很</font><font style="vertical-align: inherit;">有用</font><font style="vertical-align: inherit;">。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">反应元素也是</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">不可变的</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p>

<blockquote>
  <p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">React.cloneElement（element，[props]，[... children]）几乎等同于：
  </font></font><code>&lt;element.type {...element.props} {...props}&gt;{children}&lt;/element.type&gt;</code></p>
</blockquote>

<hr>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">但是，</font></font><code>children</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">React中</font><font style="vertical-align: inherit;">的</font><font style="vertical-align: inherit;">prop特别用于包含（也称为</font></font><a href="https://reactjs.org/docs/composition-vs-inheritance.html" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">composition</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">），与</font><font style="vertical-align: inherit;">使用props的</font></font><code>React.Children</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">API和</font></font><code>React.cloneElement</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">组件</font><font style="vertical-align: inherit;">配对。</font><font style="vertical-align: inherit;">孩子可以在内部处理更多逻辑（例如状态转换，事件，DOM测量等），同时将渲染部分转换为无论在何处使用，React Router </font></font><a href="https://github.com/ReactTraining/react-router/blob/master/packages/react-router/modules/Switch.js#L38" rel="noreferrer"><code>&lt;switch/&gt;</code></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">或复合组件</font></font><a href="https://www.youtube.com/watch?v=hEGg-3pIHlE" rel="noreferrer"><code>&lt;select/&gt;</code></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">都是很好的例子。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">值得一提的最后一件事是，react元素不仅限于props.children。</font></font></p>

<pre><code>function SplitPane(props) {<font></font>
  return (<font></font>
    &lt;div className="SplitPane"&gt;<font></font>
      &lt;div className="SplitPane-left"&gt;<font></font>
        {props.left}<font></font>
      &lt;/div&gt;<font></font>
      &lt;div className="SplitPane-right"&gt;<font></font>
        {props.right}<font></font>
      &lt;/div&gt;<font></font>
    &lt;/div&gt;<font></font>
  );<font></font>
}<font></font>
<font></font>
function App() {<font></font>
  return (<font></font>
    &lt;SplitPane<font></font>
      left={<font></font>
        &lt;Contacts /&gt;<font></font>
      }<font></font>
      right={<font></font>
        &lt;Chat /&gt;<font></font>
      } /&gt;<font></font>
  );<font></font>
}<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">它们可以是任何道具是有道理的，关键是要定义部件一份不错的合同，这样它的消费者可以从底层实现细节解耦，无论它的使用</font></font><code>React.Children</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，</font></font><code>React.cloneElement</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">或甚至</font></font><code>React.createContext</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">逆天卡卡西</span>
            <span class="discuss-time">2020.03.12</span>
          </div>
          <div class="discuss-comment"><p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">编辑：</font></font></strong></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">请</font></font><a href="https://stackoverflow.com/a/50441271/1689055"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">改用Vennesa的答案</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，这是一个更好的解释。</font></font></p>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">原版的：</font></font></strong></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">首先，该</font></font><code>React.cloneElement</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">示例仅在您的孩子是单个React元素时才有效。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">几乎所有东西</font></font><code>{this.props.children}</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">都是您想要的。</font><font style="vertical-align: inherit;">克隆在某些更高级的场景中很有用，在这种情况下，父级发送一个元素，子级组件需要更改该元素上的一些道具，或添加诸如ref之类的东西来访问实际的DOM元素。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在上面的示例中，给孩子的父级不知道该组件的密钥要求，因此它创建了给定的元素的副本，并基于对象中的某些唯一标识符添加了密钥。</font><font style="vertical-align: inherit;">有关按键作用的更多信息：</font><a href="https://facebook.github.io/react/docs/multiple-components.html" rel="noreferrer"><font style="vertical-align: inherit;">https</font></a><font style="vertical-align: inherit;"> : </font></font><a href="https://facebook.github.io/react/docs/multiple-components.html" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">//facebook.github.io/react/docs/multiple-components.html</font></font></a></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">十三Stafan</span>
            <span class="discuss-time">2020.03.12</span>
          </div>
          <div class="discuss-comment"><p><code>props.children</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">不是真正的孩子吗？</font><font style="vertical-align: inherit;">是</font></font><code>descriptor</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">孩子们的。</font><font style="vertical-align: inherit;">因此，您实际上没有任何更改；</font><font style="vertical-align: inherit;">您不能更改任何道具或编辑任何功能；</font><font style="vertical-align: inherit;">你只能</font></font><code>read from it</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">如果您需要进行任何修改，则必须</font></font><code>new elements</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">使用</font><font style="vertical-align: inherit;">创建</font></font><code>React.CloneElement</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p>

<p><a href="https://egghead.io/lessons/react-use-react-cloneelement-to-extend-functionality-of-children-components" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">https://egghead.io/lessons/react-use-react-cloneelement-to-extend-functionality-of-children-components</font></font></a></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">一个例子：</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">组件的主要渲染功能，例如</font></font><code>App.js</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">：</font></font></p>

<pre><code>render() {   <font></font>
    return(<font></font>
            &lt;Paragraph&gt;<font></font>
              &lt;Sentence&gt;First&lt;/Sentence&gt;<font></font>
              &lt;Sentence&gt;Second&lt;/Sentence&gt;<font></font>
              &lt;Sentence&gt;Third&lt;/Sentence&gt;<font></font>
            &lt;/Paragraph&gt;   <font></font>
    ) <font></font>
}<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">现在假设您需要为的</font></font><code>onClick</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">每个子</font><font style="vertical-align: inherit;">项添加一个</font></font><code>Paragraph</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">；</font><font style="vertical-align: inherit;">因此，您</font></font><code>Paragraph.js</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">可以执行以下操作：</font></font></p>

<pre><code>render() {<font></font>
        return (<font></font>
          &lt;div&gt;<font></font>
          {React.Children.map(this.props.children, child =&gt; {<font></font>
            return React.cloneElement(child, {<font></font>
              onClick: this.props.onClick })   <font></font>
         })}<font></font>
         &lt;/div&gt;<font></font>
       ) <font></font>
}<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">然后只需执行以下操作： </font></font></p>

<pre><code>render() {   <font></font>
  return(<font></font>
        &lt;Paragraph onClick={this.onClick}&gt;<font></font>
          &lt;Sentence&gt;First&lt;/Sentence&gt;<font></font>
          &lt;Sentence&gt;Second&lt;/Sentence&gt;<font></font>
          &lt;Sentence&gt;Third&lt;/Sentence&gt;<font></font>
        &lt;/Paragraph&gt;   <font></font>
   ) <font></font>
}<font></font>
</code></pre>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">注：</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">该</font></font><code>React.Children.map</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">功能将只能看到</font></font><code>top level</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">的元素，它没有看到任何的东西，这些元素渲染; </font><font style="vertical-align: inherit;">表示您正在向儿童提供直接道具（此处是</font></font><code>&lt;Sentence /&gt;</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">元素）。</font><font style="vertical-align: inherit;">如果您需要进一步传递道具，假设您</font><font style="vertical-align: inherit;">要使用</font><font style="vertical-align: inherit;">道具</font></font><code>&lt;div&gt;&lt;/div&gt;</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">的</font></font><code>&lt;Sentence /&gt;</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">元素</font><font style="vertical-align: inherit;">内部有一个，</font></font><code>onClick</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">那么在这种情况下，您可以使用道具</font></font><code>Context API</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">使</font></font><code>Paragraph</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">提供者和</font></font><code>Sentence</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">元素成为消费者。</font></font></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
