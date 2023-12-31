---
layout: question
title:  如何设置ASP.NET Core + Vue.js？
date:   2020-03-11T03:10:49.000Z
description: 我需要将Vue.js与一些ASP.NET Core MVC视图集成在一起。他们说，我选择Vue.js而不是其他选择，是因为它似乎更简单-“ 只需通过<sc...
img: 
author: 神无伽罗阳光
category: question
answer: 6
tags: JavaScript
topic: JavaScript
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我需要将Vue.js与一些ASP.NET Core MVC视图集成在一起。</font><font style="vertical-align: inherit;">他们说，</font><font style="vertical-align: inherit;">我选择Vue.js而不是其他选择，是因为它似乎更简单-“ </font></font><em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">只需通过</font></font><code>&lt;script&gt;</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">标签添加</font></font></em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> ”即可。</font><font style="vertical-align: inherit;">无需学习Gulp / Grunt / Webpack / Browserify / etc。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">事实证明这是错误的。</font><font style="vertical-align: inherit;">在我第一次尝试处理日期时，我尝试了一些扩展名，例如</font></font><a href="https://github.com/brockpetrie/vue-moment" rel="nofollow noreferrer"><code>vue-moment</code></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">和</font></font><a href="https://github.com/Haixing-Hu/vue-datetime-picker" rel="nofollow noreferrer"><code>vue-datetime-picker</code></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，</font><font style="vertical-align: inherit;">这些扩展名</font><font style="vertical-align: inherit;">来自</font></font><a href="https://github.com/vuejs/awesome-vue" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">与Vue.js相关的</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">官方</font><a href="https://github.com/vuejs/awesome-vue" rel="nofollow noreferrer"><font style="vertical-align: inherit;">精选列表，</font></a><font style="vertical-align: inherit;">但在这里遇到了</font><a href="https://github.com/vuejs/awesome-vue" rel="nofollow noreferrer"><font style="vertical-align: inherit;">麻烦</font></a><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">虽然第一个没有</font></font><code>require()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">强制</font><font style="vertical-align: inherit;">使用</font><font style="vertical-align: inherit;">JS语法（CommonJS？），但是第二个没有它就无法工作。</font></font><code>'use babel'</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">和</font></font><code>imports</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">/的</font><font style="vertical-align: inherit;">其他扩展</font></font><code>exports</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">是ECMAScript 6，需要进行</font><font style="vertical-align: inherit;">扩展</font><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">因此，大多数Vue.js库和工具确实需要编译器，</font></font><code>require()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">语法以及Node领域的所有东西吗？</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我应该如何设置我的项目以与ASP.NET Core MVC + Vue.js一起工作，以便可以使用Vue插件开发许多小型Vue应用程序（可以</font></font><code>require(stuff)</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">）？</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第587篇《如何设置ASP.NET Core + Vue.js？》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">樱西里猴子</span>
            <span class="discuss-time">2020.03.11</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我花了很长时间学习如何使用Browserify和Babel，以便可以设置自己的ES6环境。</font><font style="vertical-align: inherit;">但是，在使用Vue时，我很高兴使用默认模板，最好通过安装</font></font><a href="https://github.com/vuejs/vue-cli" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Vue-CLI来</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">访问它们</font><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">您可以在Browserify和Webpack之间进行选择，也可以使用仅运行时版本进行简单设置或完整使用lint，单元测试和Single-File Components。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">它只是工作。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">神乐米亚</span>
            <span class="discuss-time">2020.03.11</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这个问题有点老了，但是..</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我在</font></font><a href="https://github.com/pimboden/Web12VueAspx" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">GitHub上</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">有一个</font><font style="vertical-align: inherit;">使用ASP.NET和Vue.js </font><font style="vertical-align: inherit;">的小示例项目。</font><font style="vertical-align: inherit;">它使用Yarn（或npm）作为程序包管理器和Webpack。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">它不是.NET Core，但使用方式相同。</font><font style="vertical-align: inherit;">它可能会帮助您入门。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">奇怪的文件结构是因为它在我们的Sitecore CMS系统上运行。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">希望能帮助到你。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">神无Harry</span>
            <span class="discuss-time">2020.03.11</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">此处提供了将Vue.js与ASP.NET Core集成的最佳分步教程：</font></font></p>

<p><a href="https://ourtechroom.com/tech/integrating-vuejs-in-aspnetcore-application/" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">https://ourtechroom.com/tech/integrating-vuejs-in-aspnetcore-application/</font></font></a></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我在这里发布了一个GitHub示例项目：</font></font></p>

<p><a href="https://github.com/Diwas777/integrating-vue-with-asp.net-core-project" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">https://github.com/Diwas777/integrating-vue-with-asp.net-core-project</font></font></a></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">卡卡西猪猪</span>
            <span class="discuss-time">2020.03.11</span>
          </div>
          <div class="discuss-comment"><p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">首先，免责声明：我找不到任何真正适合我需要的东西，因此我从头开始提出了一个解决方案。</font><font style="vertical-align: inherit;">见末。</font></font></strong></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您询问是否要通过</font></font><code>&lt;script&gt;</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">标记</font><font style="vertical-align: inherit;">包含Vue </font><font style="vertical-align: inherit;">（在这种情况下为CDN构建）。</font><font style="vertical-align: inherit;">但是，您还提到使用Babel和ES6模块功能。</font><font style="vertical-align: inherit;">在那种情况下，我建议将Webpack用于客户端应用程序，它将使用Babel编译ES6，允许您使用模块和组件，并使用模板！</font><font style="vertical-align: inherit;">您还将获得热模块重新加载（编辑源代码并实时查看客户端应用程序中的更改！），Webpack将SPA捆绑到静态HTML5应用程序中。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">官方的Vue.js文档指向</font></font><a href="https://vuejs.org/v2/guide/installation.html#CLI" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">他们自己的Webpack模板</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">所以，你</font></font><em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">可以</font></font></em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">独立运行的WebPack开发服务器和你的ASP.NET应用程序的核心，如果适合您的需求，但有一个更好的解决方案，使发展更加精简：</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Microsoft的开源</font></font><a href="https://github.com/aspnet/JavaScriptServices" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">JavaScriptServices</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">允许您从ASP.NET Core执行Node.js，并且它们具有一些Webpack中间件，该中间件在调试构建期间将Webpack开发服务器集成到您的应用程序中。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">他们提供了Angular 2的官方模板，甚至提供了标有Vue.js的模板，但是Vue模板只是官方的Webpack模板，没有与.NET集成。</font><font style="vertical-align: inherit;">这就像独立服务器一样。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我找不到为Vue.js做到这一点的任何模板，因此我将一个示例ASP.NET Core应用程序放在一起，该应用程序将Webpack开发中间件与Vue.js Webpack应用程序一起加载。</font><font style="vertical-align: inherit;">当.NET Core服务器在开发模式下运行时，您可以编辑Vue源，并且更改将通过快速增量补丁反映出来，而无需重建整个应用程序。</font><font style="vertical-align: inherit;">在发布模式下，.NET Core将使用预构建的Webpack输出。</font><font style="vertical-align: inherit;">您可以在GitHub上找到它：</font></font></p>

<p><a href="https://github.com/0xFireball/YetAnotherShrinker" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">https://github.com/0xFireball/YetAnotherShrinker</font></font></a></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">上面链接的存储库具有使用NancyFx，axios，Vue.js和Vue Material的完整应用程序演示，并且是一个简单的URL缩短器。</font><font style="vertical-align: inherit;">如果您想要更简单的设置步骤，并且可以轻松将其添加到现有应用中，请查看</font></font><a href="https://blog.iridiumion.xyz/tutorials/2016/12/13/aspnetcore-vuejs-2/" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我的博客文章</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">强制性披露：我写了该博客文章。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">西门泡芙Jim</span>
            <span class="discuss-time">2020.03.11</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我创建了将</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">.NET MVC</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">与</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Vue.js</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">结合在一起的模板</font><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">您可以使用整个Vue生态系统，但是如果您不想在任何页面上使用它，都可以选择退出。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">GitHub：</font><a href="https://github.com/danijelh/aspnetcore-vue-typescript-template" rel="nofollow noreferrer"><font style="vertical-align: inherit;">https</font></a><font style="vertical-align: inherit;"> : </font></font><a href="https://github.com/danijelh/aspnetcore-vue-typescript-template" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">//github.com/danijelh/aspnetcore-vue-typescript-template</font></font></a></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">媒介：</font><a href="https://medium.com/@danijelhdev/multi-page-net-core-with-vue-js-typescript-vuex-vue-router-bulma-sass-and-webpack-4-efc7de83fea4" rel="nofollow noreferrer"><font style="vertical-align: inherit;">https</font></a><font style="vertical-align: inherit;">：</font></font><a href="https://medium.com/@danijelhdev/multi-page-net-core-with-vue-js-typescript-vuex-vue-router-bulma-sass-and-webpack-4-efc7de83fea4" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">//medium.com/@danijelhdev/multi-page-net-core-with-vue-js-typescript-vuex-vue-router-bulma-sass-and-webpack-4-efc7de83fea4</font></font></a></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您可以将其用作示例或起点。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Davaid阳光小卤蛋</span>
            <span class="discuss-time">2020.03.11</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我来晚了，但是现在有一个.NET Core可用的模板，您可以使用一个命令来构建。</font><font style="vertical-align: inherit;">在安装了.NET Core的Windows框中，只需创建一个空文件夹，然后在该文件夹中运行以下命令以显示可用模板的列表：</font></font></p>

<pre><code>dotnet new
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果没有所有模板，则只需运行以下模板即可安装SPA模板：</font></font></p>

<pre><code>dotnet new --install Microsoft.AspNetCore.SpaTemplates::*
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这可以搭建一个新的Vue应用程序：</font></font></p>

<pre><code>dotnet new vue
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在几毫秒内，便会构建一个完整的全新Vue.js单页Web应用程序，该Web应用程序具有可运行的.NET Core后端，并带有控制器，视图等。</font><font style="vertical-align: inherit;">只需使用VS或VS Code打开项目，您就可以离开。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">还有Aurelia，Angular，Knockout和React的模板！</font><font style="vertical-align: inherit;">您可以将它们全部构建起来，然后比较它们如何解决相同的问题。</font><font style="vertical-align: inherit;">Angular甚至可以立即进行服务器端预渲染！</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我知道.NET Core有路要走，但是它一天比一天变得越来越强大！</font></font></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
