---
title: "CCleaner 说明"
subtitle: ""
date: 2022-10-17T11:10:51+08:00
lastmod: 2022-10-17T11:10:51+08:00
# draft: true
author: "守正"
slug: "ccleaner_manual"
tags: ["CCleaner"]
categories: ["Software"]
featuredImage: ''
---

CCleaner 是一组最新的系统优化和隐私保护工具。

它用于清理操作系统中的碎片。在他们的工作中，它正在寻找并删除未使用的文件。这些包括 cookie、历史记录、IE 中的访问站点、临时 Internet 文件、搜索字符串、文件、回收站等。

<!--more-->

## CCleaner 安装

1. 双击`CCleaner_onlinedown.exe`，选择语言并点击`OK`；

2. 下一步；

3. 选择想要安装的程序，并点击下一步；

4. 安装；

5. 这时候程序会弹出软件界面，选择**简体中文**语言，点击**安装**；

## CCleaner 注册

{{< admonition type=warning title=重要提示 open=true >}}
安装成功后，不要打开软件，同时也要确保正确关闭程序（从任务栏图标关闭）。
{{< /admonition >}}

1. 断开网络链接；

2. 运行`Pctch22`文件夹中的`cmd`程序；

3. 打开后，安装要求输入任意键直至程序关闭；

4. 将`Pctch22`文件夹中的另一个补丁，复制到`CCleaner Professional`软件安装根目录中（方法：右键桌面图标 → 属性 → 打开文件位置）；

5. 在根目录中，运行`ccleaner_patch22.exe`补丁；

{{< admonition type=warning title=注意 open=true >}}
容易被杀毒软件删除，需关闭杀毒软件，介意者勿用。
{{< /admonition >}}

6. 点击`Patch`；

7. 这时候可以看到已经成功了，点击`exit`退出该程序；

最后我们联网打开`ccleaner`软件，这里可以看到程序已经注册成功了。

{{< admonition type=note title=提示 open=true >}}
如果程序要更新，它将被放入没有注册商的版本中。只需下载最新版本并再次修补即可。
{{< /admonition >}}

## 下载地址

{{< admonition type=info title=下载地址 open=true >}}
https://cajun.lanzouv.com/ie7jY0e12vla
{{< /admonition >}}

## 禁止联网

打开**火绒** → 右上角**菜单** → **安全设置** → **系统防护** → **联网控制** → 添加规则；

添加以下程序，设置为**自动阻止**：

```
CCleaner.exe
CCleaner64.exe
CCUpdate.exe
```

## 参考链接

- [CCleaner官网](https://www.ccleaner.com/zh-cn)
