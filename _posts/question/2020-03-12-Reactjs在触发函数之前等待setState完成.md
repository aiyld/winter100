---
layout: question
title:  React.js，在触发函数之前等待setState完成？
date:   2020-03-12T09:01:39.000Z
description: 这是我的情况：在this.handleFormSubmit（）上，我正在执行this.setState（）在this.handleFormSubm...
img: 
author: Stafan番长
category: question
answer: 2
tags: JavaScript
topic: JavaScript
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这是我的情况：</font></font></p>

<ul>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在this.handleFormSubmit（）上，我正在执行this.setState（）</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在this.handleFormSubmit（）内部，我正在调用this.findRoutes（）; </font><font style="vertical-align: inherit;">-这取决于this.setState（）的成功完成</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">this.setState（）; </font><font style="vertical-align: inherit;">在this.findRoutes被调用之前没有完成...</font></font></li>
<li><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在调用this.findRoutes（）之前，如何等待this.handleFormSubmit（）内部的this.setState（）完成？</font></font></strong></li>
</ul>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">较差的解决方案：</font></font></p>

<ul>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">将this.findRoutes（）放在componentDidUpdate（）中</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这是不可接受的，因为将有更多与findRoutes（）函数无关的状态更改。</font><font style="vertical-align: inherit;">我不想在不相关的状态更新时触发findRoutes（）函数。</font></font></li>
</ul>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">请参见下面的代码段：</font></font></p>

<pre><code>handleFormSubmit: function(input){<font></font>
                // Form Input<font></font>
                this.setState({<font></font>
                    originId: input.originId,<font></font>
                    destinationId: input.destinationId,<font></font>
                    radius: input.radius,<font></font>
                    search: input.search<font></font>
                })<font></font>
                this.findRoutes();<font></font>
            },<font></font>
            handleMapRender: function(map){<font></font>
                // Intialized Google Map<font></font>
                directionsDisplay = new google.maps.DirectionsRenderer();<font></font>
                directionsService = new google.maps.DirectionsService();<font></font>
                this.setState({map: map});<font></font>
                placesService = new google.maps.places.PlacesService(map);<font></font>
                directionsDisplay.setMap(map);<font></font>
            },<font></font>
            findRoutes: function(){<font></font>
                var me = this;<font></font>
                if (!this.state.originId || !this.state.destinationId) {<font></font>
                    alert("findRoutes!");<font></font>
                    return;<font></font>
                }<font></font>
                var p1 = new Promise(function(resolve, reject) {<font></font>
                    directionsService.route({<font></font>
                        origin: {'placeId': me.state.originId},<font></font>
                        destination: {'placeId': me.state.destinationId},<font></font>
                        travelMode: me.state.travelMode<font></font>
                    }, function(response, status){<font></font>
                        if (status === google.maps.DirectionsStatus.OK) {<font></font>
                            // me.response = response;<font></font>
                            directionsDisplay.setDirections(response);<font></font>
                            resolve(response);<font></font>
                        } else {<font></font>
                            window.alert('Directions config failed due to ' + status);<font></font>
                        }<font></font>
                    });<font></font>
                });<font></font>
                return p1<font></font>
            },<font></font>
            render: function() {<font></font>
                return (<font></font>
                    &lt;div className="MapControl"&gt;<font></font>
                        &lt;h1&gt;Search&lt;/h1&gt;<font></font>
                        &lt;MapForm<font></font>
                            onFormSubmit={this.handleFormSubmit}<font></font>
                            map={this.state.map}/&gt;<font></font>
                        &lt;GMap<font></font>
                            setMapState={this.handleMapRender}<font></font>
                            originId= {this.state.originId}<font></font>
                            destinationId= {this.state.destinationId}<font></font>
                            radius= {this.state.radius}<font></font>
                            search= {this.state.search}/&gt;<font></font>
                    &lt;/div&gt;<font></font>
                );<font></font>
            }<font></font>
        });<font></font>
</code></pre></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第1168篇《React.js，在触发函数之前等待setState完成？》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Tony宝儿</span>
            <span class="discuss-time">2020.03.12</span>
          </div>
          <div class="discuss-comment"><p><code>setState()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">有一个可选的回调参数可用于此目的。</font><font style="vertical-align: inherit;">您只需要对此稍作更改即可：</font></font></p>

<pre><code>// Form Input<font></font>
this.setState(<font></font>
  {<font></font>
    originId: input.originId,<font></font>
    destinationId: input.destinationId,<font></font>
    radius: input.radius,<font></font>
    search: input.search<font></font>
  },<font></font>
  this.findRoutes         // here is where you put the callback<font></font>
);<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">请注意</font><font style="vertical-align: inherit;">，作为第二个参数，</font></font><code>findRoutes</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">对的</font></font><code>setState()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">呼叫</font><font style="vertical-align: inherit;">现在位于</font><font style="vertical-align: inherit;">呼叫</font><font style="vertical-align: inherit;">内部</font><font style="vertical-align: inherit;">。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">
没有，</font></font><code>()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">因为您正在传递函数。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">JinJinDavaidNear</span>
            <span class="discuss-time">2020.03.12</span>
          </div>
          <div class="discuss-comment"><pre><code>       this.setState(<font></font>
        {<font></font>
            originId: input.originId,<font></font>
            destinationId: input.destinationId,<font></font>
            radius: input.radius,<font></font>
            search: input.search<font></font>
        },<font></font>
        function() { console.log("setState completed", this.state) }<font></font>
       )<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这可能会有所帮助</font></font></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
