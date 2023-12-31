---
layout: question
title:  Koa的\`ctx.status\`没有发送给客户
date:   2020-04-03T03:00:13.000Z
description: 这是我的简单路线：router.post('/getFile', async (ctx) => {  const fileName = \`${ctx...
img: 
author: 小胖Gil
category: question
answer: 0
tags: JavaScript KoaJS
topic: KoaJS
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这是我的简单路线：</font></font></p>

<pre><code>router.post('/getFile', async (ctx) =&gt; {<font></font>
  const fileName = `${ctx.request.body.file}.pdf`;<font></font>
  const file = fs.createReadStream(fileName); // This file might not exist.<font></font>
<font></font>
  file.on('error', (err) =&gt; {<font></font>
    ctx.response.status = 500; // This status code doesn't make it to client when there's an error.<font></font>
  });<font></font>
<font></font>
  ctx.response.type = 'application/pdf';<font></font>
  ctx.response.body = file;<font></font>
});<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这是我的客户代码：</font></font></p>

<pre><code>async function main() {<font></font>
  const request = {<font></font>
    method: 'POST',<font></font>
    body: JSON.stringify({ file: 'bad-file-name' }),<font></font>
    headers: {<font></font>
      'Content-Type': 'application/json',<font></font>
      'Accept': 'application/pdf'<font></font>
    }<font></font>
  };<font></font>
<font></font>
  const response = await fetch('/getFile', request);<font></font>
<font></font>
  if (!response.ok) {<font></font>
    console.log(response.status); // This is always 404 when I give a bad file name, even though I set it to 500 above. Why?<font></font>
  }<font></font>
}<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">发送正确的文件名后，一切都很好，但是</font></font><code>404</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">即使</font></font><code>500</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在错误期间在服务器代码</font><font style="vertical-align: inherit;">中将其设置</font><font style="vertical-align: inherit;">为响应状态，为什么总是显示响应状态代码</font><font style="vertical-align: inherit;">？</font><font style="vertical-align: inherit;">可能是我的代码到达时响应已经完成发送，</font></font><code>ctx.response.body = ...</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在这种情况下，代码中的代码</font></font><code>.on('error')</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">什么都没做？</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">任何帮助，将不胜感激。</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第3948篇《Koa的\`ctx.status\`没有发送给客户》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    
    </div>
    {% endraw %}
  </div>
<div>
