---
layout: question
title:  如何将SaSS用于ASP.NET MVC应用程序？
date:   2020-03-24T07:27:30.000Z
description: 问题与疑问我一直在CSS代码方面遇到问题，所以现在我总是使用SaSS代码。但是我的问题是：如何将SaSS用于ASP.NET MVC应用程序？我...
img: 
author: 古一
category: question
answer: 0
tags: asp.net-mvc CSS
topic: CSS
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><h2><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">问题与疑问</font></font></h2>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我一直在CSS代码方面遇到问题，所以现在我总是使用SaSS代码。</font><font style="vertical-align: inherit;">但是我的问题是：如何将SaSS用于ASP.NET MVC应用程序？</font></font></p>

<p><a href="https://www.samyoc.com//uploads/users/24004/images/thumbnails/1585034723470.gif" data-src="https://www.samyoc.com//uploads/users/24004/images/1585034723470.gif" rel="noreferrer"><img src="https://cloud.githubusercontent.com/assets/16222780/22893413/ecb2f00c-f215-11e6-8d90-52930964b6ad.gif" alt=""></a></p>

<h2><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我试过了</font></font></h2>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我尝试过为此使用Gulp任务。</font><font style="vertical-align: inherit;">我用过这些命令</font></font></p>

<pre class="lang-shell prettyprint-override"><code>npm init<font></font>
npm install --save gulp<font></font>
npm install --save gulp-sass<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这是我的</font></font><code>package.json</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">文件：</font></font></p>

<pre class="lang-json prettyprint-override"><code>{<font></font>
  "name": "markeonline",<font></font>
  "version": "1.0.0",<font></font>
  "description": "",<font></font>
  "main": "index.js",<font></font>
  "scripts": {<font></font>
    "test": "echo \"Error: no test specified\" &amp;&amp; exit 1"<font></font>
  },<font></font>
  "author": "Hein Pauwelyn",<font></font>
  "license": "ISC",<font></font>
  "dependencies": {<font></font>
    "gulp": "^3.9.1",<font></font>
    "gulp-sass": "^3.1.0"<font></font>
  }<font></font>
}<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这里是 </font></font><code>gulpfile.js</code></p>

<pre class="lang-js prettyprint-override"><code>var gulp = require("gulp"),<font></font>
    sass = require("gulp-sass");<font></font>
<font></font>
// other content removed<font></font>
<font></font>
gulp.task("sass", function () {<font></font>
    return gulp.src('./**/*.scss')<font></font>
      .pipe(sass())<font></font>
      .pipe(gulp.dest(project.webroot + './MarkeOnline.Website/Content/css'));<font></font>
});<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这是我的项目结构：</font></font></p>

<p><a href="https://www.samyoc.com//uploads/users/24004/images/thumbnails/1585034723478.png" data-src="https://www.samyoc.com//uploads/users/24004/images/1585034723478.png" rel="noreferrer"><img src="https://i.stack.imgur.com/VsdaC.png" alt="Visual Studio的解决方案资源管理器"></a></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果我使用以下命令，此代码将给我以下错误：</font></font></p>

<pre class="lang-shell prettyprint-override"><code>gulp sass
</code></pre>

<blockquote>
  <p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">ReferenceError：</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">项目未定义</font></font></p>
  
  <pre class="lang-none prettyprint-override"><code>[17:50:58] ReferenceError: project is not defined<font></font>
    at Gulp.&lt;anonymous&gt; (D:\Documenten\Howest\Semester 4\05 - Project\MarkeOnlinebis\Project Execution\MarkeOnline\gulpfile.js:9:23)<font></font>
    at module.exports (D:\Documenten\Howest\Semester 4\05 - Project\MarkeOnlinebis\Project Execution\MarkeOnline\node_modules\orchestrator\lib\runTask.js:34:7)<font></font>
    at Gulp.Orchestrator._runTask (D:\Documenten\Howest\Semester 4\05 - Project\MarkeOnlinebis\Project Execution\MarkeOnline\node_modules\orchestrator\index.js:273:3)<font></font>
    at Gulp.Orchestrator._runStep (D:\Documenten\Howest\Semester 4\05 - Project\MarkeOnlinebis\Project Execution\MarkeOnline\node_modules\orchestrator\index.js:214:10)<font></font>
    at Gulp.Orchestrator.start (D:\Documenten\Howest\Semester 4\05 - Project\MarkeOnlinebis\Project Execution\MarkeOnline\node_modules\orchestrator\index.js:134:8)<font></font>
    at C:\Users\hein_\AppData\Roaming\npm\node_modules\gulp\bin\gulp.js:129:20<font></font>
    at _combinedTickCallback (internal/process/next_tick.js:67:7)<font></font>
    at process._tickCallback (internal/process/next_tick.js:98:9)<font></font>
    at Module.runMain (module.js:592:11)<font></font>
    at run (bootstrap_node.js:394:7)<font></font>
<font></font>
events.js:160<font></font>
      throw er; // Unhandled 'error' event<font></font>
      ^<font></font>
Error: node_modules\node-sass\test\fixtures\depth-first\_vars.scss<font></font>
Error: Undefined variable: "$import-counter".<font></font>
        on line 1 of node_modules/node-sass/test/fixtures/depth-first/_vars.scss<font></font>
&gt;&gt; $import_counter: $import_counter + 1;<font></font>
   -----------------^<font></font>
<font></font>
    at options.error (D:\Documenten\Howest\Semester 4\05 - Project\MarkeOnlinebis\Project Execution\MarkeOnline\node_modules\node-sass\lib\index.js:291:26)<font></font>
</code></pre>
</blockquote></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第3440篇《如何将SaSS用于ASP.NET MVC应用程序？》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    
    </div>
    {% endraw %}
  </div>
<div>
