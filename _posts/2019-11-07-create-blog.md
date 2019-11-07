---
layout: post
title: '使用GitHub Pages+Jekyll搭建个人博客'
date: 2019-11-07
author: zsc
cover: 'http://on2171g4d.bkt.clouddn.com/jekyll-banner.png'
tags: zsc
---

> Transform your plain text into static websites and blogs.

### 创建一个github仓库，用来存放博客模板

1. 在 GitHub 上建立一个以 .github.io 为后缀的和你帐号名一样的代码仓库，如我的帐号是:sjqway，则建立的仓库名为:[sjqway.github.io]．

### 克隆别人的github里的模板

2. 在终端里写入git clone +别人的博客模板网址，克隆到本地文件夹，名为［sjqway.github.io］．

### 更新博客内容

3. 通过更改配置文件 ＿config.yml 修改里面的URL以及个人信息，通过修改或添加＿POSTＳ文件夹里的内容，可以更新博客所展示的文章．

### 预览博客内容

4.  终端进入本地文件夹 cd sjqway.github.io ，打开jekyll server，在本地浏览器输入https://127.0.0.1:4000 ，可以预览效果，

### 上传本地文件夹修改的内容到github仓库中

- git add .
- git commit
- git pull
- git push

最后提示

对象计数中: 20, 完成.
Delta compression using up to 4 threads.
压缩对象中: 100% (14/14), 完成.
写入对象中: 100% (20/20), 1.70 KiB | 868.00 KiB/s, 完成.

即为上传成功，输入＿ｃｏｎｆｉｇ文件中的ｕｒｌ地址，即可浏览博客．

