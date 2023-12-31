---
layout: question
title:  Laravel 5.2 CORS，GET无法与预检选项一起使用
date:   2020-03-12T09:07:57.000Z
description: 可怕的CORS错误：  跨域请求被阻止：同源策略禁止读取http：// localhost / mysite / api / test上的远程资源。...
img: 
author: 猪猪L
category: question
answer: 1
tags: php PHP
topic: PHP
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">可怕的CORS错误：</font></font></p>

<blockquote>
  <p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">跨域请求被阻止：同源策略禁止读取</font></font><a href="http://localhost/mysite/api/test"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">http：// localhost / mysite / api / test上</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">的远程资源</font><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">（原因：CORS标头“ Access-Control-Allow-Origin”缺失）。</font></font></p>
</blockquote>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Laravel路线：</font></font></p>

<pre><code>$router-&gt;group(['prefix' =&gt; 'api', 'middleware' =&gt; 'cors'], function ($router) {<font></font>
    $router-&gt;get('/test', 'MyController@myMethod');<font></font>
});<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Laravel Cors Middlware：</font></font></p>

<pre><code>public function handle($request, Closure $next)<font></font>
    {<font></font>
        header('Access-Control-Allow-Origin: *');<font></font>
<font></font>
        // ALLOW OPTIONS METHOD<font></font>
        $headers = [<font></font>
            'Access-Control-Allow-Methods' =&gt; 'POST, GET, OPTIONS, PUT, DELETE',<font></font>
            'Access-Control-Allow-Headers' =&gt; 'Content-Type, X-Auth-Token, Origin, Authorization'<font></font>
        ];<font></font>
        if ($request-&gt;getMethod() == "OPTIONS") {<font></font>
            // The client-side application can set only headers allowed in Access-Control-Allow-Headers<font></font>
            return Response::make('OK', 200, $headers);<font></font>
        }<font></font>
<font></font>
        $response = $next($request);<font></font>
        foreach ($headers as $key =&gt; $value)<font></font>
            $response-&gt;header($key, $value);<font></font>
        return $response;<font></font>
    }<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Laravel内核：</font></font></p>

<pre><code> protected $routeMiddleware = [<font></font>
        'auth' =&gt; \App\Http\Middleware\Authenticate::class,<font></font>
        'auth.basic' =&gt; \Illuminate\Auth\Middleware\AuthenticateWithBasicAuth::class,<font></font>
        'guest' =&gt; \App\Http\Middleware\RedirectIfAuthenticated::class,<font></font>
        'throttle' =&gt; \Illuminate\Routing\Middleware\ThrottleRequests::class,<font></font>
        'cors' =&gt; \App\Http\Middleware\CORS::class<font></font>
    ];<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">相关的.htaccess：</font></font></p>

<pre><code>RewriteCond %{HTTP:Authorization} .<font></font>
RewriteRule .* - [E=HTTP_AUTHORIZATION:%{HTTP:Authorization}]<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">相关的Vue.js：</font></font></p>

<pre><code> new Vue({<font></font>
        el: '#app',<font></font>
        data: {<font></font>
           //data here<font></font>
        },<font></font>
        http: {<font></font>
            headers: {<font></font>
                "Authorization": "Basic " + "apiKeyHere"<font></font>
            }<font></font>
        },<font></font>
        methods: {<font></font>
            mymethod: function (e)<font></font>
            {<font></font>
                e.preventDefault();<font></font>
                this.$http.get('http://localhost/mysite/api/test').then(<font></font>
                        function (response)<font></font>
                        {<font></font>
                          //do something<font></font>
                        }<font></font>
                )<font></font>
            }<font></font>
        }<font></font>
    });<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果我取出Authorization标头选项，则请求有效。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我也尝试过</font></font><a href="https://github.com/barryvdh/laravel-cors"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">https://github.com/barryvdh/laravel-cors，</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">但仍然没有任何乐趣。</font><font style="vertical-align: inherit;">任何帮助表示赞赏！</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第1182篇《Laravel 5.2 CORS，GET无法与预检选项一起使用》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">LEYAItachi</span>
            <span class="discuss-time">2020.03.12</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您的中间件还可以，但是您需要在全局HTTP中间件堆栈中注册Cors中间件。</font></font></p>

<pre><code>protected $middleware = [<font></font>
    \Illuminate\Foundation\Http\Middleware\CheckForMaintenanceMode::class,<font></font>
    \App\Http\Middleware\CorsMiddleware::class<font></font>
];<font></font>
</code></pre></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
