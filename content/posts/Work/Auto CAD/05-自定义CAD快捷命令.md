---
title: "Auto CAD - 自定义快捷命令"
subtitle: ""
date: 2021-11-18T19:57:37+08:00
lastmod: 2021-11-18T19:57:37+08:00
author: "守正"
slug: "cad_short_command"
tags: ["Auto CAD"]
categories: ["Work"]
---

画CAD有两种方式：通过鼠标点击命令按钮来作图，或者是使用命令行。命令行作图便捷、快速、易于思路连贯，是首选。但有些命令行命令很长，输入它反倒还使作图速度减慢。

<!--more-->

## 背景

CAD本身提供的命令行快捷键有限，有很多的CAD命令都很长，难以记忆且不能快速输入，大大降低了我们日常工作的效率；

这个时候，就可以自行设置，接下来介绍两种可以快速自定义短命令的方法。

## 操作方法

### 自定义命令的原则

> 1. 不要直接修改CAD本身的快捷命令、可以在原有的基础上添加；
>
> 2. 设置的快捷命令不要与CAD本身命令或加载的插件命令冲突；
>
> 3. 设置的快捷命令以简单便捷为主、推荐设置“左手键”，可以大大提高绘图效率；

### 自定义快捷命令

打开 `CAD` --> 菜单栏「工具」 --> 自定义 --> 编辑程序参数（`acad.pgp`）；

<img class=l-img src={{< param cdnPrefix >}}/Posts/Work/AutoCAD/05_CAD_Short_command/2021-11-18_20-04-25.png alt=img width=60% >

**第一步** 打开 `acad.pgp` 文件如下图：

{{< imgcapcdn src=`/Posts/Work/AutoCAD/05_CAD_Short_command/2021-11-18_20-05-22.png` alt="acad.pgp 文件" width=80% >}}

{{< admonition type=info title=提示 open=true >}}

**逗号**左侧为自定义的快捷命令；

**星号**右侧为对应的命令全称；

{{< /admonition >}}

**第二步** 将第一行复制并粘贴在上面空白处，并按自己需要进行修改；

{{< admonition type=tip title=提示 open=true >}}

快捷命令与命令全称不区分大小写、也无需与下方`CAD`默认命令对齐；

{{< /admonition >}}

### 使自定义快捷命令生效

快捷命令添加完成后，按 `Ctrl + S` 保存`acad.pgp`文件。

两种方式使编辑好的自定义命令生效：

**第一种** 关闭并重新启动`CAD`即可生效；

**第二种** 不关闭`CAD`状态下，输入 `reinit` 命令后勾选「PGP文件」，点击「确定」按钮即可；

[重新植入pgp文件](/posts/cad-skills-problem/#重新植入pgp)

### 编辑lsp文件

在 `CAD` 的安装盘下找到`\Program Files\Autodesk\AutoCAD 2018\Support\acad2022.lsp`这个文件；

你可以用VB汇编语言设置自己的快捷键。无法在`acad.pgp`文件中更改的快捷键在这里都可以实现；

```vb
(princ)

(DEFUN C:V1 () (command "VPMAX"))

(DEFUN C:V2 () (command "PSPACE"))
```

{{< admonition type=info title=提示 open=true >}}

`C:xx` 后面为自定义的快捷命令；

`command "xxx"` 为对应的命令全称；

{{< /admonition >}}
