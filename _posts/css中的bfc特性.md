---
title: css中BFC特性
abbrlink: 5d5065d5
categories: 
- 前端
date: 2020-07-08 19:33:57
tags:
- 前端
- css
---
bfc，即块格式化上下文。浏览器满足一定的条件时会形成一种叫块渲染区域,它会按照一定的规则进行渲染,它拥有以下特性:
- BFC的块不会和浮动块重叠;
- 计算BFC元素的高度时，会包括浮动元素;
- 在一个BFC下的块 margin 会发生重叠，不在同一个则不会;
- BFC元素是一个独立的容器，使得里面的元素和外部元素隔离开，互补影响
<!-- more -->

它具有一下形成条件:

- float 的值不为 none;
- overflow 的值为 auto, scroll和 hidden
- display 的值为 table-cell, table-caption和 inline-block
- position 设置为 absolute和 fixed

bfc特性的应用详见:
[如何理解CSS中的BFC特性][1]  

[1]: https://juejin.im/post/5c7a84b1518825629f3877a0 "Markdown"