---
title: 动态内容处理
date: '2012-09-15'
description:
categories:
- 技术
tags:
- pebble
---

传统CGI类应用，如PHP或者模板引擎，会根据上下文生成完整页面，并根据用户点击响应新的页面内容。这类应用很适合使用MVC框架，以状态页面为单位处理用户请求，一般配合页面静态化技术提高性能。2.0应用则倾向单页面配合Ajax请求，避免页面刷新，状态则由网页地址哈希来完成，后台一般也是REST服务。实验室里一般也都是2.0引用为主，配合Dojo做前台。所以在接触了WP和Pebble之后，十分地不适应。其核心问题是对动态内容的处理方式。

从经验上来说，涉及交互的动态内容最好使用JS来处理，避免页面加载过慢而影响用户体验；不涉及交互的内容，则在平衡初次加载时间的考量下，采用模板插入，如JSP、Velocity或XXXTemplate之类。JS的方式，对搜索引擎优化是个考验，毕竟那些实际的数据都变成了一对JSON或XML，如果不能提供对搜索引擎友好的HTML链接，那就糟糕了。模板的方式，则要考虑页面静态化，否则会占用过多的CPU和内存，而且从代码可读性和可维护性上来说，模板对于复杂内容网站来说，其实是很难懂的。

Pebble采用了JSP 2.0的写法，没有使用Scriptlet，主要功能通过标签完成。我倒不是不喜欢JSP，而且本地访问JSP页面，有时候真的是飞快。但是每个JSP自定义标签都会成为一个Java类，看起代码来真的很累。这种不把功能写在页面内，但实际逻辑还是紧密不分的行为，让我觉得有些自欺欺人。