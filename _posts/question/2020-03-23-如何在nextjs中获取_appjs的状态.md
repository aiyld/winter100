---
layout: question
title:  如何在next.js中获取_app.js的状态？
date:   2020-03-23T06:41:07.000Z
description: 我已经使用next.js在_app.js中启动了状态。我想在index.js文件中使用此状态。我该如何访问？这是我的_app.js代码：impor...
img: 
author: 梅
category: question
answer: 0
tags: JavaScript React.js
topic: React.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我已经使用next.js在_app.js中启动了状态。</font><font style="vertical-align: inherit;">我想在index.js文件中使用此状态。</font><font style="vertical-align: inherit;">我该如何访问？</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这是我的_app.js代码：</font></font></p>

<pre><code>import React from "react";<font></font>
import App, { Container } from "next/app";<font></font>
import Layout from "../components/Layout";<font></font>
<font></font>
export default class MyApp extends App {<font></font>
  constructor(props) {<font></font>
    super(props);<font></font>
    this.state = {<font></font>
      currencyType: {<font></font>
        name: "Ether",<font></font>
        price: 1<font></font>
      },<font></font>
      ethPriceUsd: 1<font></font>
    };<font></font>
  }<font></font>
<font></font>
  static async getInitialProps({ Component, router, ctx }) {<font></font>
    let pageProps = {};<font></font>
    let ethPriceUsd;<font></font>
<font></font>
    if (Component.getInitialProps) {<font></font>
          fetch(`https://api.coingecko.com/api/v3/coins/ethereum/<font></font>
        `)<font></font>
        .then(result =&gt; result.json())<font></font>
        .then(data =&gt; {<font></font>
          ethPriceUsd = parseFloat(data.market_data.current_price.usd).toFixed(<font></font>
            2<font></font>
          );<font></font>
        });<font></font>
      pageProps = await Component.getInitialProps(ctx);<font></font>
    }<font></font>
<font></font>
    return { pageProps, ethPriceUsd };<font></font>
  }<font></font>
<font></font>
  componentDidMount() {<font></font>
    const ethPriceUsd = this.props.ethPriceUsd;<font></font>
    this.setState({ ethPriceUsd });<font></font>
  }<font></font>
<font></font>
  onCurrencyTypeChange(currencyTypeValue) {<font></font>
    let currencyType = {};<font></font>
    //Value comes from Header.js where Ether is 0 and USD is 1<font></font>
    if (currencyTypeValue) {<font></font>
      currencyType = {<font></font>
        name: "USD",<font></font>
        price: this.state.ethPriceUsd<font></font>
      };<font></font>
    } else {<font></font>
      currencyType = {<font></font>
        name: "Ether",<font></font>
        price: 1<font></font>
      };<font></font>
    }<font></font>
    alert("We pass argument from Child to Parent: " + currencyType.price);<font></font>
    this.setState({ currencyType });<font></font>
  }<font></font>
<font></font>
  render() {<font></font>
    const { Component, pageProps } = this.props;<font></font>
    return (<font></font>
      &lt;Container&gt;<font></font>
        &lt;Layout changeCurrencyType={this.onCurrencyTypeChange.bind(this)}&gt;<font></font>
          &lt;Component {...pageProps} /&gt;<font></font>
        &lt;/Layout&gt;<font></font>
      &lt;/Container&gt;<font></font>
    );<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">}}</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">其中很多都是不相关的（例如将数据传递到Layout等）。</font><font style="vertical-align: inherit;">我只想在index.js中使用此状态</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">谢谢</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第2859篇《如何在next.js中获取_app.js的状态？》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    
    </div>
    {% endraw %}
  </div>
<div>
