---
title: 解决ios设备设备下页面滚动问题
abbrlink: 3d040cbc
categories:
- 前端
date: 2020-07-07 23:02:46
tags:
- 前端
- css
---

如果你在safari浏览器和app内核浏览器中对需要滚动的元素设置如下样式时

    overflow|overflow-x|overflow-y:scroll;

你会发现滚动区域的表现极其差劲,滚动在手指抬起时立即停止,不产生惯性滚动.

这时可以在以上样式的基础上通过添加`-webkit-overflow-scrolling: touch;`属性来实现ios下的惯性滚动效果.

    overflow:scroll;
    -webkit-overflow-scrolling: touch;
    
分析详见: https://juejin.im/post/5c6ebc8af265da2dec623d51