---
layout: question
title:  如何防止moment.js用webpack加载语言环境？
date:   2020-03-20T06:01:59.000Z
description: 您好，无论如何，当您使用webpack时，您可以阻止moment.js加载所有语言环境（我只需要英语）？我正在查看源代码，似乎如果为Webpack定义了h...
img: 
author: 老丝神奇
category: question
answer: 0
tags: JavaScript Webpack
topic: Webpack
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您好，无论如何，当您使用webpack时，您可以阻止moment.js加载所有语言环境（我只需要英语）？</font><font style="vertical-align: inherit;">我正在查看源代码，似乎如果为Webpack定义了hasModule，那么它将始终尝试对每个语言环境进行require（）。</font><font style="vertical-align: inherit;">我很确定这需要拉取请求来解决。</font><font style="vertical-align: inherit;">但是无论如何，我们可以使用webpack配置修复此问题。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这是我的webpack配置以加载moment.js</font></font></p>

<pre><code>resolve: {<font></font>
            alias: {<font></font>
                moment: path.join(__dirname, "src/lib/bower/moment/moment.js")<font></font>
            },<font></font>
        },<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">然后，在我需要的任何地方，我只需要require（'moment'）即可，但这会在捆绑包中添加约250kb不需要的语言文件。</font><font style="vertical-align: inherit;">另外，我正在使用momentjs和gulp的凉亭版本。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">此外，如果无法通过webpack配置解决此问题，则这里是指向该函数的链接，该函数在其中加载语言环境</font></font><a href="https://github.com/moment/moment/blob/develop/moment.js#L760-L772"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">https://github.com/moment/moment/blob/develop/moment.js#L760-L772</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我尝试添加“ &amp;&amp; module.exports.loadLocales”添加到if语句，但是我想webpack不会以某种可行的方式正常工作，无论我现在认为它使用的是regex就是什么，所以我真的不知道你怎么会去修复它。</font><font style="vertical-align: inherit;">无论如何，感谢您的帮助。</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第2515篇《如何防止moment.js用webpack加载语言环境？》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    
    </div>
    {% endraw %}
  </div>
<div>
