---
title: "Auto CAD - 关于参照的使用技巧"
subtitle: ""
date: 2021-11-02T16:35:47+08:00
lastmod: 2021-11-02T16:35:47+08:00
author: "守正"
authorLink: ""
description: ""
slug: "cad_xref_manager"
tags: ["Auto CAD"]
categories: ["Work"]
---

在绘图的过程中经常会用到 **参照**，如果没有正确使用参照文件，图纸发给别人就会出现参照文件丢失，比如图框显示不出来，那么该如何保证发出的图纸不丢失参照文件呢？

<!--more-->

## 批量修改参照文件路径

当参照文件被移动了位置过后，重新打开图纸，就会发现参照图形没了，变成了一串文字路径；

那么该如何解决这个问题呢？

如果打开每个文件手动修改参照路径，文件数量不多的时候还行；

但遇到大型项目，文件很多的时候这种方式就不可取了；

接下来就介绍一种非常方便快捷可批量操作的方法；

**第一步** 关闭所有的`CAD`文件；

**第二步** 按下`Win`键，输入「参照管理器」，点击打开；

{{< imgcapcdn src=`/Posts/Work/AutoCAD/04_CAD_XREF_Manager/2021-11-02_19-55-55.webp` alt=`搜索参照管理器` >}}

{{< imgcapcdn src=`/Posts/Work/AutoCAD/04_CAD_XREF_Manager/2021-11-02_19-56-59.webp` alt=`开始菜单找到参照管理器` >}}

**第三步** 点击左上角的「添加文件」；

{{< imgcapcdn src=`/Posts/Work/AutoCAD/04_CAD_XREF_Manager/2021-11-02_19-57-35.png` alt=`添加文件` >}}

**第四步** 将所有需要修改的文件添加到参照管理器；

{{< imgcapcdn src=`/Posts/Work/AutoCAD/04_CAD_XREF_Manager/2021-11-02_20-00-16.webp` alt=`添加需要修改的文件` >}}

选择「自动添加所有外部参照，而不管嵌套级别」；

{{< imgcapcdn src=`/Posts/Work/AutoCAD/04_CAD_XREF_Manager/2021-11-02_20-00-24.png` alt=添加所有外部参照 width=70% >}}

**第五步** 选择视图 --> 按参照类型列表，在左侧找到外部参照 --> 参照对象；

{{< imgcapcdn src=`/Posts/Work/AutoCAD/04_CAD_XREF_Manager/2021-11-02_20-02-42.png` alt=`` >}}

**第六步** 全选所有文件，点击鼠标右键，选择编辑选定的路径；

{{< imgcapcdn src=`/Posts/Work/AutoCAD/04_CAD_XREF_Manager/2021-11-02_20-03-09.png` alt=`编辑路径` >}}

**第七步** 在弹出的对话框点击右侧按钮，重新找到移动过后参照文件的位置，点击确定；

{{< imgcapcdn src=`/Posts/Work/AutoCAD/04_CAD_XREF_Manager/2021-11-02_20-03-32.png` alt=选择新的参照路径 width=50% >}}

**第八步** 最后点击工具栏的「应用修改」，操作完成；

{{< imgcapcdn src=`/Posts/Work/AutoCAD/04_CAD_XREF_Manager/2021-11-02_20-04-24.png` alt=`应用修改` >}}

打开我们的文件，这个时候所有丢失的参照文件就已经正常显示了。

## 批量绑定参照文件

**第一步** 打开一个 `CAD` 文件；

**第二步** 点击「文件」 --> 电子传递；

{{< imgcapcdn src=`/Posts/Work/AutoCAD/04_CAD_XREF_Manager/2021-11-02_23-40-13.png` alt=文件菜单 width=60% >}}

**第三步** 添加文件 --> 将我们需要绑定参照的文件添加进来，点击「传递设置」；

{{< imgcapcdn src=`/Posts/Work/AutoCAD/04_CAD_XREF_Manager/2021-11-02_23-54-27.webp` alt=`创建新的传递` >}}

**第四步** 点击「新建」；

<img class=l-img src={{< param cdnPrefix >}}/Posts/Work/AutoCAD/04_CAD_XREF_Manager/2021-11-02_23-43-24.png alt=img width=60% >

**第五步** 输入一个名称，确定；

<img class=l-img src={{< param cdnPrefix >}}/Posts/Work/AutoCAD/04_CAD_XREF_Manager/2021-11-02_23-43-27.png alt=img width=60% >

**第六步** 设置如下图所示：

{{< imgcapcdn src=`/Posts/Work/AutoCAD/04_CAD_XREF_Manager/2021-11-02_23-45-17.png` alt=`传递设置项` >}}

**第七步** 回到传递页面，选择刚刚创建的设置，点击确定开始创建；

**第八步** 选择保存位置，等待打包完成；

{{< imgcapcdn src=`/Posts/Work/AutoCAD/04_CAD_XREF_Manager/2021-11-02_23-48-59.png` alt=`打包中` >}}

**第九步** 打包完成的文件结构如下，同设置的时候选择；

{{< imgcapcdn src=`/Posts/Work/AutoCAD/04_CAD_XREF_Manager/2021-11-02_23-49-40.webp` alt=`打包完成的文件` >}}
