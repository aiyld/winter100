---
layout: question
title:  Next.js，getInitialProps不起作用
date:   2020-03-26T08:02:16.000Z
description: 当页面第一次在服务器站点上呈现或刷新呈现的页面时，getInitialProps不起作用：Home.getInitialProps = async (...
img: 
author: LEvaGreen
category: question
answer: 0
tags: JavaScript React.js
topic: React.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">当页面第一次在服务器站点上呈现或刷新呈现的页面时，getInitialProps不起作用：</font></font></p>

<pre><code>Home.getInitialProps = async ({store}) =&gt; {<font></font>
    axios.post('/user').then(res =&gt; {<font></font>
        var user = res.data;<font></font>
        store.dispatch(setLoggingState(user));<font></font>
    }, res =&gt; {<font></font>
        console.log('4444');<font></font>
    })<font></font>
    return {};<font></font>
}<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在以上代码中，服务器始终打印“ 4444”，而快递未收到“ POST”请求。</font><font style="vertical-align: inherit;">坦克为您提供帮助</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第3739篇《Next.js，getInitialProps不起作用》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    
    </div>
    {% endraw %}
  </div>
<div>
