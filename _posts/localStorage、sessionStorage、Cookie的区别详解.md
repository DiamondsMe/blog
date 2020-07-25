---
title: localStorage、sessionStorage、Cookie的区别详解
categories: uncategorized
tags:
  - javascript
abbrlink: e9431e4e
date: 2020-07-22 14:01:23
---

localStorage、sessionStorage、Cookie共同点:

都保存在浏览器端，且是同源的（顺便解释一下同源：域名、协议、端口号相同）

localStorage、sessionStorage、Cookie不共同点:

- 存储大小的不同：

localStorage的大小一般为5M
sessionStorage的大小一般为5M
cookies的大小一般为4K

- 有效期不同：

localStorage的有效期为永久有效，除非你进行手动删除。
sessionStorage在当前会话下有效，关闭页面或者浏览器时会被清空。
cookies在设置的有效之前有效，当超过有效期便会失效

- 与服务器端的通信

localStorage不参与服务器端的通信。
sessionStorage不参与服务器端的通信。
cookies参与服务器端通信，每次都会携带http的头信息中。（如果使用cookie保存过多数据会带来性能问题）

- localStorage和sessionStorage的作用域的区别详解

不同浏览器无法共享localStorage或sessionStorage中的信息。
相同浏览器的不同页面间可以共享相同的 localStorage（页面属于相同域名和端口），但是不同页面或标签页间无法共享sessionStorage的信息。


## 参考文章

[localStorage、sessionStorage、Cookie的区别详解][1]

[1]: https://blog.csdn.net/qq_26941173/article/details/88369543 "Markdown"