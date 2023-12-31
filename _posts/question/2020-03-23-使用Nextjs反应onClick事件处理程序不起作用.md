---
layout: question
title:  使用Next.js反应onClick事件处理程序不起作用
date:   2020-03-23T06:40:09.000Z
description: 我正在制作Reddit克隆，并且正在使用Next.js，以便呈现其服务器端。我开始时没有使用Next.js，当我了解了它之后，我立即切换到了它。我创建...
img: 
author: 猴子
category: question
answer: 1
tags: JavaScript React.js
topic: React.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我正在制作Reddit克隆，并且正在使用Next.js，以便呈现其服务器端。</font><font style="vertical-align: inherit;">我开始时没有使用Next.js，当我了解了它之后，我立即切换到了它。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我创建了一个自定义，</font></font><code>_app.js</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">以便页眉和侧边栏出现在每个页面上，并且它充当保持应用程序状态的最顶层组件。</font><font style="vertical-align: inherit;">后来还不太行。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这里是</font></font><code>.project/src/pages/_app.js</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">：</font></font></p>

<pre><code>import App, { Container } from 'next/app';<font></font>
<font></font>
// Components<font></font>
import Header from '../components/Header/Header';<font></font>
<font></font>
const MainLayout = props =&gt; (<font></font>
  &lt;React.Fragment&gt;<font></font>
    &lt;Header<font></font>
      isSidebarOpen={props.isSidebarOpen}<font></font>
      sidebarToggle={props.sidebarToggle}<font></font>
    /&gt;<font></font>
    {props.children}<font></font>
  &lt;/React.Fragment&gt;<font></font>
);<font></font>
<font></font>
export default class MyApp extends App {<font></font>
  static async getInitialProps({ Component, router, ctx }) {<font></font>
    let pageProps = {};<font></font>
<font></font>
    if (Component.getInitialProps) {<font></font>
      pageProps = await Component.getInitialProps(ctx);<font></font>
    }<font></font>
<font></font>
    return { pageProps };<font></font>
  }<font></font>
<font></font>
  state = {<font></font>
    isSidebarOpen: true<font></font>
  };<font></font>
<font></font>
  sidebarToggle = () =&gt; {<font></font>
    this.setState({ isSidebarOpen: !this.state.isSidebarOpen });<font></font>
  };<font></font>
<font></font>
  render() {<font></font>
    const { Component, pageProps } = this.props;<font></font>
    return (<font></font>
      &lt;Container&gt;<font></font>
        &lt;MainLayout<font></font>
          isSidebarOpen={this.state.isSidebarOpen}<font></font>
          sidebarToggle={this.sidebarToggle}<font></font>
        &gt;<font></font>
          &lt;Component {...pageProps} /&gt;<font></font>
        &lt;/MainLayout&gt;<font></font>
      &lt;/Container&gt;<font></font>
    );<font></font>
  }<font></font>
}<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我遇到的问题是，</font></font><code>isSidebarOpen</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">和</font></font><code>sidebarToggle</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">被传递到正是我需要他们-他们在控制台中显示出来-但onClick处理常式的不激活，如果我的变化</font></font><code>isSidebarOpen</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，直到我重新启动服务器不生效。</font><font style="vertical-align: inherit;">在使用Next.js之前，我曾使用过这种方法，并且按预期工作。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我如何才能实现自己的目标？</font><font style="vertical-align: inherit;">我已经阅读了文档，搜索了Google和Stack Overflow。</font><font style="vertical-align: inherit;">我什至没有运气就检查了他们回购中的问题。</font><font style="vertical-align: inherit;">我怀疑这与风俗有关</font></font><code>_app.js</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，因为道具正确地传递了下来。</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第2856篇《使用Next.js反应onClick事件处理程序不起作用》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Gil伽罗小宇宙</span>
            <span class="discuss-time">2020.03.23</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">一种可能是</font></font><code>sidebarToggle</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在正在使用的组件中</font><font style="vertical-align: inherit;">定义</font><font style="vertical-align: inherit;">函数（可能是因为在Component内部调用该函数，代码可能在_app.js中而不是您的组件中运行，这可能很大！但是值得一试）</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这</font></font><code>_app.js</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">是应用程序的包装，我认为它不适合用于最顶层的组件来保持状态。</font><font style="vertical-align: inherit;">最好使一个简单的反应根组件做到这一点！</font></font></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
