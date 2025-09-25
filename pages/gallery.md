---
layout: page
title: 画廊
subtitle: From the pexels folder
permalink: /gallery/
gallery_path: "assets/img/pexels"
feature-img: "assets/img/pexels/bg-little-universe.jpg"
excluded: true
position: 3
tags: [Page]
---

这是一个由`assets/img/pexels`文件夹中的静态文件组成的照片库。我想从文件夹中自动创建一个简单的库，而不必像创建投资组合那样创建一个标记页面。


{% include gallery.html gallery_path=page.gallery_path %}
