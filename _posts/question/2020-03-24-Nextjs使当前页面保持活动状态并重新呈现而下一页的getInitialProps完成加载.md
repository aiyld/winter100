---
layout: question
title:  Next.js使当前页面保持活动状态并重新呈现，而下一页的getInitialProps完成加载
date:   2020-03-24T02:10:26.000Z
description: 场景是这样的：在一页（AssessmentListPage）中，我显示了现有评估的列表；在第二页（AssessmentDetailPage）中，我将...
img: 
author: Gil
category: question
answer: 0
tags: reactjs React.js
topic: React.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">场景是这样的：</font></font></p>

<ol>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在一页（</font></font><code>AssessmentListPage</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">）中，我显示了现有评估的列表；</font><font style="vertical-align: inherit;">在第二页（</font></font><code>AssessmentDetailPage</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">）中，我将显示所选评估的详细信息；</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我正在使用redux，并且两个页面都使用相同的slice操作系统状态（</font></font><code>assessments</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">）</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">当我从</font></font><code>AssessmentListPage</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">转到时</font></font><code>AssessmentDetailPage</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，一切正常。</font><font style="vertical-align: inherit;">当我按下后退按钮时，它崩溃了。</font></font></li>
<li><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">崩溃的原因</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">：Next.js使</font></font><code>AssessmentDetailPage</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">页面</font><font style="vertical-align: inherit;">保持</font><font style="vertical-align: inherit;">活动状态，直到</font></font><code>static getInitialProps</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">方法完成。</font><font style="vertical-align: inherit;">被调用的操作会更改状态，并导致当前页面在没有预期数据的情况下重新呈现。</font><font style="vertical-align: inherit;">然后它会</font></font><code>AssessmentListPage</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">正确</font><font style="vertical-align: inherit;">呈现</font><font style="vertical-align: inherit;">。</font></font></li>
</ol>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">解决这个问题的最优雅的方法是什么？</font><font style="vertical-align: inherit;">我应该分离减速器吗？</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">目前，我只是更具防御性，并添加了通常不需要避免此特定崩溃的检查。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我还考虑过不要在中加载数据</font></font><code>getInitialProps</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">并这样做，</font></font><code>componentDidMount()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">但是我不喜欢复制代码来处理服务器端和客户端渲染的想法。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">任何建议深表感谢。</font><font style="vertical-align: inherit;">谢谢！</font></font></p>

<pre><code>class AssessmentListPage extends React.Component {<font></font>
  static async getInitialProps({ store, req }) {<font></font>
    await store.dispatch(loadProfile(api)(req))<font></font>
    await store.dispatch(loadAssessments(api)(req))<font></font>
  }<font></font>
}<font></font>
<font></font>
class AssessmentDetailPage extends React.Component {<font></font>
  static async getInitialProps({ store, req }) {<font></font>
    await store.dispatch(loadProfile(api)(req))<font></font>
    await store.dispatch(loadAssessment(api)(req, query.id))<font></font>
  }<font></font>
}<font></font>
</code></pre></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第3217篇《Next.js使当前页面保持活动状态并重新呈现，而下一页的getInitialProps完成加载》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    
    </div>
    {% endraw %}
  </div>
<div>
