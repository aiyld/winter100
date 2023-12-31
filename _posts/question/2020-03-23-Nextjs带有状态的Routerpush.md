---
layout: question
title:  Next.js：带有状态的Router.push
date:   2020-03-23T06:40:50.000Z
description: 我正在使用next.js重建用于服务器端渲染的应用程序。我有一个处理搜索请求的按钮。在旧的应用程序中，处理程序是这样的：search = (eve...
img: 
author: 西门
category: question
answer: 0
tags: JavaScript React.js
topic: React.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我正在使用next.js重建用于服务器端渲染的应用程序。</font><font style="vertical-align: inherit;">我有一个处理搜索请求的按钮。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在旧的应用程序中，处理程序是这样的：</font></font></p>

<pre><code>search = (event) =&gt; {<font></font>
    event.preventDefault();<font></font>
    history.push({<font></font>
        pathname: '/results',<font></font>
        state: {<font></font>
            pattern: this.state.searchText,<font></font>
        }<font></font>
    });<font></font>
}<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在结果类中，我可以使用this.props.location.state.pattern获取状态日期。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">所以现在我正在使用next.js：</font></font></p>

<pre><code>import Router, { withRouter } from 'next/router'<font></font>
<font></font>
performSearch = (event) =&gt; {<font></font>
    event.preventDefault();<font></font>
    Router.push({ pathname: '/results', state: { pattern: this.state.searchText } });<font></font>
};<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在结果类中，我使用 </font></font></p>

<pre><code>static async getInitialProps({req}) {<font></font>
    return req.params;<font></font>
}<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我不确定是否必须将其添加到我的server.js中：</font></font></p>

<pre><code>server.get('/results', (req, res) =&gt; {<font></font>
    return app.render(req, res, '/results', req.params)<font></font>
})<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">但是，由于未定义req，因此函数getInitialProps引发错误。</font><font style="vertical-align: inherit;">长文本，简短问题：如何在不使用GET参数的情况下将状态或参数传递给另一个页面？</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第2858篇《Next.js：带有状态的Router.push》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    
    </div>
    {% endraw %}
  </div>
<div>
