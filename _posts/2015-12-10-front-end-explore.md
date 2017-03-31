---
layout: post
title: 前端探险
categories: [front-end, io]
---

## JavaScript 将会统治世界的

成长过程中，重心没有放在前端，按需学习的前端知识，凑不成一个完整的知识网。每次见到这句玩笑话，愉悦的同时，还会肃然起敬。

希望在温婉、慢热的前端学习过程中，可以少些不可思议的坑，而一般的坑，踩踩还是有好处的，可以增加经验，提升思维能力。

将遇到的印象深刻的经历记录下来，自己可以回味，也可以与人交流。将不断更新。

![fe](/img/front-end-exp.jpg "fe")

## HTML

null

## CSS

### 2016-05-15: flex 属性实现简单的、快速的布局

今天在给博客的分页器写样式的时候，想起了前几天问过阿黎的`flex`属性，是一个nice的属性，于是决定应用到这里。

用法是：给父容器设置`display: flex;`属性，表示这是一个`flex`盒模型，它的每个子元素都称为`flex item`，同时它的子元素的`float`、`clear`和`vertical-align`属性失效。

正好只有3个子元素，满足我的需求，我就取`justify-content: space-between;`这个用法，来实现，代码如下：

CSS：

~~~css
.flex-item{
  display: -webkit-flex; /* Safari */
  display: flex;
  justify-content: space-between;
}
~~~

HTML：

~~~html
<div class="flex-item">
  <span>上一页</span>
  <span>当前页：1</span>    
  <span><a href="/page2">下一页</a></span>     
</div>
~~~

> 实测 Safari 8.0 不支持这个属性

## JS

### 2015-12-10: jQuery 可以解决浏览器兼容问题

写了一段 js 代码，无意中发现在火狐下无法运行，原来火狐不支持 innerText 这个属性。

使用 jQuery 可以解决这个问题。

浏览器的兼容问题，可以解决一部分，并不是所有都可以。

## 视觉效果

null
