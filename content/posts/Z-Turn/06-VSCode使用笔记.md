---
title: "VSCode - 使用笔记"
subtitle: ""
date: 2021-10-31T15:22:05+08:00
lastmod: 2022-09-18T22:40:15+08:00
author: "守正"
authorLink: ""
description: ""
slug: "vscode_use_notes"
tags: ["VSCode"]
categories: ["Z-Turn"]
---
在使用 VSCode 过程中学习的一些笔记分享……

<!--more-->

## 插件安装

### Markdown All in One

<img class=l-img src={{< param cdnPrefix >}}/Posts/Z-Turn/04_VSCode/2021-11-15_19-39-07.png alt=img width=65% >

#### 特点

1. 提供了常用操作便利的快捷键；
2. 支持目录；
3. 一边书写一边预览(`Ctrl + Shift + V` or `Ctrl + K V`)；
4. 可轻松转换为 `HTML`文件和 `PDF`文件；
5. 优化了 `List editing`的编辑；
6. 可格式化 `table` (`Alt+Shift+F`) 以及 `Task list` (`use Alt+C to check/uncheck a list item`)；
7. 支持特殊数学符号渲染；

#### 常用快捷键

```Text
Ctrl + B　　　　　　粗体
Ctrl + I　　　　　　斜体
Alt + S　　　　　　 删除线
Ctrl + Shift + ]　 标题(uplevel)
Ctrl + Shift + [ 　标题(downlevel)
Ctrl + M　　　　　　切换数学环境
Alt + C　　　　　　 选中/取消选中任务列表项
```

### Office Viewer

该扩展在 `VScode`内集成 `Vditor`, 实现了对 `Markdown`的所见即所得编辑；

#### 使用说明

* 编辑方式: 直接通过`VScode`打开`md`文件
* 编辑器内, 通过`Ctrl+`单击或者双击可打开超链接
* 需要临时使用`VSCode`内置编辑器, 可点击以下按钮
* 点击以下按钮可将`Markdown`导出为`PDF`, 需要机器上有安装`Chrome`或`Edge`浏览器

{{< admonition type=warning title=注意 open=true >}}
安装后需重启成效。
{{< /admonition >}}

#### 缓存说明

由于 `VScode`每次加载 `WebView`会缓存文件, 这个扩展每次会生成 `3M`多, 建议定期进行清理, 打开缓存路径删除所有文件。

**缓存路径:** C:\Users[用户名]\AppData\Roaming\Code\Service Worker\CacheStorage

**项目地址：** [https://github.com/cweijan/vscode-office](https://github.com/cweijan/vscode-office)

## 使用技巧

### 自定义用户代码片段

只是写好片段后要打开 `Markdown` 的 `QuickSuggestions` 选项

`Ctrl+P` 打开 `VSCode` 的 `Settings.json` ,添加

```
"[markdown]":{
 	"editor.quickSuggestions": true
},
```

### 自动保存

设置 --> 常用设置 --> `files.autoSave` --> `onWindowChange`(窗口失去焦点自动保存)；

<img class=l-img src={{< param cdnPrefix >}}/Posts/Z-Turn/04_VSCode/2021-11-15_19-45-04.png alt=img width=60% >

### 自动换行显示

将 `VSCode` 中 `Editor:WordWrap` 选项更改为 `on` 即可。

**方法** ：打开 `VSCode`，在 `Search settings` 中搜索 `Editor:WordWrap` 即可找到该选项，更改成 `on` 即可。

**快捷键** : `alt + Z`

## 解决报错

### unins000.exe 尝试在目标目录创建文件时出错

`VS Code` 运行时会弹出 `unins000.exe` 尝试在目标目录创建文件时出错；

<img class=l-img src={{< param cdnPrefix >}}/Posts/Z-Turn/04_VSCode/2021-11-05_16-11-43.png alt=img width=60% >

解决办法是，为 `VS Code` 的安装目录权限添加 `Everyone` 用户完全控制就可以了。

**第一步** 右键安装目录文件夹 --> 属性，如图示依次点击「安全」 -- > 编辑 --> 在弹出的新窗口点击「添加」；

<img class=l-img src={{< param cdnPrefix >}}/Posts/Z-Turn/04_VSCode/2021-11-05_16-12-50.png alt=img width=95% >

**第二步** 点击「高级」；

<img class=l-img src={{< param cdnPrefix >}}/Posts/Z-Turn/04_VSCode/2021-11-05_16-14-38.png alt=img width=65% >

**第三步** 点击「立即查找」 --> 选择 `Everyone` --> 点击「确定」；

<img class=l-img src={{< param cdnPrefix >}}/Posts/Z-Turn/04_VSCode/2021-11-05_16-15-23.png alt=img width=65% >

**第四步** 回到安全窗口，选择 `Everyone` 用户，勾选「完全控制」权限；

<img class=l-img src={{< param cdnPrefix >}}/Posts/Z-Turn/04_VSCode/2021-11-05_16-15-40.png alt=img width=65% >

## Markdown 部分

### MD033 html标签警告

**一、问题**：

在 `Vscode` 中使用 `Markdownlint` 插件进行代码分析，当使用了 `Html` 标签时，插件会给出 `Md033/No-Inline-Html` 警告（没错，就是那种强迫症最讨厌的黄色波浪线）。

{{< imgcapcdn src=`/Posts/Z-Turn/04_VSCode/2021-10-30_15-24-20.png` alt=比如这样 >}}

**二、原因**：

插件作者的意图是为了使 `Markdown` 文件是纯 `Markdown` 的，避免在使用 `Html` 以外的方式渲染时出错；

{{< imgcapcdn src=`/Posts/Z-Turn/04_VSCode/2021-10-30_15-44-07.png` alt=官方解释 >}}

**三、解决方法**：

**第一步** 打开设置文件：左侧栏「扩展」（快捷键：Ctrl+Shift+X） --> 点击 Markdown All in One 右边的齿轮 --> 扩展设置 --> 在settings.json中编辑；

{{< imgcapcdn src=`/Posts/Z-Turn/04_VSCode/2021-10-30_15-51-03.webp` alt=打开设置文件 >}}

**第二步** 在设置的 `.json` 文件中添加如下代码：

```json
"markdownlint.config": {
    "default": true,
    "MD033": {
      "allowed_elements": [ "font", "li", "table", "tr", "td", "center", "br" ]
    }
},
```

其中 `"allowed_elements"` 的列表中填入不想提出警告的 `Html` 标签，按自己需要进行修改；

保存修改后，`Markdownlint` 将不再对 `"allowed_elements"` 中的 `Html` 标签提出警告。

### MD040 代码块警告

{{< imgcapcdn src=`/Posts/Z-Turn/04_VSCode/2021-10-30_16-00-35.png` alt=就像这样的 >}}

但是有些代码并不需要高亮，可以在 ``` 后面加上 `Text` ；

写为：**```Text**

### MD024 标题重复警告

**第一步** 打开设置文件：左侧栏「扩展」（快捷键：Ctrl+Shift+X） --> 点击 Markdown All in One 右边的齿轮 --> 扩展设置 --> 在settings.json中编辑；

{{< imgcapcdn src=`/Posts/Z-Turn/04_VSCode/2021-10-30_15-51-03.webp` alt=打开设置文件 >}}

**第二步** 在设置的 `.json` 文件中添加如下代码：

```json
"MD024": {
  "siblings_only": true,
},
```

### 换行

行尾最多可以增加两个空格，超过会给出警告，两个空格正好可以用于换行。

## 参考链接

- [Markdownlint全部警告解释](https://github.com/DavidAnson/markdownlint/blob/v0.21.0/doc/Rules.md)
- [Markdownlint Rules On Github](https://github.com/DavidAnson/markdownlint/blob/v0.21.0/doc/Rules.md#md033)
