---
layout: question
title:  如何撰写next.config.js文件
date:   2020-03-24T03:15:55.000Z
description: 我正在尝试为我的下一个应用程序添加sass支持和webpack图像加载器，以及对导出路由的支持。我在如何撰写配置文件时遇到问题。我不明白sass插件如何添...
img: 
author: LEY小卤蛋
category: question
answer: 1
tags: JavaScript React.js
topic: React.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我正在尝试为我的下一个应用程序添加sass支持和webpack图像加载器，以及对导出路由的支持。</font><font style="vertical-align: inherit;">我在如何撰写配置文件时遇到问题。</font><font style="vertical-align: inherit;">我不明白sass插件如何添加到webpack配置中，以及如何编写和导出next.config.js函数。</font></font></p>

<pre><code>const fetch = require('isomorphic-unfetch');<font></font>
var Prismic = require('prismic-javascript');<font></font>
const withSass = require('@zeit/next-sass')<font></font>
<font></font>
var apiEndpoint = 'https://apiendpoint/api/v2';<font></font>
<font></font>
module.exports =<font></font>
<font></font>
withSass({<font></font>
    async exportPathMap() {<font></font>
<font></font>
  const response = await Prismic.getApi(apiEndpoint)<font></font>
    .then(function (api) {<font></font>
      return api.query(<font></font>
        Prismic.Predicates.at('document.type', 'post')<font></font>
      );<font></font>
    })<font></font>
    .then(<font></font>
      function (response) {<font></font>
        return response.results<font></font>
      },<font></font>
      function (err) {<font></font>
        console.log('Something went wrong: ', err);<font></font>
      }<font></font>
    );<font></font>
<font></font>
  // tranform the list of posts into a map of pages with the pathname `/post/:id`<font></font>
  const pages = await response.reduce((pages, post) =&gt;<font></font>
<font></font>
    Object.assign({}, pages, {<font></font>
      [`/post/${post.id}`]: {<font></font>
        page: '/post',<font></font>
        query: {<font></font>
          id: post.id<font></font>
        }<font></font>
      }<font></font>
    }), {},<font></font>
<font></font>
  )<font></font>
<font></font>
<font></font>
  // combine the map of post pages with the home<font></font>
  return Object.assign({}, pages, {<font></font>
    '/': {<font></font>
      page: '/'<font></font>
    }<font></font>
  })<font></font>
 }<font></font>
})<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">有人可以帮忙吗？</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第3296篇《如何撰写next.config.js文件》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">伽罗理查德</span>
            <span class="discuss-time">2020.03.24</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这是一个古老的问题，但是看到人们正在搜索这个问题时，我认为我应该发布答案。</font><font style="vertical-align: inherit;">我建议使用</font></font><a href="https://github.com/cyrilwanner/next-compose-plugins" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">https://github.com/cyrilwanner/next-compose-plugins</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这是一个非常简单的API，而且更加干净。</font><font style="vertical-align: inherit;">希望这可以帮助。</font></font></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
