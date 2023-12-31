---
layout: question
title:  React.createElement：类型无效-预期为字符串
date:   2020-03-13T07:36:08.000Z
description: 试图使react-router（v4.0.0）和react-hot-loader（3.0.0-beta.6）正常播放，但是在浏览器控制台中出现以下错误：...
img: 
author: LEY古一阿飞
category: question
answer: 12
tags: reactjs React.js
topic: React.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">试图使react-router（v4.0.0）和react-hot-loader（3.0.0-beta.6）正常播放，但是在浏览器控制台中出现以下错误：</font></font></p>

<blockquote>
  <p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">警告：React.createElement：类型无效-预期为字符串（对于内置组件）或类/函数（对于复合组件），但得到：未定义。</font><font style="vertical-align: inherit;">您可能忘记了从定义文件中导出组件。</font></font></p>
</blockquote>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">index.js：</font></font></p>

<pre><code>import React from 'react';<font></font>
import ReactDom from 'react-dom';<font></font>
import routes from './routes.js';<font></font>
require('jquery');<font></font>
import 'bootstrap/dist/css/bootstrap.min.css';<font></font>
import 'bootstrap/dist/js/bootstrap.min.js';<font></font>
import './css/main.css';<font></font>
<font></font>
const renderApp = (appRoutes) =&gt; {<font></font>
    ReactDom.render(appRoutes, document.getElementById('root'));<font></font>
};<font></font>
<font></font>
renderApp( routes() );<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">route.js：</font></font></p>

<pre><code>import React from 'react';<font></font>
import { AppContainer } from 'react-hot-loader';<font></font>
import { Router, Route, browserHistory, IndexRoute } from 'react-router';<font></font>
import store from './store/store.js';<font></font>
import { Provider } from 'react-redux';<font></font>
import App from './containers/App.jsx';<font></font>
import Products from './containers/shop/Products.jsx';<font></font>
import Basket from './containers/shop/Basket.jsx';<font></font>
<font></font>
const routes = () =&gt; (<font></font>
<font></font>
    &lt;AppContainer&gt;<font></font>
        &lt;Provider store={store}&gt;<font></font>
            &lt;Router history={browserHistory}&gt;<font></font>
                &lt;Route path="/" component={App}&gt;<font></font>
                    &lt;IndexRoute component={Products} /&gt;<font></font>
                    &lt;Route path="/basket" component={Basket} /&gt;<font></font>
                &lt;/Route&gt;<font></font>
            &lt;/Router&gt;<font></font>
        &lt;/Provider&gt;<font></font>
    &lt;/AppContainer&gt;<font></font>
<font></font>
);<font></font>
<font></font>
export default routes;<font></font>
</code></pre></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第1395篇《React.createElement：类型无效-预期为字符串》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">西里Mandy</span>
            <span class="discuss-time">2020.03.13</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我收到此错误，但我的情况没有一个答案，它可能有助于谷歌搜索：</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我定义了一个Proptype错误：</font></font></p>

<pre><code>ids: PropTypes.array(PropTypes.string)
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">它应该是：</font></font></p>

<pre><code>ids: PropTypes.arrayOf(PropTypes.string)
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">VSCode和编译错误没有给我正确的提示。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">L理查德</span>
            <span class="discuss-time">2020.03.13</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这是一些必须调试的错误。</font><font style="vertical-align: inherit;">正如许多次所说的，不正确的导入/导出会导致此错误，但是令人惊讶的</font></font><code>react-router-dom authentication setup</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">是</font><font style="vertical-align: inherit;">，我</font><font style="vertical-align: inherit;">是</font><font style="vertical-align: inherit;">从</font><font style="vertical-align: inherit;">下面的</font><font style="vertical-align: inherit;">一个小错误中得到此错误的</font><font style="vertical-align: inherit;">：</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">错误设置：</font></font></p>

<pre><code>const PrivateRoute = ({ component: Component, ...rest }) =&gt; (<font></font>
    &lt;Route<font></font>
        {...rest}<font></font>
        render={(props) =&gt; (token ? &lt;Component {...props} /&gt; : &lt;Redirect to={{ pathname: "/login" }} /&gt;)}<font></font>
    /&gt;<font></font>
);<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">正确的设置：</font></font></p>

<pre><code>const PrivateRoute = ({ component: Component, token, ...rest }) =&gt; (<font></font>
    &lt;Route<font></font>
        {...rest}<font></font>
        render={(props) =&gt; (token ? &lt;Component {...props} /&gt; : &lt;Redirect to={{ pathname: "/login" }} /&gt;)}<font></font>
    /&gt;<font></font>
);<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">唯一的区别是我是解构</font></font><code>token</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">的</font></font><code>PrivateRoute component</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">令牌从得到的方式</font></font><code>localstorage</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">是这样</font></font><code>const token = localStorage.getItem("authUser");</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，所以如果它不存在，我知道该用户未通过身份验证。</font><font style="vertical-align: inherit;">这也会导致该错误。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">神奇启人</span>
            <span class="discuss-time">2020.03.13</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">循环依赖也是原因之一。</font><font style="vertical-align: inherit;">[一般来说]</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">猿神奇</span>
            <span class="discuss-time">2020.03.13</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">就我而言，尝试使用ContextApi时发生了错误。</font><font style="vertical-align: inherit;">我误用了：</font></font></p>

<pre><code>const MyContext = () =&gt; createContext()
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">但这应该定义为：</font></font></p>

<pre><code>const MyContext = createContext()
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我将其张贴在这里，以便将来因此类愚蠢错误而卡住的访客将有助于避免数小时的头痛，因为这不是由错误的进出口引起的。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Tony飞云</span>
            <span class="discuss-time">2020.03.13</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">就我而言，我只需要从升级到</font></font><code>react-router-redux</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">即可</font></font><code>react-router-redux@next</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">我假设它一定是某种兼容性问题。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">逆天伽罗宝儿</span>
            <span class="discuss-time">2020.03.13</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我错过了一个</font></font><a href="https://reactjs.org/docs/fragments.html" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">React Fragment</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">：</font></font></p>

<pre class="lang-js prettyprint-override"><code><font></font>
function Bar({ children }) {<font></font>
<font></font>
  return (<font></font>
    &lt;div&gt;<font></font>
     {children}<font></font>
    &lt;/div&gt;<font></font>
  );<font></font>
}<font></font>
<font></font>
function Foo() {<font></font>
  return (<font></font>
    &lt;Bar&gt;<font></font>
      &lt;Baz/&gt;<font></font>
      &lt;Qux/&gt;<font></font>
    &lt;/Bar&gt;<font></font>
  );<font></font>
}<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">上面的代码抛出上面的错误。</font><font style="vertical-align: inherit;">但这解决了：</font></font></p>

<pre class="lang-js prettyprint-override"><code>&lt;Bar&gt;<font></font>
  &lt;&gt;<font></font>
    &lt;Baz/&gt;<font></font>
    &lt;Qux/&gt;<font></font>
  &lt;/&gt;<font></font>
&lt;/Bar&gt;<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">理查德村村小宇宙</span>
            <span class="discuss-time">2020.03.13</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">简而言之，以下情况正在发生：</font></font></p>

<pre><code>render() {<font></font>
    return (<font></font>
        &lt;MyComponent /&gt; // MyComponent is undefined.<font></font>
    );<font></font>
}<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">它可能不一定与某些不正确的导入或导出有关：</font></font></p>

<pre><code>render() {<font></font>
    // MyComponent may be undefined here, for example.<font></font>
    const MyComponent = this.wizards[this.currentStep];<font></font>
<font></font>
    return (<font></font>
        &lt;MyComponent /&gt;<font></font>
    );<font></font>
}<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">村村AL</span>
            <span class="discuss-time">2020.03.13</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">就我而言，我忘记了导入和导出index.js文件中的render调用的（新）元素。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">小胖泡芙</span>
            <span class="discuss-time">2020.03.13</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">就我而言，创建组件和渲染的顺序很重要。</font><font style="vertical-align: inherit;">我在创建组件之前就对其进行了渲染。</font><font style="vertical-align: inherit;">最好的方法是先创建子组件，再创建父组件，然后渲染父组件。</font><font style="vertical-align: inherit;">更改订单对我来说解决了这个问题。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">村村小小十三</span>
            <span class="discuss-time">2020.03.13</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我认为解决此错误时最重要的事情是，当您尝试实例化一个不存在的组件时，它就会显现出来。</font><font style="vertical-align: inherit;">该组件不必导入。</font><font style="vertical-align: inherit;">就我而言，我将组件作为属性传递。</font><font style="vertical-align: inherit;">在进行一些重构后，我忘记更新其中一个调用以正确传递组件。</font><font style="vertical-align: inherit;">不幸的是，由于JS不是静态类型的，所以没有捕获到我的错误，并且花了一些时间才弄清楚发生了什么。  </font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">要解决此错误，请在渲染组件之前检查组件，以确保它是您期望的组件类型。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">GO村村</span>
            <span class="discuss-time">2020.03.13</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">对于未来的Google员工：</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我对这个问题的解决办法是升级</font></font><code>react</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">和</font></font><code>react-dom</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">对新公共管理的最新版本。</font><font style="vertical-align: inherit;">显然我正在导入使用</font></font><a href="https://reactjs.org/blog/2017/11/28/react-v16.2.0-fragment-support.html" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">新片段语法</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">的Component，</font><font style="vertical-align: inherit;">并且在我的旧版React中</font><font style="vertical-align: inherit;">已将</font><font style="vertical-align: inherit;">其破坏。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">十三Stafan</span>
            <span class="discuss-time">2020.03.13</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">当我在渲染/返回语句中引用错误时，就发生了这个问题。</font><font style="vertical-align: inherit;">（指向不存在的类）。</font><font style="vertical-align: inherit;">还要检查您的退货声明代码是否有错误的引用。</font></font></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
