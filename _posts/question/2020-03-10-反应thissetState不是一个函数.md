---
layout: question
title:  反应this.setState不是一个函数
date:   2020-03-10T02:45:21.000Z
description: 我是React的新手，正在尝试编写使用API​​的应用程序。我不断收到此错误：  TypeError：this.setState不是一个函数当...
img: 
author: Stafan小宇宙
category: question
answer: 4
tags: JavaScript
topic: JavaScript
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我是React的新手，正在尝试编写使用API​​的应用程序。</font><font style="vertical-align: inherit;">我不断收到此错误：</font></font></p>

<blockquote>
  <p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">TypeError：this.setState不是一个函数</font></font></p>
</blockquote>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">当我尝试处理API响应时。</font><font style="vertical-align: inherit;">我怀疑此绑定有问题，但我不知道如何解决它。</font><font style="vertical-align: inherit;">这是我组件的代码：</font></font></p>

<pre><code>var AppMain = React.createClass({<font></font>
    getInitialState: function() {<font></font>
        return{<font></font>
            FirstName: " "<font></font>
        };<font></font>
    },<font></font>
    componentDidMount:function(){<font></font>
        VK.init(function(){<font></font>
            console.info("API initialisation successful");<font></font>
            VK.api('users.get',{fields: 'photo_50'},function(data){<font></font>
                if(data.response){<font></font>
                    this.setState({ //the error happens here<font></font>
                        FirstName: data.response[0].first_name<font></font>
                    });<font></font>
                    console.info(this.state.FirstName);<font></font>
                }<font></font>
<font></font>
            });<font></font>
        }, function(){<font></font>
        console.info("API initialisation failed");<font></font>
<font></font>
        }, '5.34');<font></font>
    },<font></font>
    render:function(){<font></font>
        return (<font></font>
            &lt;div className="appMain"&gt;<font></font>
            &lt;Header  /&gt;<font></font>
            &lt;/div&gt;<font></font>
        );<font></font>
    }<font></font>
});<font></font>
</code></pre></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第444篇《反应this.setState不是一个函数》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">神乐蛋蛋</span>
            <span class="discuss-time">2020.03.10</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">使用箭头函数，因为箭头函数指向父级作用域，因此将可用。</font><font style="vertical-align: inherit;">（代替绑定技术）</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">LEYMandy</span>
            <span class="discuss-time">2020.03.10</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">现在，ES6具有箭头功能，如果您确实与bind（this）表达式混淆，可以尝试使用箭头功能</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我就是这样</font></font></p>

<pre><code>componentWillMount() {<font></font>
        ListApi.getList()<font></font>
            .then(JsonList =&gt; this.setState({ List: JsonList }));<font></font>
    }<font></font>
<font></font>
 //Above method equalent to this...<font></font>
     componentWillMount() {<font></font>
         ListApi.getList()<font></font>
             .then(function (JsonList) {<font></font>
                 this.setState({ List: JsonList });<font></font>
             }.bind(this));<font></font>
 }<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">西里西门</span>
            <span class="discuss-time">2020.03.10</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您只需要绑定事件 </font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">对于前 </font></font></p>

<pre><code>// place this code to your constructor<font></font>
<font></font>
this._handleDelete = this._handleDelete.bind(this);<font></font>
<font></font>
// and your setState function will work perfectly<font></font>
<font></font>
_handleDelete(id){<font></font>
<font></font>
    this.state.list.splice(id, 1);<font></font>
<font></font>
    this.setState({ list: this.state.list });<font></font>
<font></font>
    // this.setState({list: list});<font></font>
<font></font>
}<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">TomGO</span>
            <span class="discuss-time">2020.03.10</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">React建议在需要使用this </font></font><code>class</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">而不是self的</font><font style="vertical-align: inherit;">所有方法中将此绑定</font></font><code>function</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p>

<pre><code>constructor(props) {<font></font>
    super(props)<font></font>
    this.onClick = this.onClick.bind(this)<font></font>
}<font></font>
<font></font>
 onClick () {<font></font>
     this.setState({...})<font></font>
 }<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">或者您也可以使用</font></font><code>arrow function</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
