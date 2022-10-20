---
title: "SVG - 学习笔记"
subtitle: ""
date: 2021-10-25T19:58:36+08:00
lastmod: 2021-10-25T19:58:36+08:00
author: "守正"
authorLink: ""
description: ""
slug: "svg_study_notes"
tags: ["SVG"]
categories: ["Study"]

hiddenFromHomePage: true
hiddenFromSearch: false
---

在学习 SVG 过程中的一些笔记分享……

<!--more-->

``` svg
<svg xmlns="http://www.w3.org/2000/svg">
<!-- 画布宽度 -->
    width="500px"
<!-- 画布高度 -->
    height="500px"
<!-- 盒子 -->
    viewBox="0 0 100 100"
<!-- 矩形：x,y起点坐标，宽度，高度 -->
    <rect x='10' y='10' width='20' height='10'/>
<!-- 多边形：起点坐标开始连线 -->
    <polygon points="0,0 10,0 20,5 5,5 0,0"/>
<!-- 圆:cx,cy中心坐标；r半径 -->
    <circle cx='20' cy='20' r='5'/>
<!-- 椭圆：cx,cy中心点坐标；rx横向半径；ry纵向半径 -->
    <ellipse cx='40' cy='30' rx="10" ry="50" />
<!-- 直线：x1,y1起点坐标；x2,y2终点坐标；填充；边框 -->
    <line x1="40" x2="0" y1="40" y2="0" 
    stroke="black" stroke-width="5"/>
<!-- 折现：起点坐标开始连线，自动闭合；填充颜色=透明；边框颜色；边框宽度 -->
    <polyline points="45,0 50,0 50,15 40,15" 
    fill="transparent"
    stroke="black" stroke-width="2"/>
<!-- 文字：位置；字体大小；内容 -->
    <text x="10" y="50" font-size="20">
        hello
    </text>
</svg>
```

{{< bilibili id=BV1Nz411b7sQ >}}
