---
title: 新建一个npm配置文件package.json
abbrlink: 7f3647cb
categories:
- 开发工具
date: 2018-05-13 17:23:48
tags: 
- 前端
---

如果需要在项目中使用npm的一些功能,一般有需要在项目里面添加一个`package.json`文件.它描述了项目目需要使用的npm模块,项目的基本信息等.

该文件可以手动添加,更方便一点的方式是在控制台使用如下命令:

```
    npm init
```

<!-- more -->
执行此命令后,会有一系列回答步骤,回答完毕后会在`package.json`中生成如下基本配置

```
    {
        /* 项目名称 */
        "name": "new-npm",

        /* 版本号 */
        "version": "1.0.0",

        /* 项目描述 */
        "description": "",

        /* 
            入口文件,如果改项目作为模块使用,其他
            项目依赖此项目时返回此路径中的文件
        */
        "main": "index.js",

        "scripts": {
            "test": "aaa"
        },

        /* 存放代码的地方 */
        "repository": {
            "type": "git",
            "url": "https://github.com/DiamondsMe/study.git"
        },

        /* 关键字,便于用户搜索到此模块 */
        "keywords": [
            "adfasf"
        ],

        /* 作者 */
        "author": "fasfd",

        /* 项目许可证 */
        "license": "ISC"
    }
```

## 参考文章

[package.json说明 by 张小伟][1]  
[对package.json的理解和学习][2]

[1]: https://www.cnblogs.com/bydzhangxiaowei/p/8729210.html "Markdown"
[2]: https://www.cnblogs.com/whkl-m/p/6617540.html "Markdown"