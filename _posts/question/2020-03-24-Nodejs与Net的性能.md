---
layout: question
title:  Node.js与.Net的性能
date:   2020-03-24T02:57:46.000Z
description: 我已经阅读了很多有关Node.js快速且能够容纳大量负载的信息。有没有人比其他框架有任何现实世界的证据，特别是.Net？我读过的大多数文章都是轶事，或者没...
img: 
author: 泡芙
category: question
answer: 5
tags: .net Node.js
topic: Node.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我已经阅读了很多有关Node.js快速且能够容纳大量负载的信息。</font><font style="vertical-align: inherit;">有没有人比其他框架有任何现实世界的证据，特别是.Net？</font><font style="vertical-align: inherit;">我读过的大多数文章都是轶事，或者没有与.Net的比较。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">谢谢   </font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第3258篇《Node.js与.Net的性能》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">米亚逆天</span>
            <span class="discuss-time">2020.03.24</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我必须同意Marcus Granstrom的观点，在这里非常重要。</font></font></p>

<p>To be honest it sounds like you’re making a high impact architectural decision. 
My advice would be to isolate the areas of concern and do a "bake off" between whatever stacks you are considering. </p>

<p>At the end of the day you are responsible for the decision and I don’t think the excuse 
"Some guy on Stackoverflow showed me an article that said it would be fine" 
Will cut it with your boss.</p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">猪猪</span>
            <span class="discuss-time">2020.03.24</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我在nodejs和IIS之间进行了基本的性能测试。</font><font style="vertical-align: inherit;">抛出“ hello，world！”时，IIS的速度大约是nodejs的2.5倍。</font><font style="vertical-align: inherit;">下面的代码。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我的硬件：Dell Latitude E6510，Core i5（双核），8 GB RAM，Windows 7 Enterprise 64位操作系统</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">节点服务器</font></font></p>

<pre><code>runs at http://localhost:9090/<font></font>
/// &lt;reference path="node-vsdoc.js" /&gt;<font></font>
var http = require("http");<font></font>
http.createServer(function (request, response) {<font></font>
response.writeHead(200, { "Content-Type": "text/html" });<font></font>
response.write("&lt;p&gt;hello, world!&lt;/p&gt;");<font></font>
response.end();<font></font>
}).listen(9090);<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">default.htm</font></font></p>

<pre><code>hosted by iis at http://localhost/test/<font></font>
&lt;p&gt;hello, world!&lt;/p&gt;<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我自己的使用任务并行库的基准测试程序：</font></font></p>

<pre><code>using System;<font></font>
using System.Collections.Generic;<font></font>
using System.Linq;<font></font>
using System.Text;<font></font>
using System.Net;<font></font>
using System.Threading;<font></font>
using System.Threading.Tasks;<font></font>
using System.Diagnostics;<font></font>
<font></font>
namespace HttpBench<font></font>
{<font></font>
class Program<font></font>
{<font></font>
    private int TotalCount = 100000;<font></font>
    private int ConcurrentThreads = 1000;<font></font>
    private int failedCount;<font></font>
    private int totalBytes;<font></font>
    private int totalTime;<font></font>
    private int completedCount;<font></font>
    private static object lockObj = new object();<font></font>
<font></font>
    /// &lt;summary&gt;<font></font>
    /// main entry point<font></font>
    /// &lt;/summary&gt;<font></font>
    static void Main(string[] args)<font></font>
    {<font></font>
        Program p = new Program();<font></font>
        p.Run(args);<font></font>
    }<font></font>
<font></font>
    /// &lt;summary&gt;<font></font>
    /// actual execution<font></font>
    /// &lt;/summary&gt;<font></font>
    private void Run(string[] args)<font></font>
    {<font></font>
        // check command line<font></font>
        if (args.Length == 0)<font></font>
        {<font></font>
            this.PrintUsage();<font></font>
            return;<font></font>
        }<font></font>
        if (args[0] == "/?" || args[0] == "/h")<font></font>
        {<font></font>
            this.PrintUsage();<font></font>
            return;<font></font>
        }<font></font>
<font></font>
        // use parallel library, download data<font></font>
        ParallelOptions options = new ParallelOptions();<font></font>
        options.MaxDegreeOfParallelism = this.ConcurrentThreads;<font></font>
        int start = Environment.TickCount;<font></font>
        Parallel.For(0, this.TotalCount, options, i =&gt;<font></font>
            {<font></font>
                this.DownloadUrl(i, args[0]);<font></font>
            }<font></font>
        );<font></font>
        int end = Environment.TickCount;<font></font>
<font></font>
        // print results<font></font>
        this.Print("Total requests sent: {0}", true, this.TotalCount);<font></font>
        this.Print("Concurrent threads: {0}", true, this.ConcurrentThreads);<font></font>
        this.Print("Total completed requests: {0}", true, this.completedCount);<font></font>
        this.Print("Failed requests: {0}", true, this.failedCount);<font></font>
        this.Print("Sum total of thread times (seconds): {0}", true, this.totalTime / 1000);<font></font>
        this.Print("Total time taken by this program (seconds): {0}", true, (end - start) / 1000);<font></font>
        this.Print("Total bytes: {0}", true, this.totalBytes);<font></font>
    }<font></font>
<font></font>
    /// &lt;summary&gt;<font></font>
    /// download data from the given url<font></font>
    /// &lt;/summary&gt;<font></font>
    private void DownloadUrl(int index, string url)<font></font>
    {<font></font>
        using (WebClient client = new WebClient())<font></font>
        {<font></font>
            try<font></font>
            {<font></font>
                int start = Environment.TickCount;<font></font>
                byte[] data = client.DownloadData(url);<font></font>
                int end = Environment.TickCount;<font></font>
                lock (lockObj)<font></font>
                {<font></font>
                    this.totalTime = this.totalTime + (end - start);<font></font>
                    if (data != null)<font></font>
                    {<font></font>
                        this.totalBytes = this.totalBytes + data.Length;<font></font>
                    }<font></font>
                }<font></font>
            }<font></font>
            catch<font></font>
            {<font></font>
                lock (lockObj) { this.failedCount++; }<font></font>
            }<font></font>
            lock (lockObj)<font></font>
            {<font></font>
                this.completedCount++;<font></font>
                if (this.completedCount % 10000 == 0)<font></font>
                {<font></font>
                    this.Print("Completed {0} requests.", true, this.completedCount);<font></font>
                }<font></font>
            }<font></font>
        }<font></font>
    }<font></font>
<font></font>
    /// &lt;summary&gt;<font></font>
    /// print usage of this program<font></font>
    /// &lt;/summary&gt;<font></font>
    private void PrintUsage()<font></font>
    {<font></font>
        this.Print("usage: httpbench [options] &lt;url&gt;");<font></font>
    }<font></font>
<font></font>
    /// &lt;summary&gt;<font></font>
    /// print exception message to console<font></font>
    /// &lt;/summary&gt;<font></font>
    private void PrintError(string msg, Exception ex = null, params object[] args)<font></font>
    {<font></font>
        StringBuilder sb = new System.Text.StringBuilder();<font></font>
        sb.Append("Error: ");<font></font>
        sb.AppendFormat(msg, args);<font></font>
        if (ex != null)<font></font>
        {<font></font>
            sb.Append("Exception: ");<font></font>
            sb.Append(ex.Message);<font></font>
        }<font></font>
        this.Print(sb.ToString());<font></font>
    }<font></font>
<font></font>
    /// &lt;summary&gt;<font></font>
    /// print to console<font></font>
    /// &lt;/summary&gt;<font></font>
    private void Print(string msg, bool isLine = true, params object[] args)<font></font>
    {<font></font>
        if (isLine)<font></font>
        {<font></font>
            Console.WriteLine(msg, args);<font></font>
        }<font></font>
        else<font></font>
        {<font></font>
            Console.Write(msg, args);<font></font>
        }<font></font>
    }<font></font>
<font></font>
}<font></font>
}<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">结果：</font></font></p>

<pre><code>IIS: httpbench.exe http://localhost/test<font></font>
<font></font>
Completed 10000 requests.<font></font>
Completed 20000 requests.<font></font>
Completed 30000 requests.<font></font>
Completed 40000 requests.<font></font>
Completed 50000 requests.<font></font>
Completed 60000 requests.<font></font>
Completed 70000 requests.<font></font>
Completed 80000 requests.<font></font>
Completed 90000 requests.<font></font>
Completed 100000 requests.<font></font>
Total requests sent: 100000<font></font>
Concurrent threads: 1000<font></font>
Total completed requests: 100000<font></font>
Failed requests: 0<font></font>
Sum total of thread times (seconds): 97<font></font>
Total time taken by this program (seconds): 16<font></font>
Total bytes: 2000000<font></font>
<font></font>
nodejs: httpbench.exe http://localhost:9090/<font></font>
<font></font>
Completed 10000 requests.<font></font>
Completed 20000 requests.<font></font>
Completed 30000 requests.<font></font>
Completed 40000 requests.<font></font>
Completed 50000 requests.<font></font>
Completed 60000 requests.<font></font>
Completed 70000 requests.<font></font>
Completed 80000 requests.<font></font>
Completed 90000 requests.<font></font>
Completed 100000 requests.<font></font>
Total requests sent: 100000<font></font>
Concurrent threads: 1000<font></font>
Total completed requests: 100000<font></font>
Failed requests: 0<font></font>
Sum total of thread times (seconds): 234<font></font>
Total time taken by this program (seconds): 27<font></font>
Total bytes: 2000000<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">结论：IIS比nodejs快约2.5倍（在Windows上）。</font><font style="vertical-align: inherit;">这是一个非常基本的测试，绝不是结论性的。</font><font style="vertical-align: inherit;">但是我相信这是一个很好的起点。</font><font style="vertical-align: inherit;">在其他Web服务器和其他平台上，Node.js可能更快，但是在Windows IIS上胜出。</font><font style="vertical-align: inherit;">希望将ASP.NET MVC转换为nodejs的开发人员应该暂停并三思而后行。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">已更新（5/17/2012）Tomcat（在Windows上）似乎击败了IIS，在抛出静态html方面比IIS快约3倍。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">雄猫</font></font></p>

<pre><code>index.html at http://localhost:8080/test/<font></font>
&lt;p&gt;hello, world!&lt;/p&gt;<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Tomcat结果</font></font></p>

<pre><code>httpbench.exe http://localhost:8080/test/<font></font>
Completed 10000 requests.<font></font>
Completed 20000 requests.<font></font>
Completed 30000 requests.<font></font>
Completed 40000 requests.<font></font>
Completed 50000 requests.<font></font>
Completed 60000 requests.<font></font>
Completed 70000 requests.<font></font>
Completed 80000 requests.<font></font>
Completed 90000 requests.<font></font>
Completed 100000 requests.<font></font>
Total requests sent: 100000<font></font>
Concurrent threads: 1000<font></font>
Total completed requests: 100000<font></font>
Failed requests: 0<font></font>
Sum total of thread times (seconds): 31<font></font>
Total time taken by this program (seconds): 5<font></font>
Total bytes: 2000000<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">更新后的结论：我多次运行基准程序。</font><font style="vertical-align: inherit;">Tomcat似乎是在WINDOWS上分发STATIC HTML的最快的服务器。</font></font></p>

<p>Updated (5/18/2012)
Previously I had 100,000 total requests with 10,000 concurrent requests. I increased it to 1,000,000 total requess and 100,000 concurrent requests. IIS comes out as the screaming winner, with Nodejs fairing the worst. I have tabularized the results below:</p>

<p><img src="https://i.stack.imgur.com/9YDGA.gif" alt="NodeJS vs IIS vs Tomcat在Windows上提供静态HTML">.</p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">梅番长</span>
            <span class="discuss-time">2020.03.24</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">作为</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">FAST</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">和处理大量的</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">负载</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">是两回事。</font><font style="vertical-align: inherit;">如果您每秒发送500个请求（在</font><strong><font style="vertical-align: inherit;">LOAD</font></strong><font style="vertical-align: inherit;">之下</font><font style="vertical-align: inherit;">）</font><font style="vertical-align: inherit;">，那么实际上</font><font style="vertical-align: inherit;">每秒处理一个请求的速度</font><font style="vertical-align: inherit;">非常</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">快的</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">服务器</font><font style="vertical-align: inherit;">可能完全崩溃</font><font style="vertical-align: inherit;">。</font></font><strong><font style="vertical-align: inherit;"></font></strong><font style="vertical-align: inherit;"></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您还必须考虑静态（和缓存）与动态页面。</font><font style="vertical-align: inherit;">如果您担心静态页面，则IIS可能会击败节点，因为IIS使用内核模式缓存，这意味着请求静态页面的请求甚至都不会脱离内核。  </font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我猜想您正在寻找ASP.NET与节点之间的比较。</font><font style="vertical-align: inherit;">在这场战斗中，在对所有内容进行编译/解释之后，您的性能可能会非常接近。</font><font style="vertical-align: inherit;">也许.NET有点</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">更快</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">或许节点是一个小</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">更快</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，但它可能接近，以至于你不在乎。</font><font style="vertical-align: inherit;">我会在.NET上下注，但我不确定。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">节点真正引人注目的地方是处理</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">LOAD</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">这就是技术真正不同之处。</font><font style="vertical-align: inherit;">ASP.NET为来自其线程池的每个请求专用一个线程，一旦ASP.NET用尽了所有可用线程的请求，便开始排队。</font><font style="vertical-align: inherit;">如果您像@shankar的示例一样在提供“ Hello World”应用程序，那么这可能没什么大不了的，因为不会阻塞线程，并且您将能够处理很多请求，然后再处理用完线程。</font><font style="vertical-align: inherit;">当您开始发出阻止线程的I / O请求（调用DB，向服务发出http请求，从磁盘读取文件）时，ASP.NET模型就会出现问题。</font><font style="vertical-align: inherit;">这些阻塞请求意味着您来自线程池的宝贵线程无所作为。</font><font style="vertical-align: inherit;">您拥有的障碍越多，</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">加载</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您的ASP.NET应用即可。  </font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">为了防止这种阻塞，请使用I / O完成端口，这些端口在等待响应时不需要保持线程。</font><font style="vertical-align: inherit;">ASP.NET支持此功能，但是不幸的是，.NET中的许多常见框架/库都不支持。</font><font style="vertical-align: inherit;">例如，ADO.NET支持I / O完成端口，但是Entity Framework不使用它们。</font><font style="vertical-align: inherit;">因此，您可以构建一个纯异步的ASP.NET应用程序并处理大量负载，但是大多数人不会这样做，因为它不像构建同步的应用程序那样容易，并且您可能无法使用某些喜欢的部分框架（如linq到实体）。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">问题在于，ASP.NET（和.NET Framework）是针对异步I / O创建的。</font><font style="vertical-align: inherit;">.NET不在乎您编写同步代码还是异步代码，因此，由开发人员决定是什么。</font><font style="vertical-align: inherit;">部分原因是因为使用异步操作进行线程和编程被认为是“困难的”，.NET希望让每个人都感到高兴（新手和专家）。</font><font style="vertical-align: inherit;">变得更加困难，因为.NET最终以3-4种不同的模式进行异步处理。</font><font style="vertical-align: inherit;">.NET 4.5试图回过头来对.NET框架进行改造，使其具有围绕异步IO的自以为是的模型，但是直到您关心的框架实际支持它时，可能还需要一段时间。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">另一方面，node的设计者做出了明智的选择，即ALL I / O应该是异步的。</font><font style="vertical-align: inherit;">由于这一决定，节点设计者还能够做出以下决定：每个节点实例都是单线程的，以最大程度地减少线程切换，并且一个线程将仅执行已排队的代码。</font><font style="vertical-align: inherit;">那可能是一个新请求，可能是来自数据库请求的回调，也可能是来自您发出的http rest请求的回调。</font><font style="vertical-align: inherit;">节点尝试通过消除线程上下文切换来最大化CPU效率。</font><font style="vertical-align: inherit;">因为节点选择所有I / O都是异步的，所以这也意味着它的所有框架/附加组件都支持该选择。</font><font style="vertical-align: inherit;">在节点中编写100％异步的应用程序比较容易（因为节点会强制您编写异步的应用程序）。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">同样，我没有任何硬性数字可以证明一种方法，但是我认为节点将赢得典型Web应用程序的LOAD竞争。</font><font style="vertical-align: inherit;">高度优化的（100％异步）.NET应用程序可能会花钱让等效的node.js应用程序运行，但是，如果您平均提取所有.NET和所有节点应用程序，则平均而言，节点可能会处理更多加载。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">希望能有所帮助。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">凯西里</span>
            <span class="discuss-time">2020.03.24</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我看到的主要区别是node .js是动态编程语言（类型检查），因此类型必须在运行时派生。</font><font style="vertical-align: inherit;">从理论上讲，像C＃.NET这样的强类型语言在与Node .js（和PHP等）的对抗中具有更大的潜力，尤其是在计算成本很高的地方。</font><font style="vertical-align: inherit;">顺便说一下，.NET与C / C ++的本地互操作性应优于节点.js。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">西里Near</span>
            <span class="discuss-time">2020.03.24</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">NIO服务器（Node.js等）往往比BIO服务器要快。</font><font style="vertical-align: inherit;">（IIS等）。</font><font style="vertical-align: inherit;">为了证明我的观点，TechEmpower是一家专门从事</font></font><a href="http://www.techempower.com/benchmarks/" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Web框架基准测试的公司</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">它们非常开放，并且具有测试所有framewrks的标准方法。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">第9轮测试目前是最新的（2014年5月）。</font><font style="vertical-align: inherit;">已经测试了许多IIS风格，但是aspnet剥离的似乎是最快的IIS变体。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">以下是</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">每秒响应</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">的结果</font><font style="vertical-align: inherit;">（越高越好）：</font></font></p>

<ul>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">JSON序列化 

</font></font><ul>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">nodejs： </font></font><code>228,887</code></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">aspnet剥离： </font></font><code>105,272</code></li>
</ul></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">单一查询

</font></font><ul>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">nodejs-mysql： </font></font><code>88,597</code></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">aspnet-stripped-raw： </font></font><code>47,066</code></li>
</ul></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">多重查询 

</font></font><ul>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">nodejs-mysql： </font></font><code>8,878</code></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">aspnet-stripped-raw： </font></font><code>3,915</code></li>
</ul></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">纯文本 

</font></font><ul>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">nodejs： </font></font><code>289,578</code></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">aspnet剥离： </font></font><code>109,136</code></li>
</ul></li>
</ul>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在所有情况下，Node.js的速度往往都比IIS快2倍以上。 </font></font></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
