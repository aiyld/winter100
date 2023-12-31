---
layout: question
title:  如何在Node.js中对Mongoose进行分页？
date:   2020-03-23T03:33:45.000Z
description: 我正在用Node.js和猫鼬编写一个webapp。如何对.find()通话结果进行分页？我想要一个与"LIMIT 50,100"SQL 相当的功能。...
img: 
author: 凯泡芙JinJin
category: question
answer: 9
tags: mongodb Node.js
topic: Node.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我正在用Node.js和猫鼬编写一个webapp。</font><font style="vertical-align: inherit;">如何对</font></font><code>.find()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">通话</font><font style="vertical-align: inherit;">结果进行分页</font><font style="vertical-align: inherit;">？</font><font style="vertical-align: inherit;">我想要一个与</font></font><code>"LIMIT 50,100"</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">SQL </font><font style="vertical-align: inherit;">相当的功能</font><font style="vertical-align: inherit;">。</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第2735篇《如何在Node.js中对Mongoose进行分页？》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">凯西里</span>
            <span class="discuss-time">2020.03.23</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果您使用猫鼬作为</font></font><a href="https://www.npmjs.com/package/restify-mongoose#queries" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">静态</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> API的来源，请查看“ </font><a href="https://www.npmjs.com/package/restify-mongoose#queries" rel="nofollow"><font style="vertical-align: inherit;">restify-mongoose</font></a><font style="vertical-align: inherit;"> ”及其查询。</font><font style="vertical-align: inherit;">它完全内置了此功能。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">集合上的任何查询都提供了在这里有用的标题 </font></font></p>

<pre><code>test-01:~$ curl -s -D - localhost:3330/data?sort=-created -o /dev/null<font></font>
HTTP/1.1 200 OK<font></font>
link: &lt;/data?sort=-created&amp;p=0&gt;; rel="first", &lt;/data?sort=-created&amp;p=1&gt;; rel="next", &lt;/data?sort=-created&amp;p=134715&gt;; rel="last"<font></font>
.....<font></font>
Response-Time: 37<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">因此，基本上，您将获得具有相对线性加载时间的通用服务器，用于查询集合。</font><font style="vertical-align: inherit;">如果您想进入自己的实现中，那真是太棒了。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">飞云</span>
            <span class="discuss-time">2020.03.23</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您可以这样编写查询。  </font></font></p>

<pre><code>mySchema.find().skip((page-1)*per_page).limit(per_page).exec(function(err, articles) {<font></font>
        if (err) {<font></font>
            return res.status(400).send({<font></font>
                message: err<font></font>
            });<font></font>
        } else {<font></font>
            res.json(articles);<font></font>
        }<font></font>
    });<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">page：来自客户端的页码，作为请求参数。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">
per_page：每页显示的结果数</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果您使用的是MEAN堆栈，则以下博客文章提供了许多信息，这些信息可用于在前端使用angular-UI引导程序创建分页，并在后端使用猫鼬跳过和限制方法。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">参见：</font><a href="https://techpituwa.wordpress.com/2015/06/06/mean-js-pagination-with-angular-ui-bootstrap/" rel="nofollow"><font style="vertical-align: inherit;">https</font></a><font style="vertical-align: inherit;"> :   </font></font><a href="https://techpituwa.wordpress.com/2015/06/06/mean-js-pagination-with-angular-ui-bootstrap/" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">//techpituwa.wordpress.com/2015/06/06/mean-js-pagination-with-angular-ui-bootstrap/</font></font></a></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">乐米亚</span>
            <span class="discuss-time">2020.03.23</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您可以使用skip（）和limit（），但是效率很低。</font><font style="vertical-align: inherit;">更好的解决方案是对索引字段加limit（）进行排序。</font><font style="vertical-align: inherit;">Wunderflats的我们在这里发布了一个小型库：</font></font><a href="https://github.com/wunderflats/goosepage" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">https</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> : </font><a href="https://github.com/wunderflats/goosepage" rel="nofollow"><font style="vertical-align: inherit;">//github.com/wunderflats/goosepage</font></a><font style="vertical-align: inherit;"> 
它使用第一种方法。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">西门Jim</span>
            <span class="discuss-time">2020.03.23</span>
          </div>
          <div class="discuss-comment"><p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">简单而强大的分页解决方案</font></font></strong></p>

<pre><code>async getNextDocs(no_of_docs_required: number, last_doc_id?: string) {<font></font>
    let docs<font></font>
<font></font>
    if (!last_doc_id) {<font></font>
        // get first 5 docs<font></font>
        docs = await MySchema.find().sort({ _id: -1 }).limit(no_of_docs_required)<font></font>
    }<font></font>
    else {<font></font>
        // get next 5 docs according to that last document id<font></font>
        docs = await MySchema.find({_id: {$lt: last_doc_id}})<font></font>
                                    .sort({ _id: -1 }).limit(no_of_docs_required)<font></font>
    }<font></font>
    return docs<font></font>
}<font></font>
</code></pre>

<p><code>last_doc_id</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">：您获得的最后一个文档ID</font></font></p>

<p><code>no_of_docs_required</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">：您要提取的文档数，即5、10、50等。</font></font></p>

<ol>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果您不向</font></font><code>last_doc_id</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">方法</font><font style="vertical-align: inherit;">提供</font><font style="vertical-align: inherit;">，则将获得5份最新文档</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果提供了，</font></font><code>last_doc_id</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">那么您将获得接下来的5个文档。</font></font></li>
</ol></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">古一十三</span>
            <span class="discuss-time">2020.03.23</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">最简单，最快捷的方法是，使用objectId示例进行分页；</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">初始负载条件</font></font></p>

<pre><code>condition = {limit:12, type:""};
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">从响应数据中获取第一个和最后一个ObjectId</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">页面下一个条件</font></font></p>

<pre><code>condition = {limit:12, type:"next", firstId:"57762a4c875adce3c38c662d", lastId:"57762a4c875adce3c38c6615"};
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">页面下一个条件</font></font></p>

<pre><code>condition = {limit:12, type:"next", firstId:"57762a4c875adce3c38c6645", lastId:"57762a4c875adce3c38c6675"};
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在猫鼬</font></font></p>

<pre><code>var condition = {};<font></font>
    var sort = { _id: 1 };<font></font>
    if (req.body.type == "next") {<font></font>
        condition._id = { $gt: req.body.lastId };<font></font>
    } else if (req.body.type == "prev") {<font></font>
        sort = { _id: -1 };<font></font>
        condition._id = { $lt: req.body.firstId };<font></font>
    }<font></font>
<font></font>
var query = Model.find(condition, {}, { sort: sort }).limit(req.body.limit);<font></font>
<font></font>
query.exec(function(err, properties) {<font></font>
        return res.json({ "result": result);<font></font>
});<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Itachi</span>
            <span class="discuss-time">2020.03.23</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您也可以使用以下代码行</font></font></p>

<pre><code>per_page = parseInt(req.query.per_page) || 10<font></font>
page_no = parseInt(req.query.page_no) || 1<font></font>
var pagination = {<font></font>
  limit: per_page ,<font></font>
  skip:per_page * (page_no - 1)<font></font>
}<font></font>
users = await User.find({&lt;CONDITION&gt;}).limit(pagination.limit).skip(pagination.skip).exec()<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">该代码将在最新版本的mongo中工作</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Gil</span>
            <span class="discuss-time">2020.03.23</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这是一个示例示例，您可以尝试一下，</font></font></p>



<pre class="lang-js prettyprint-override"><code>var _pageNumber = 2,<font></font>
  _pageSize = 50;<font></font>
<font></font>
Student.count({},function(err,count){<font></font>
  Student.find({}, null, {<font></font>
    sort: {<font></font>
      Name: 1<font></font>
    }<font></font>
  }).skip(_pageNumber &gt; 0 ? ((_pageNumber - 1) * _pageSize) : 0).limit(_pageSize).exec(function(err, docs) {<font></font>
    if (err)<font></font>
      res.json(err);<font></font>
    else<font></font>
      res.json({<font></font>
        "TotalCount": count,<font></font>
        "_Array": docs<font></font>
      });<font></font>
  });<font></font>
 });<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">西里神奇</span>
            <span class="discuss-time">2020.03.23</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在这种情况下，您可以将查询</font></font><code>page</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">和/或</font><font style="vertical-align: inherit;">添加为</font></font><code>limit</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">URL作为查询字符串。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">例如：</font></font><br>
<code>?page=0&amp;limit=25 // this would be added onto your URL: http:localhost:5000?page=0&amp;limit=25</code>  </p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">由于它将是a，因此</font></font><code>String</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我们需要将其转换为a </font></font><code>Number</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">进行计算。</font><font style="vertical-align: inherit;">让我们使用</font></font><code>parseInt</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">方法进行操作，并提供一些默认值。</font></font></p>

<pre><code>const pageOptions = {<font></font>
    page: parseInt(req.query.page, 10) || 0,<font></font>
    limit: parseInt(req.query.limit, 10) || 10<font></font>
}<font></font>
<font></font>
sexyModel.find()<font></font>
    .skip(pageOptions.page * pageOptions.limit)<font></font>
    .limit(pageOptions.limit)<font></font>
    .exec(function (err, doc) {<font></font>
        if(err) { res.status(500).json(err); return; };<font></font>
        res.status(200).json(doc);<font></font>
    });<font></font>
</code></pre>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">BTW</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">  
分页始于</font></font><code>0</code></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">猪猪</span>
            <span class="discuss-time">2020.03.23</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在通过Rodolphe提供的信息仔细研究了Mongoose API之后，我想出了以下解决方案：</font></font></p>

<pre><code>MyModel.find(query, fields, { skip: 10, limit: 5 }, function(err, results) { ... });
</code></pre></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
