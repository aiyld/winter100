---
layout: question
title:  如何在类组件中使用next.js中的“ useRouter（）”？
date:   2020-03-23T14:03:06.000Z
description: 我试图从我的url模式中获取查询，例如localhost 3000/post?loc=100通过useRouter()从“ next / router”中...
img: 
author: Gil
category: question
answer: 2
tags: JavaScript React.js
topic: React.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我试图从我的url模式中获取查询，例如</font></font><code>localhost:3000/post?loc=100</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">通过</font></font><code>useRouter()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">从“ next / router”中使用，并使用该ID从服务器中获取一些数据。</font><font style="vertical-align: inherit;">当我在无状态功能组件中使用它时，它就可以工作。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">但是页面显示“ Invalid hook call”。</font><font style="vertical-align: inherit;">我尝试调用</font></font><code>getInitalProps()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">无状态功能组件，但该组件也无法正常工作，并显示了相同的错误。</font><font style="vertical-align: inherit;">是否有使用此方法的规则？</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我正在使用React库和Next.js框架开发前端。</font></font></p>

<pre class="lang-js prettyprint-override"><code>constructor(props) {<font></font>
  this.state = {<font></font>
    loc: useRouter().query.loc,<font></font>
    loaded: false<font></font>
  };<font></font>
}<font></font>
</code></pre></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第3121篇《如何在类组件中使用next.js中的“ useRouter（）”？》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">阿飞古一A</span>
            <span class="discuss-time">2020.03.23</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">React Hooks有一个约定。</font><font style="vertical-align: inherit;">挂钩的名称以开头</font></font><code>use</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">React提供了内置的或官方的钩子，但是显然，您可以构建自己的钩子。</font></font></p>

<p><code>useRouter</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">显然是一个钩子。</font><font style="vertical-align: inherit;">您可以在功能组件中使用它。</font><font style="vertical-align: inherit;">您不能在类组件中使用它。</font><font style="vertical-align: inherit;">在功能组件内部，可以这样使用它：</font></font></p>

<pre><code><font></font>
function MyComponent(){<font></font>
   const router = useRouter();<font></font>
}<font></font>
<font></font>
</code></pre>

<p><code>withRouter</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">另一方面，由于它是HOC，因此可以在功能和类组件中使用</font></font><code>higher order component</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">但是对于类组件，您别无选择。</font><font style="vertical-align: inherit;">您必须使用</font></font><code>withRouter</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">总之，这是官方文档：
</font></font><code>To inject the pathname, query or asPath in your component, you can use the useRouter hook, or withRouter for class components.</code></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">阿飞</span>
            <span class="discuss-time">2020.03.23</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">挂钩只能在功能组件内部使用，而不能在类内部使用。</font><font style="vertical-align: inherit;">我建议</font><font style="vertical-align: inherit;">根据next.js文档</font><font style="vertical-align: inherit;">使用</font></font><a href="https://github.com/zeit/next.js/#using-a-higher-order-component" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">withRouter</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> HOC：</font></font></p>

<blockquote>
  <p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">使用</font></font><code>useRouter</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">挂钩，或</font></font><code>withRouter</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">用于类组件。</font></font></p>
</blockquote>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">或者</font></font><a href="https://reactjs.org/docs/hooks-faq.html#from-classes-to-hooks" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果要切换到挂钩，</font><font style="vertical-align: inherit;">请参阅</font><a href="https://reactjs.org/docs/hooks-faq.html#from-classes-to-hooks" rel="noreferrer"><font style="vertical-align: inherit;">从类到挂钩</font></a><font style="vertical-align: inherit;">。</font></font></p>

<p></p><hr><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">
通常，可以创建包装器功能组件，以通过prop将自定义钩子传递给类组件（但在这种情况下不可用）：</font></font><p></p>

<pre><code>const MyClassWithRouter = (props) =&gt; {<font></font>
  const router = useRouter()<font></font>
  return &lt;MyClass {...props} router={router} /&gt;<font></font>
}<font></font>
<font></font>
class MyClass...<font></font>
  constructor(props) {<font></font>
    this.state = {<font></font>
      loc: props.router.query.loc,<font></font>
      loaded: false<font></font>
    };<font></font>
  }<font></font>
</code></pre></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
