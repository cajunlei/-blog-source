---
title: "Sublime Text3 - 使用手册"
subtitle: ""
date: 2021-10-16T22:29:24+08:00
lastmod: 2021-10-19T22:29:24+08:00
author: "守正"
authorLink: ""
description: ""
slug: "sublime_text_manual"
tags: ["Sublime Text"]
categories: ["Z-Turn"]
featuredImage: "https://cdn.chiga.ga/Posts/Z-Turn/Sublime_Text_01/Cover.webp"
---

个人使用 Sublime Text3 过程中收集整理的一些技巧和方法。

<!--more-->

## 安装插件、卸载插件

### 安装 Package Control

打开 `Package Control` 的网页 <https://packagecontrol.io> ，点击右侧的 `Install Now` 按钮;

{{< imgcapcdn src=`/Posts/Z-Turn/Sublime_Text_01/2021-10-15_22-37-30.webp` alt="Package Control 官网" >}}

`Package Control` 为插件管理包，所以我们首先要安装它。有了它，我们就可以很方便的浏览、安装和卸载 `Sublime Text` 中的插件。官网安装步骤的一些相关说明，如下图所示：

{{< imgcapcdn src=`/Posts/Z-Turn/Sublime_Text_01/2021-10-15_22-38-26.webp` alt=官网安装步骤说明 >}}

**第一步** `Win` 系统，在`Sublime Text`中：同时按下`Ctrl + Shift + P`，会打开命令面板；

**第二步** 然后输入：`Install Package Control` ，按 `Enter` ，即会开始安装 `Package Control`；

**第三步** 等待 `Package Control` 安装完成。之后使用`Ctrl + Shift + P`打开命令板，输入`PC`应出现 `Package Control：`（如下图所示，即为安装成功）

{{< imgcapcdn src=`/Posts/Z-Turn/Sublime_Text_01/2021-10-15_22-50-03.png` alt=安装成功 width=80% >}}

### 安装插件

同时按`Ctrl + Shift + P`打开命令板，输入`PCIP`, 然后下选点击 `Package Control: Install Package`。

{{< imgcapcdn src=`/Posts/Z-Turn/Sublime_Text_01/2021-10-15_22-45-20.png` alt=安装插件 width=80% >}}

会出现一个输入框，输入你想要安装的插件，然后选择它，即可进行安装。

### 卸载插件

卸载比较容易，同时按`Ctrl + Shift + P`打开命令板，输入`PCRP`然后然后下选点击 `Package Control: Remove Package` ;

{{< imgcapcdn src=`/Posts/Z-Turn/Sublime_Text_01/2021-10-15_22-47-25.png` alt=卸载插件 width=80% >}}

然后选择你要卸载的插件，就可以卸载了。

{{< imgcapcdn src=`/Posts/Z-Turn/Sublime_Text_01/2021-10-15_22-52-18.png` alt=已安装插件 width=80% >}}

## 失去焦点自动保存

**第一步** `Preference`（首选项）-> `Settings`（设置）；

{{< imgcapcdn src=`/Posts/Z-Turn/Sublime_Text_01/2021-10-15_23-35-03.png` alt=打开设置文件 width=50% >}}

**第二步** 打开的界面是分两边的，左边是只读的不能编辑，在左边区域`Ctrl + F`（查找），然后在下面输入框里输入 `save_on_focus_lost`；

{{< imgcapcdn src=`/Posts/Z-Turn/Sublime_Text_01/2021-10-15_23-36-52.webp` alt=查找代码 >}}

**第三步** 复制这行代码到右边的框里，然后把 `false` ,改成 `true` ，保存后关闭窗口，大功告成，今后就不用手动`Ctrl + S`了，Nice!！！

{{< imgcapcdn src=`/Posts/Z-Turn/Sublime_Text_01/2021-10-15_23-38-59.webp` alt=修改完成 >}}

{{< admonition type=Tip title=" Tips:" open=true >}}

懒得查找的，也可以直接复制下面这段代码粘贴到右边区域，保存关闭窗口即可；

{{< /admonition >}}

```Text
"save_on_focus_lost": true,
```

## 实现 Markdown 编辑和实时预览

### 安装所需的插件

按下`Ctrl + Shift + P`打开快速菜单，输入 `pcip`：

{{< imgcapcdn src=`/Posts/Z-Turn/Sublime_Text_01/2021-10-15_22-45-20.png` alt=安装插件 width=80% >}}

回车，等待数据更新，完成后会主动显示软件列表。

在里面输入以下软件名称并回车进行安装：

```Text
Markdown Editing      // Markdown编辑和语法高亮支持
OmniMarkupPreviewer   //本地hsot实时预览
Markdown Preview      // Markdown导出html预览支持 
auto-save             // 可自定义的自动保存功能 
```

耐心等待操作完成，之后关闭并重新打开 `Sublime Text 3`.

前两个是标准的 `Markdown` 编辑与预览工具，第三个是实现实时预览的关键。

{{< imgcapcdn src=`/Posts/Z-Turn/Sublime_Text_01/2021-10-16_15-36-38.png` alt="安装好的 Markdown 插件" width=80% >}}

### 实现实时预览

#### 方法一

安装 `OmniMarkupPreviewer` 插件;

> 在浏览器中预览：Ctrl + Alt + O
>
> 导出HTML：Ctrl + Alt + X
>
> 标记拷贝至剪贴板：Ctrl + Alt + C

- 便可以实现实时预览；

<img class=l-img src={{< param cdnPrefix >}}/Posts/Z-Turn/Sublime_Text_01_20200416135738564.png alt=img width=95% >

- 输出样式的修改

默认情况下，在目录 `OmniMarkupPreviewer` -> `Public` 下，修改 `Github.css` 文件即可。

如果想要修改控制样式输出的 `.css` 文件，可以在首选项 -> 插件设置 -> `OmniMarkupPreviewer` -> `Settings-User` 中修改 `html_template_name` 选项对应的文件名即可。

{{< admonition type=warning title="注意：" open=true >}}

上面的修改只是修改了你在浏览器中的预览的样式，如果想要同步修改输出的样式
默认情况下，在目录 `OmniMarkupPreviewer` -> `templates` 下，修改 `github-export.tpl` 文件即可。
比如：想要修改输出 `HTML` 中内容区域的整体宽度，就需要同时修改 `github.css` 和 `github-export.tpl` 这两个文件中的 `.container` 的 `max-width` 的值即可。这样就可以保证在预览和导出时的样式都是一致的。

{{< /admonition >}}

#### 方法二

更改 `MarkdownPreview.sublime-settings`, 启用 `enable_autoreload`

依次点击 `Preference`（首选项）--> `Package Settings` --> `Markdown Preview` --> `Settings` ，打开 `Markdown Preview` 设置文件；

{{< imgcapcdn src=`/Posts/Z-Turn/Sublime_Text_01/2021-10-16_15-44-39.png` alt=打开设置文件 width=65% >}}

输入以下代码：

```Text
"enable_autoreload": true,
```

{{< imgcapcdn src=`/Posts/Z-Turn/Sublime_Text_01/2021-10-16_15-46-29.png` alt=输入代码 width=80% >}}

### 如何打开预览

我们使用 `Markdown Preview` 插件来打开浏览器进行预览：

按下`Ctrl + Shift + P`打开快速菜单，键入 `mp`；

{{< imgcapcdn src=`/Posts/Z-Turn/Sublime_Text_01/2021-10-16_15-54-34.png` alt="选择 Markdown Preview" width=80% >}}

选择 `Markdown`;

{{< imgcapcdn src=`/Posts/Z-Turn/Sublime_Text_01/2021-10-16_15-55-02.png` alt="选择 Markdown" width=80% >}}

### 自定义快捷键

直接在浏览器中预览效果的话，可以自定义快捷键：点击 `Preferences`（首选项）--> 选择 `Key Bindings User`（快捷键设置）：

{{< imgcapcdn src=`/Posts/Z-Turn/Sublime_Text_01/2021-10-16_17-04-43.png` alt=打开快捷键设置 width=40% >}}

输入一下代码；

```Text
{ "keys": ["alt+m"], "command": "markdown_preview", "args": {"target": "browser", "parser":"markdown"} },
```

<br>

{{< imgcapcdn src=`/Posts/Z-Turn/Sublime_Text_01/2021-10-16_17-07-59.png` alt=输入代码 >}}

保存后，直接输入快捷键：`Alt + M`就可以直接在浏览器中预览生成的`HTML`文件了。

### 实现浏览器自动刷新

对于浏览器而言，我们让它自动刷新只需在`md`文件最下面加入一行：

```Text
<meta http-equiv="refresh" content="0.1">
```

`0.1` 负责表示刷新间隔，单位是秒，这是一个比较合适的设定值。

太快的话我们难以滚动页面，太慢的话有可能体验很差。

为了不让滚动时编辑的新文字触底，可以在最后一行的刷新代码之上打好几个占空间的行即可。

由于空行不会被解析，在每一行之前放一个字符`#`或者打三个以上的减号表示分割线。

### md文档到html文件的自动更新

这里我们用到了一个叫做 `Auto-Save` 的插件，它可以针对一个文档实现空闲 x 秒后自动保存。

我们打开 `Auto-Save` 的默认设置和用户设置文件：

依次点击` Preference`（首选项）--> `Package Settings` --> `Auto-save` -->打开 `Settings-Defualt` 和 `Settings-User`;

{{< imgcapcdn src=`/Posts/Z-Turn/Sublime_Text_01/2021-10-16_17-33-21.png` alt="Auto-save设置" width=75% >}}

将 `Default` 的内容复制粘贴到 `User` 里面，并复制以下代码到 `User` 设置文件：

{{< imgcapcdn src=`/Posts/Z-Turn/Sublime_Text_01/2021-10-16_17-29-19.png` alt="Default 文件" width=75% >}}

{{< imgcapcdn src=`/Posts/Z-Turn/Sublime_Text_01/2021-10-16_17-29-39.png` alt="User 文件" width=75% >}}

```Text
"auto_save_delay_in_seconds": 0.15,
```

经过实测，`0.15` 是一个比较能接受的值，不会对磁盘造成频繁读写的影响，延迟也不大。

最后就是打开本文档的自动保存功能了：

按下`Ctrl + Shift + P`打开快速菜单，键入 `auto`；

{{< admonition type=Tip title=" Tips:" open=true >}}

如果是写带图片的文章，反复刷新会影响使用，我一般写博客是打开生成本地静态文件，用浏览器预览，采用[失去焦点自动保存](/posts/sublime-text-manual/#二失去焦点自动保存) ，体验更佳。

{{< /admonition >}}
