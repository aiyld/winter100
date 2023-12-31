---
layout: question
title:  React.js中的Bootstrap模态
date:   2020-03-30T09:48:56.000Z
description: 我需要通过单击Bootstrap导航栏和其他位置的按钮来打开Bootstrap Modal（以显示组件实例的数据，即提供“编辑”功能），但是我不知道如何实...
img: 
author: Tony凯
category: question
answer: 2
tags: JavaScript React.js
topic: React.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我需要通过单击Bootstrap导航栏和其他位置的按钮来打开Bootstrap Modal（</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">以显示组件实例的数据，即提供“编辑”功能</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">），但是我不知道如何实现此目的。</font><font style="vertical-align: inherit;">这是我的代码：</font></font></p>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">编辑：代码已更新。</font></font></strong></p>

<pre><code>ApplicationContainer = React.createClass({<font></font>
    render: function() {<font></font>
        return (<font></font>
            &lt;div className="container-fluid"&gt;<font></font>
            &lt;NavBar /&gt;<font></font>
                &lt;div className="row"&gt;<font></font>
                    &lt;div className="col-md-2"&gt;<font></font>
                        &lt;ScheduleEntryList /&gt;<font></font>
                    &lt;/div&gt;<font></font>
                    &lt;div className="col-md-10"&gt;<font></font>
                    &lt;/div&gt;<font></font>
                &lt;/div&gt;<font></font>
                &lt;ScheduleEntryModal /&gt;<font></font>
            &lt;/div&gt;<font></font>
        );<font></font>
    }<font></font>
});<font></font>
<font></font>
NavBar = React.createClass({<font></font>
    render: function() {<font></font>
        return (<font></font>
            &lt;nav className="navbar navbar-default navbar-fixed-top"&gt;<font></font>
                &lt;div className="container-fluid"&gt;<font></font>
                    &lt;div className="navbar-header"&gt;<font></font>
                        &lt;a className="navbar-brand" href="#"&gt;<font></font>
                            &lt;span className="glyphicon glyphicon-eye-open"&gt;&lt;/span&gt;<font></font>
                        &lt;/a&gt;<font></font>
                    &lt;/div&gt;<font></font>
                    &lt;form className="navbar-form navbar-left"&gt;<font></font>
                        &lt;button className="btn btn-primary" type="button" data-toggle="modal" data-target="#scheduleentry-modal"&gt;<font></font>
                            &lt;span className="glyphicon glyphicon-plus"&gt;<font></font>
                            &lt;/span&gt;<font></font>
                        &lt;/button&gt;<font></font>
                    &lt;/form&gt;<font></font>
                    &lt;ul className="nav navbar-nav navbar-right"&gt;<font></font>
                        &lt;li&gt;&lt;a href="#"&gt;&lt;span className="glyphicon glyphicon-user"&gt;&lt;/span&gt; Username&lt;/a&gt;&lt;/li&gt;<font></font>
                    &lt;/ul&gt;<font></font>
                &lt;/div&gt;<font></font>
            &lt;/nav&gt;<font></font>
        );<font></font>
    }<font></font>
});<font></font>
<font></font>
ScheduleEntryList = React.createClass({<font></font>
    getInitialState: function() {<font></font>
        return {data: []}<font></font>
    },<font></font>
<font></font>
    loadData: function() {<font></font>
        $.ajax({<font></font>
            url: "/api/tasks",<font></font>
            dataType: "json",<font></font>
<font></font>
            success: function(data) {<font></font>
                this.setState({data: data});<font></font>
            }.bind(this),<font></font>
<font></font>
            error: function(xhr, status, error) {<font></font>
                console.error("/api/tasks", status, error.toString());<font></font>
            }.bind(this)<font></font>
        });<font></font>
    },<font></font>
<font></font>
    componentWillMount: function() {<font></font>
        this.loadData();<font></font>
        setInterval(this.loadData, 20000);<font></font>
    },<font></font>
<font></font>
    render: function() {<font></font>
        items = this.state.data.map(function(item) {<font></font>
            return &lt;ScheduleEntryListItem item={item}&gt;&lt;/ScheduleEntryListItem&gt;;<font></font>
        });<font></font>
<font></font>
        return (<font></font>
            &lt;div className="list-group"&gt;<font></font>
                &lt;a className="list-group-item active"&gt;<font></font>
                    &lt;h5 className="list-group-item-heading"&gt;Upcoming&lt;/h5&gt;<font></font>
                &lt;/a&gt;<font></font>
                {items}<font></font>
            &lt;/div&gt;<font></font>
        );<font></font>
    }<font></font>
});<font></font>
<font></font>
ScheduleEntryListItem = React.createClass({<font></font>
    openModal: function() {<font></font>
        $("#scheduleentry-modal").modal("show");<font></font>
    },<font></font>
<font></font>
    render: function() {<font></font>
        deadline = moment(this.props.item.deadline).format("MMM Do YYYY, h:mm A");<font></font>
<font></font>
        return (<font></font>
            &lt;a className="list-group-item" href="#" onClick={this.openModal}&gt;<font></font>
                &lt;h5 className="list-group-item-heading"&gt;<font></font>
                    {this.props.item.title}<font></font>
                &lt;/h5&gt;<font></font>
                &lt;small className="list-group-item-text"&gt;<font></font>
                    {deadline}<font></font>
                &lt;/small&gt;<font></font>
            &lt;/a&gt;<font></font>
        );<font></font>
    }<font></font>
});<font></font>
<font></font>
Modal = React.createClass({<font></font>
    componentDidMount: function() {<font></font>
        $(this.getDOMNode())<font></font>
            .modal({backdrop: "static", keyboard: true, show: false});<font></font>
    },<font></font>
<font></font>
    componentWillUnmount: function() {<font></font>
        $(this.getDOMNode())<font></font>
            .off("hidden", this.handleHidden);<font></font>
    },<font></font>
<font></font>
    open: function() {<font></font>
        $(this.getDOMNode()).modal("show");<font></font>
    },<font></font>
<font></font>
    close: function() {<font></font>
        $(this.getDOMNode()).modal("hide");<font></font>
    },<font></font>
<font></font>
    render: function() {<font></font>
        return (<font></font>
            &lt;div id="scheduleentry-modal" className="modal fade" tabIndex="-1"&gt;<font></font>
                &lt;div className="modal-dialog"&gt;<font></font>
                    &lt;div className="modal-content"&gt;<font></font>
                        &lt;div className="modal-header"&gt;<font></font>
                            &lt;button type="button" className="close" data-dismiss="modal"&gt;<font></font>
                                &lt;span&gt;&amp;times;&lt;/span&gt;<font></font>
                            &lt;/button&gt;<font></font>
                            &lt;h4 className="modal-title"&gt;{this.props.title}&lt;/h4&gt;<font></font>
                        &lt;/div&gt;<font></font>
                        &lt;div className="modal-body"&gt;<font></font>
                            {this.props.children}<font></font>
                        &lt;/div&gt;<font></font>
                        &lt;div className="modal-footer"&gt;<font></font>
                            &lt;button type="button" className="btn btn-danger pull-left" data-dismiss="modal"&gt;Delete&lt;/button&gt;<font></font>
                            &lt;button type="button" className="btn btn-primary"&gt;Save&lt;/button&gt;<font></font>
                        &lt;/div&gt;<font></font>
                    &lt;/div&gt;<font></font>
                &lt;/div&gt;<font></font>
            &lt;/div&gt;<font></font>
<font></font>
        )<font></font>
    }<font></font>
});<font></font>
<font></font>
ScheduleEntryModal = React.createClass({<font></font>
    render: function() {<font></font>
        var modal = null;<font></font>
        modal = (<font></font>
            &lt;Modal title="Add Schedule Entry"&gt;<font></font>
                    &lt;form className="form-horizontal"&gt;<font></font>
                        &lt;div className="form-group"&gt;<font></font>
                            &lt;label htmlFor="title" className="col-sm-2 control-label"&gt;Title&lt;/label&gt;<font></font>
                            &lt;div className="col-sm-10"&gt;<font></font>
                                &lt;input id="title" className="form-control" type="text" placeholder="Title" ref="title" name="title"/&gt;<font></font>
                            &lt;/div&gt;<font></font>
                        &lt;/div&gt;<font></font>
                        &lt;div className="form-group"&gt;<font></font>
                            &lt;label htmlFor="deadline" className="col-sm-2 control-label"&gt;Deadline&lt;/label&gt;<font></font>
                            &lt;div className="col-sm-10"&gt;<font></font>
                                &lt;input id="deadline" className="form-control" type="datetime-local" ref="deadline" name="deadline"/&gt;<font></font>
                            &lt;/div&gt;<font></font>
                        &lt;/div&gt;<font></font>
                        &lt;div className="form-group"&gt;<font></font>
                            &lt;label htmlFor="completed" className="col-sm-2 control-label"&gt;Completed&lt;/label&gt;<font></font>
                            &lt;div className="col-sm-10"&gt;<font></font>
                                &lt;input id="completed" className="form-control" type="checkbox" placeholder="completed" ref="completed" name="completed"/&gt;<font></font>
                            &lt;/div&gt;<font></font>
                        &lt;/div&gt;<font></font>
                        &lt;div className="form-group"&gt;<font></font>
                            &lt;label htmlFor="description" className="col-sm-2 control-label"&gt;Description&lt;/label&gt;<font></font>
                            &lt;div className="col-sm-10"&gt;<font></font>
                                &lt;textarea id="description" className="form-control" placeholder="Description" ref="description" name="description"/&gt;<font></font>
                            &lt;/div&gt;<font></font>
                        &lt;/div&gt;<font></font>
                    &lt;/form&gt;<font></font>
            &lt;/Modal&gt;<font></font>
        );<font></font>
<font></font>
        return (<font></font>
            &lt;div className="scheduleentry-modal"&gt;<font></font>
                {modal}<font></font>
            &lt;/div&gt;<font></font>
        );<font></font>
    }<font></font>
});<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">感谢其他注释和对代码的改进。</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第3854篇《React.js中的Bootstrap模态》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">斯丁前端</span>
            <span class="discuss-time">2020.03.30</span>
          </div>
          <div class="discuss-comment"><p><a href="https://github.com/reactstrap/reactstrap" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Reactstrap </font></font></a><font style="vertical-align: inherit;"></font><a href="https://github.com/reactstrap/reactstrap/blob/master/src/Modal.js" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在React中</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">也有</font><a href="https://github.com/reactstrap/reactstrap/blob/master/src/Modal.js" rel="nofollow"><font style="vertical-align: inherit;">Bootstrap </font></a><a href="https://github.com/reactstrap/reactstrap" rel="nofollow"><font style="vertical-align: inherit;">Modals</font></a><font style="vertical-align: inherit;">的</font><a href="https://github.com/reactstrap/reactstrap/blob/master/src/Modal.js" rel="nofollow"><font style="vertical-align: inherit;">实现</font></a><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">该库以Bootstrap版本4为目标，而react-bootstrap目标版本为3.X。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">阳光小宇宙</span>
            <span class="discuss-time">2020.03.30</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您可以使用React-Bootstrap（</font></font><a href="https://react-bootstrap.github.io/components/modal" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">https://react-bootstrap.github.io/components/modal</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">）。</font><font style="vertical-align: inherit;">该链接上有一个模态示例。</font><font style="vertical-align: inherit;">加载react-bootstrap之后，可以将模式组件用作react组件：</font></font></p>

<pre><code>var Modal = ReactBootstrap.Modal;
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">然后可以用作的反应成分
 </font></font><code>&lt;Modal/&gt;</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">对于Bootstrap 4，有react-strap（</font></font><a href="https://reactstrap.github.io" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">https://reactstrap.github.io</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">）。</font><font style="vertical-align: inherit;">React-Bootstrap仅支持Bootstrap 3。</font></font></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
