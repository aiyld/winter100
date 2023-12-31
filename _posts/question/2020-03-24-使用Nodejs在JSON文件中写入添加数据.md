---
layout: question
title:  使用Node.js在JSON文件中写入/添加数据
date:   2020-03-24T02:57:03.000Z
description: 我试图使用节点从循环数据中写入JSON文件，例如：let jsonFile = require('jsonfile');for (i = 0; i...
img: 
author: 斯丁
category: question
answer: 1
tags: JavaScript Node.js
topic: Node.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我试图使用节点从循环数据中写入JSON文件，例如：</font></font></p>

<pre class="lang-js prettyprint-override"><code>let jsonFile = require('jsonfile');<font></font>
<font></font>
for (i = 0; i &lt; 11; i++) {<font></font>
    jsonFile.writeFile('loop.json', "id :" + i + " square :" + i * i);<font></font>
}<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">loop.json中的outPut是：</font></font></p>

<pre><code>id :1 square : 1
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">但是我想要这样的输出文件（如下），并且如果我再次运行该代码，它应该将该新输出添加为相同的现有JSON文件中的元素：</font></font></p>

<pre class="lang-json prettyprint-override"><code>{<font></font>
   "table":[<font></font>
      {<font></font>
         "Id ":1,<font></font>
         "square ":1<font></font>
      },<font></font>
      {<font></font>
         "Id ":2,<font></font>
         "square ":3<font></font>
      },<font></font>
      {<font></font>
         "Id ":3,<font></font>
         "square ":9<font></font>
      },<font></font>
      {<font></font>
         "Id ":4,<font></font>
         "square ":16<font></font>
      },<font></font>
      {<font></font>
         "Id ":5,<font></font>
         "square ":25<font></font>
      },<font></font>
      {<font></font>
         "Id ":6,<font></font>
         "square ":36<font></font>
      },<font></font>
      {<font></font>
         "Id ":7,<font></font>
         "square ":49<font></font>
      },<font></font>
      {<font></font>
         "Id ":8,<font></font>
         "square ":64<font></font>
      },<font></font>
      {<font></font>
         "Id ":9,<font></font>
         "square ":81<font></font>
      },<font></font>
      {<font></font>
         "Id ":10,<font></font>
         "square ":100<font></font>
      }<font></font>
   ]<font></font>
}<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我想使用第一次创建的相同文件，但是每当我运行该代码时，新元素都应添加到该文件中</font></font></p>

<pre class="lang-js prettyprint-override"><code>const fs = require('fs');<font></font>
<font></font>
let obj = {<font></font>
    table: []<font></font>
};<font></font>
<font></font>
fs.exists('myjsonfile.json', function(exists) {<font></font>
<font></font>
    if (exists) {<font></font>
<font></font>
        console.log("yes file exists");<font></font>
<font></font>
        fs.readFile('myjsonfile.json', function readFileCallback(err, data) {<font></font>
<font></font>
            if (err) {<font></font>
                console.log(err);<font></font>
            } else {<font></font>
                obj = JSON.parse(data);<font></font>
<font></font>
                for (i = 0; i &lt; 5; i++) {<font></font>
                    obj.table.push({<font></font>
                        id: i,<font></font>
                        square: i * i<font></font>
                    });<font></font>
                }<font></font>
<font></font>
                let json = JSON.stringify(obj);<font></font>
                fs.writeFile('myjsonfile.json', json);<font></font>
            }<font></font>
        });<font></font>
    } else {<font></font>
<font></font>
        console.log("file not exists");<font></font>
<font></font>
        for (i = 0; i &lt; 5; i++) {<font></font>
            obj.table.push({<font></font>
                id: i,<font></font>
                square: i * i<font></font>
            });<font></font>
        }<font></font>
<font></font>
        let json = JSON.stringify(obj);<font></font>
        fs.writeFile('myjsonfile.json', json);<font></font>
    }<font></font>
});<font></font>
</code></pre></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第3256篇《使用Node.js在JSON文件中写入/添加数据》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">卡卡西Near</span>
            <span class="discuss-time">2020.03.24</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">尝试</font></font></p>

<pre><code>var fs = require("fs");<font></font>
var sampleObject = { your data };<font></font>
<font></font>
fs.writeFile("./object.json", JSON.stringify(sampleObject, null, 4), (err) =&gt; {<font></font>
    if (err) {  console.error(err);  return; };<font></font>
    console.log("File has been created");<font></font>
});<font></font>
</code></pre></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
