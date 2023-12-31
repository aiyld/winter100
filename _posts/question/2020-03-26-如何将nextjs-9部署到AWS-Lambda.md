---
layout: question
title:  如何将next.js 9部署到AWS Lambda
date:   2020-03-26T08:03:57.000Z
description: 我正在用next.js9开发一个项目。我有一些问题和疑问。我想将我的next.js 9项目部署到AWS lambda。next.js 9官方文档告诉...
img: 
author: 村村
category: question
answer: 2
tags: reactjs React.js
topic: React.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我正在用next.js9开发一个项目。</font><font style="vertical-align: inherit;">我有一些问题和疑问。</font><font style="vertical-align: inherit;">我想将我的next.js 9项目部署到AWS lambda。</font></font></p>

<ol>
<li><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">next.js 9官方文档告诉我“页面目录中的每个页面都变成了无服务器lambda”。</font><font style="vertical-align: inherit;">上面的库无法像doc一样工作。</font><font style="vertical-align: inherit;">如何从每个页面部署到每个lambda？</font></font></p></li>
<li><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">什么是合理的部署解决方案？</font><font style="vertical-align: inherit;">请在生产级别使用nextjs 9的人帮助我。</font></font></p></li>
<li><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我正在使用这个库</font></font><a href="https://github.com/danielcondemarin/serverless-next.js" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">https://github.com/danielcondemarin/serverless-next.js</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">运行良好。</font><font style="vertical-align: inherit;">但所有选项都是固定的。</font><font style="vertical-align: inherit;">我想将我的项目部署到东京地区。</font><font style="vertical-align: inherit;">但我不知道如何更改区域。</font><font style="vertical-align: inherit;">始终部署到弗吉尼亚州北部地区。</font><font style="vertical-align: inherit;">我已经检查过文件，但我认为他们没有选择权。</font><font style="vertical-align: inherit;">并像这样的yml文件进行测试。</font></font></p></li>
</ol>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">无服务器</font></font></p>

<pre><code>myNextApplication:<font></font>
  component: serverless-next.js<font></font>
region: ap-northeast-1<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">但它没有用。</font><font style="vertical-align: inherit;">如果有人知道如何使用serverless-next.js更改区域。</font><font style="vertical-align: inherit;">请帮我。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">先感谢您</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第3745篇《如何将next.js 9部署到AWS Lambda》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">乐西里</span>
            <span class="discuss-time">2020.03.26</span>
          </div>
          <div class="discuss-comment"><ol>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我还没主意</font></font></li>
</ol>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">2，3。</font><font style="vertical-align: inherit;">serverless-next.js是有一定理由的。</font><font style="vertical-align: inherit;">我发出了问题github。</font><font style="vertical-align: inherit;">贡献者回答我如下。</font><font style="vertical-align: inherit;">我了解框架的概念。</font></font></p>

<p><a href="https://github.com/danielcondemarin/serverless-next.js#my-lambda-is-deployed-to-us-east-1-how-can-i-deploy-it-to-another-region" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">https://github.com/danielcondemarin/serverless-next.js#my-lambda-is-deployed-to-us-east-1-how-can-i-deploy-it-to-another-region</font></font></a></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">神无泡芙</span>
            <span class="discuss-time">2020.03.26</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">有一个webpack插件，可以帮助</font></font><a href="https://github.com/vincent-herlemont/next-aws-lambda-webpack-plugin" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">next-aws-lambda-webpack-plugin</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p>

<ol>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">该插件为每个页面生成一个目录，</font></font><a href="https://nextjs.org/docs/api-reference/next.config.js/build-target#server-target" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">其中包含Next.JS的无服务器代码</font></font></a> </li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">此插件不使用</font></font><a href="https://serverless.com/" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">无服务器框架，</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">因此您可以将本机AWS部署解决方案用于基础架构，例如：</font></font><a href="https://aws.amazon.com/serverless/sam/" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">AWS SAM</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">或</font></font><a href="https://aws.amazon.com/fr/cloudformation/" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">AWS cloudformation</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">进行部署，并从AWS支持中受益。</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">借助AWS本机解决方案部署，您可以自由选择任何需要的区域。</font></font></li>
</ol></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
