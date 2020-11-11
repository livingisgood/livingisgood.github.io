---
layout: post
title: win10下使用Jekyll写博客
categories: 
 -备忘
permalink: /posts/Set-up-blog-on-win10
---

简单的方法是在win10中打开wsl功能,安装ubuntu.

目前我使用的是WSL1,优点是跨系统文件IO比较快,另外因为不需要用到Hyper-V,不会影响模拟器的使用.

wsl中使用git拉取github上的博客仓库到本地

wsl中用apt-get 安装jekyll

在博客仓库目录尝试直接jekyll serve

报错, 原因是缺少一个github-pages的依赖

用gem install命令安装, 中途build会失败,原因是缺少zlib库

apt-get无法找到名为zlib的包, 经搜索知道用这个包名zlib1g-dev

安装好了以后 jekyll serve应当可以工作了. 

如果还是报错, 按照提示在命令前加上 bundle exec即可

