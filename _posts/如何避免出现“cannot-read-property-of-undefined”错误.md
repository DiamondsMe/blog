---
title: 如何避免出现“cannot read property of undefined”错误
abbrlink: c9529d69
categories:
- 前端
date: 2020-07-07 22:12:02
tags:
- javascript
---
# 如何避免出现“cannot read property of undefined”错误

开发时经常会出现某对象属性为undefined,而继续获取下一层属性时导致报错,有以下方案可以避免错误的发生

## 使用方法库

lodash中的_.get或者Ramda 里的 R.path方法;  
但有时只是想单纯避免出现这个错误,而不想引入整合类库造成不必要的浪费.

<!-- more -->
## 使用 && “短路”

使用`&&`符号,例如:

    meals.breakfast && meals.breakfast.protein

但是会导致获取属性值时有重复的代码,比如前面的`meals.breakfast`

## 使用“或单元”

同上是一种特殊的代码结构,在每个`||`后都有一个默认值防止报错,例如:

    ((favorites.reading||{}).books||[])[0],

然而此方案代码可读性较差;

## 使用try/catch

此方案检查单个属性可用,多个属性写在里面无法排查错误位置;

## 未来展望

可选链式调用:TC39 提案中的一个功能,例如

    favorites?.video?.shows[0];

## 参考文章

[避免那些可恶的 "cannot read property of undefined" 错误][1]

[1]: https://juejin.im/post/5c810170e51d450a453fb48e "Markdown"