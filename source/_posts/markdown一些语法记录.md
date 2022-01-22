---
title: markdown一些语法记录
author: Cici
avatar: https://gitee.com/ljv0606/cdn/raw/master/img/logo.webp
authorLink: /about
authorAbout: 小菜出击
authorDesc: 小菜出击
categories: 技术
comments: true
date: 2022-01-20 13:00:28
tags: note
keywords:
description: 存一些不常见用法和引用
photos: https://gitee.com/ljv0606/cdn/raw/master/img/b3.webp
---

#### 图片引用格式

```
# Markdown
![图片描述](图片地址)
# HTML
<img src="图片地址"/>
```
其中，图片地址可以使用图片的绝对或者相对路径，比如：
`/img/Mintimate_Logo.png`：到网站根目录下img文件夹找Mintimate_Logo.png图片来展示。
`../Mintimate_logo.png`：到上级目录找Mintimate_Logo.png图片来展示

#### 图床
gitee国内访问稳定，个人免费使用仓库总容量是5G，假设每个图像50K，5G大概可以存放104857张图像，完全够用，实在不够用的话，换个仓库存放就行了。问题不大<br>
github国内访问不稳定，仓库容量也有上述问题，但是都无所谓，不够用重新新建一个就可以了。<br>
参考链接：
首选：github,gitee,Pigo：https://blog.csdn.net/qq_33188180/article/details/122591105<br>
github+Pico+jsdelivr：https://zhuanlan.zhihu.com/p/350598351

github图床地址：https://cdn.jsdelivr.net/gh/acdefg/cdn

作为图床的仓库最好不能超过 1G，因为仓库超过 1G 后会有人工审核仓库内容。一旦发现用于图床可能会被删库也可能会被封号！！！所以建议在 1G 之前就换个仓库

#### 表情
github的markdown支持的emoji：https://gist.github.com/rxaviers/7360908
言文字：https://www.fuhaozi.cn/yanwenzi/
emoji表情：http://emojixd.com/group/smileys-emotion#h-face-neutral-skeptical