---
title: "Auto CAD - 出电子版蓝图使用方法"
subtitle: ""
date: 2021-12-26T12:13:40+08:00
lastmod: 2021-12-26T12:13:40+08:00
author: "守正"
slug: "cad_electronic_blueprint"
tags: ["Auto CAD"]
categories: ["Work"]
featuredImage: ''
---

仅作为项目内部使用，勿作他用，否则后果自负……

<!--more-->

{{< admonition type=tip title=提示 open=true >}}
本教程原创于源泉设计4群 - 悟空老师
{{< /admonition >}}

## 设置打印线型

按自己的画图标准将平常用的出图线型修改以下内容：

选中`1~255`号色，将颜色设置为`RGB：72,120,170`，然后另存为「xx电子版蓝图.ctb」

{{< imgcapcdn src=`/Posts/Work/AutoCAD/07_blueprint/2021-12-26_12-28-04.png` alt=打印线型设置 width=60% >}}

使用刚刚另存的打印样式进行打印预览，效果如下：

{{< imgcapcdn src=`/Posts/Work/AutoCAD/07_blueprint/2021-12-26_12-30-13.webp` alt=打印预览 width=95% >}}

## 打印图纸为PDF文件

不管是采用批量打印的方式，还是`CTRL+P`单张打印，或者是通过[图纸集](#参考链接)发布到`PDF`；

具体采用什么软件来进行批量打印，本文不做展开，根据自己的使用习惯操作；

总之，只有一个目的，就是将我们的`CAD`图纸转为`PDF`文件；

### 举个栗子

我使用的是[源泉设计](http://www.yqarch.cn/)的批量打印；

**第一步** 打开需要打印的图纸文件；

**第二步** 在加载好「源泉插件」的情况下，按快捷键`BPT`启动批量打印；

**重点一** 打印机要选择打印成`PDF`的虚拟打印机；

{{< imgcapcdn src=`/Posts/Work/AutoCAD/07_blueprint/2021-12-28_19-51-25.png` alt=打印成PDF的虚拟打印机 width=60% >}}

**重点二** 打印线型需要选择刚刚设置好的，名为「xx电子版蓝图.ctb」线型；
 
{{< imgcapcdn src=`/Posts/Work/AutoCAD/07_blueprint/2021-12-28_19-51-54.png` alt=批量打印设置界面 width=75% >}}

**第五步** 框选需要打印的图纸，开始批量打印；

## 添加蓝图底色

打印出来的`PDF`线条已经是蓝色的了，接下来我们需要将`PDF`图纸的背景色也变成蓝色，模拟蓝图的样式；

这里我以`Adobe Acrobat Pro DC`软件这款软件为例：

**第一步** 用`Adobe Acrobat Pro DC`软件打开上一步准备好的`PDF`文件；

**第二步** 依次点击「编辑PDF」 --> 「更多」 --> 「背景」 --> 「添加」；

<img class=l-img src={{< param cdnPrefix >}}/Posts/Work/AutoCAD/07_blueprint/2021-12-28_20-19-20.webp alt=img width=95% >

**第三步** 选择「从颜色」 --> 「其他颜色」；

<img class=l-img src={{< param cdnPrefix >}}/Posts/Work/AutoCAD/07_blueprint/2021-12-28_20-20-03.png alt=img width=85% >

**第四步** 自定义颜色，颜色值为：`R=184 G=203 B=218`，点击确定；

<img class=l-img src={{< param cdnPrefix >}}/Posts/Work/AutoCAD/07_blueprint/2021-12-28_20-20-28.png alt=img width=60% >

{{< admonition type=tip title=小提示 open=true >}}
设置好颜色值后，可以点击「添加颜色到自定义颜色」，以后就可以直接在「自定义颜色」总选择我们预定义好的颜色；
{{< /admonition >}}

**第五步** 最后点击「保存」，我们的`PDF`文件就变成蓝图的样子了；

{{< imgcapcdn src=`/Posts/Work/AutoCAD/07_blueprint/2021-12-28_20-21-08.webp` alt=完成效果 width=95% >}}

## 添加图章及签名

**第一步** 用`Adobe Acrobat Pro DC`软件打开`PDF`图纸文件；

**第二步** 依次点击「编辑PDF」 --> 「添加图像」；

<img class=l-img src={{< param cdnPrefix >}}/Posts/Work/AutoCAD/07_blueprint/2021-12-28_20-38-41.webp alt=img width=95% >

**第三步** 在弹出的窗口选择需要添加的图章文件（PNG格式）；

<img class=l-img src={{< param cdnPrefix >}}/Posts/Work/AutoCAD/07_blueprint/2021-12-28_20-39-07.webp alt=img width=75% >

**第四步** 鼠标选择添加的图章，通过「旋转」、「移动」到适合的位置即可；

<img class=l-img src={{< param cdnPrefix >}}/Posts/Work/AutoCAD/07_blueprint/2021-12-28_20-42-02.webp alt=img width=95% >

**第五步** 最后点击「保存」，我们的`PDF`文件图纸就是蓝图且签好章的了；

{{< imgcapcdn src=`/Posts/Work/AutoCAD/07_blueprint/2021-12-28_20-42-21.webp` alt=完成效果 width=95% >}}

{{< admonition type=tip title=小贴士 open=true >}}
在添加图章的时候，可以提前用`Photoshop`把相应需要签字人的手写体抠图，然后复制到图章内正确的位置，调整适合的大小；

一般签名应为**黑**色，章为**红**色；

修改完毕后，另存为`PNG`格式；

在**第三步**的时候选择带有签名的`PNG`文件；
{{< /admonition >}}

## 图章文件下载

{{< admonition type=info title=` 百度云` open=false >}}

- **链　接：** <https://pan.baidu.com/s/1h0l3C2P7FEPWBKXokCyIfQ> 
- **提取码：** cf25

{{< /admonition >}}

{{< admonition type=info title=` 蓝奏云` open=false >}}

- **链　接：** <https://cajun.lanzouq.com/inp35y2s7bc>
- **密　码：** dikf

{{< /admonition >}}

## 参考链接

- [Auto CAD - 图纸集的正确使用方法](https://ll.sc.cn/posts/cad-drawings-instructions/)