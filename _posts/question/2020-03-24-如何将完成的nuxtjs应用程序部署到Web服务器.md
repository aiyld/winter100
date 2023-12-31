---
layout: question
title:  如何将完成的nuxt.js应用程序部署到Web服务器？
date:   2020-03-24T06:41:28.000Z
description: 在工作中，我对nuxtjs开发有一些了解，并对它非常感兴趣。因此，我开始自己进行一些开发，但是现在，我坚持完成的项目。为了进行开发，我在CLI中使用“...
img: 
author: 西门Davaid
category: question
answer: 2
tags: vue.js Vue.js
topic: Vue.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在工作中，我对nuxtjs开发有一些了解，并对它非常感兴趣。</font><font style="vertical-align: inherit;">因此，我开始自己进行一些开发，但是现在，我坚持完成的项目。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">为了进行开发，我在CLI中使用“ npm run dev”启动了本地服务器。</font><font style="vertical-align: inherit;">这一切都很好。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">但是，如何在家庭服务器上部署我现在完成的项目，以使其在类似nginx的环境中运行（或者在Windows Server环境中运行更好的替代方法）？</font><font style="vertical-align: inherit;">我听说在CLI中有“ npm run build”的信息，但是除此之外的程序又如何呢？</font><font style="vertical-align: inherit;">该命令甚至是正确的方法吗？</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我绝对是这个部门的菜鸟。</font><font style="vertical-align: inherit;">有人可以教我逐步进行“生产”该做什么吗？</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">首先十分感谢！</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">最高</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">当然，“ npm run dev”对于生产而言不是可行的选择。</font><font style="vertical-align: inherit;">只能从运行服务器的计算机上访问它。</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第3400篇《如何将完成的nuxt.js应用程序部署到Web服务器？》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">泡芙达蒙</span>
            <span class="discuss-time">2020.03.24</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这个问题没有答案，主要的变量是，您要部署静态应用程序还是通用（ssr）应用程序，以及要在何处托管它。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">正如评论和其他答案中所建议的那样，静态应用程序非常简单，但是您可能有一个SSR应用程序，需要进行部署。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">该</font></font><a href="https://nuxtjs.org/faq/deployment-aws-s3-cloudfront" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">文档</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">详细介绍了如何部署到一系列托管服务提供商，以及有关使用nginx的知识。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">有一个</font></font><a href="https://kaloraat.com/articles/how-to-deploy-nuxtjs-ssr-app-to-digital-ocean" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">教程</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">可以部署到数字海洋。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">一些托管提供商比其他托管提供商更容易，实际上提供托管CLI的托管提供商通常更容易。</font><font style="vertical-align: inherit;">因此，Heroku和Now和Netlify都是不错的选择，但后两者仅适用于静态应用程序。</font><font style="vertical-align: inherit;">文档说“ AWS裁员了1000张纸”，所以我想这并不容易。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">因此，您应该检查一下托管选项，然后选择一个，尝试并遵循nuxt文档进行部署，如果遇到麻烦，请在此处询问其他有关具体问题。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">宝儿</span>
            <span class="discuss-time">2020.03.24</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">最简单的方法-您需要生成所有内容：</font></font></p>

<ol>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">运行</font></font><code>npm run generate</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">转到</font></font><code>dist</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">项目</font><font style="vertical-align: inherit;">的</font><font style="vertical-align: inherit;">子文件夹，然后将所有内容都复制到一些公共托管中，例如GitHub Pages。</font></font></li>
</ol>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">尽管如果您有一些内容取决于用户，则需要将其部署为SPA：</font></font></p>

<ol>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">改变</font></font><code>mode</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在</font></font><code>nuxt.config.js</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">给</font></font><code>spa</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">运行</font></font><code>npm run build</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">将创建的</font></font><code>dist/</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">文件夹</font><font style="vertical-align: inherit;">部署</font><font style="vertical-align: inherit;">到Surge，GitHub Pages或nginx等静态主机。</font></font></li>
</ol>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">更多细节： </font></font></p>

<p><a href="https://nuxtjs.org/guide/commands#static-generated-deployment-pre-rendered-" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">https://nuxtjs.org/guide/commands#static-generation-deployment-pre-rendered-</font></font></a></p>

<p><a href="https://nuxtjs.org/faq/github-pages#how-to-deploy-on-github-pages-" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">https://nuxtjs.org/faq/github-pages#how-to-deploy-on-github-pages-</font></font></a></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
