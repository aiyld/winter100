---
layout: question
title:  通过jQuery.Ajax下载文件
date:   2020-03-28T11:38:58.000Z
description: 我在服务器端有一个Struts2操作，用于文件下载。<action name="download" class="com.xxx.DownAction...
img: 
author: 伽罗Itachi
category: question
answer: 1
tags: JavaScript
topic: JavaScript
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我在服务器端有一个Struts2操作，用于文件下载。</font></font></p>

<pre><code>&lt;action name="download" class="com.xxx.DownAction"&gt;<font></font>
    &lt;result name="success" type="stream"&gt;<font></font>
        &lt;param name="contentType"&gt;text/plain&lt;/param&gt;<font></font>
        &lt;param name="inputName"&gt;imageStream&lt;/param&gt;<font></font>
        &lt;param name="contentDisposition"&gt;attachment;filename={fileName}&lt;/param&gt;<font></font>
        &lt;param name="bufferSize"&gt;1024&lt;/param&gt;<font></font>
    &lt;/result&gt;<font></font>
&lt;/action&gt;<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">但是，当我使用jQuery调用操作时：</font></font></p>

<pre><code>$.post(<font></font>
  "/download.action",{<font></font>
    para1:value1,<font></font>
    para2:value2<font></font>
    ....<font></font>
  },function(data){<font></font>
      console.info(data);<font></font>
   }<font></font>
);<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在Firebug中，我看到数据是通过</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Binary流</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">检索的</font><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">我想知道如何打开</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">文件下载窗口</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，用户可以用它在本地保存文件吗？</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第3826篇《通过jQuery.Ajax下载文件》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">梅</span>
            <span class="discuss-time">2020.03.28</span>
          </div>
          <div class="discuss-comment"><p><em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">没有人发布此</font></font><a href="https://stackoverflow.com/questions/4545311/download-a-file-by-jquery-ajax#comment4981707_4545311"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">@Pekka的解决方案</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> ...所以我将其发布。</font><font style="vertical-align: inherit;">它可以帮助某人。</font></font></em></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您不需要通过Ajax进行此操作。</font><font style="vertical-align: inherit;">只需使用</font></font></p>

<pre><code>window.location="download.action?para1=value1...."
</code></pre></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
