---
layout: post
title: 欢呼
tagline: I finished building and start bloging.
tag: blog
categories: [随笔]
---

## 欢迎访问

这是一湾刚刚起步的博客，内容以技术交流分享为主，辅以其他有趣的内容。

感谢Github、Jekyll、Twitter以及各位工程师前辈，让我可以顺利地搭建此博客。

本博客源码 [iwj.github.io](https://github.com/iwj/iwj.github.io)

## 部落主人有话说

前前后后折腾了好久，5月份正式上线啦。用来记录自己的拙见，也会分享一些有趣的或者酷酷的事物。

代码如诗，我现在还不太擅长写优雅的「诗」。 过于急躁，反而不利于成长。希望自己能将这种糟糕的情况降到最低，扎实地成长。

我喜欢交流和思考，想有个稳定的地方记录和分享自己的成长、思考、见解等等，这些记录可以鼓励自己。喜欢折腾的我，在知道`Word Press`之后就对第三方博客没有好感。总想有那么片自己掌控的土地，自己耕耘，正好`Github Pages`是一种上乘的载体。前段时间在前辈的博客里知道它，一番了解之后，心中暗暗欣喜，完美！

本人知道得还很少，当发现愚钝的错误时，前辈们请轻鄙，多多指教。

## 近期文章

<ul>
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>

## 其他

本博正在完善中，朝着发布高质量内容这个目标前进。
