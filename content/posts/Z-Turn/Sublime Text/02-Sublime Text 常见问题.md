---
title: "Sublime Text3 - 常见问题"
subtitle: ""
date: 2021-10-17T19:12:06+08:00
lastmod: 2021-10-20T20:12:06+08:00
author: "守正"
authorLink: ""
description: ""
slug: "sublime_text_common_problem"
tags: ["Sublime Text"]
categories: ["Z-Turn"]
featuredImage: "https://cdn.chiga.ga/Posts/Z-Turn/Sublime_Text_02/2021-10-15_21-04-30.png"
---

关于在使用 `Sublime Text3` 所遇到的一系列报错等问题的解决办法。

<!--more-->

## 问题一

### 问题描述

打开 `Sublime Text3` 软件时或者安装插件时，弹出提示框：

{{< imgcapcdn src=`/Posts/Z-Turn/Sublime_Text_02/2021-10-15_21-04-30.png` alt=错误提示 width=75% >}}

```Text
Package Control
Unable to download XXX. Please view the console for more details. 
```

一番搜索后在 `Github` 上找到答案：

### 解决方法

{{< imgcapcdn src=`/Posts/Z-Turn/Sublime_Text_02_2019020116042854.png` alt=解决办法 >}}

**第一步** 打开 `Sublime Text3` ；

**第二步** 依次点击` Preference`（首选项）--> `ackage Settings` --> `Package Control` --> `Settings` ，打开设置文件；

{{< imgcapcdn src=`/Posts/Z-Turn/Sublime_Text_02/2021-10-15_17-08-21.png` alt=打开设置文件 width=65% >}}

**第三步** 在打开文件中添加下面以下代码；

```Text
"debug": true,
"downloader_precedence":    
    {
      "linux": [ "curl", "urllib",    "wget" ],
      "osx": [ "curl", "urllib" ],
      "windows": [ "wininet" ]
    },
```

**第四步** `Ctrl + S`保存即可；

{{< imgcapcdn src=`/Posts/Z-Turn/Sublime_Text_02/2021-10-15_22-02-37.png` alt=添加代码 width=80% >}}

**第五步** 重启 `Sublime Text3` ，问题解决。

## 问题二

### 问题描述

`Sublime Text3` 在安装插件的时候出现 `There Are No Packages Available For Installation`。如下图：

<img class=l-img src={{< param cdnPrefix >}}/Posts/Z-Turn/Sublime_Text_02/2021-10-15_17-05-40.png alt=img width=75% >

原因是系统下载`channel_v3.json`包失败，解决办法是手动下载`channel_v3.json`包然后复制到相应的文件夹并修改目录即可。

### 解决方法

**第一步** 下载 `channel_v3.json` 包，可以自行百度或者点此下载；

**第二步** 打开`Sublime Text3`，依次点击导航栏上面 `Preferences`（首选项）-> `Browse Packages`（浏览插件目录）；

{{< imgcapcdn src=`/Posts/Z-Turn/Sublime_Text_02/2021-10-15_17-06-14.png` alt=首选项-浏览插件目录 width=40% >}}

**第三步** 然后点击地址栏上面的 `Sublime text3` 进入上级目录：

{{< imgcapcdn src=`/Posts/Z-Turn/Sublime_Text_02/2021-10-15_17-06-41.webp` alt=进入上级目录 >}}

**第四步** 点击 `Lib`；

{{< imgcapcdn src=`/Posts/Z-Turn/Sublime_Text_02/2021-10-15_17-07-02.webp` alt=进入Lib文件夹 >}}

**第五步** 将上面下载的`channel_v3.json`复制粘贴进去；

{{< imgcapcdn src=`/Posts/Z-Turn/Sublime_Text_02/2021-10-15_17-07-19.webp` alt=拷贝文件到当前目录 >}}

**第六步** 回到 `Sublime Text3` 中，依次点击 `Preference`（首选项）--> `Package Settings` --> `Package Control` --> `Settings` ，打开设置文件；

{{< imgcapcdn src=`/Posts/Z-Turn/Sublime_Text_02/2021-10-15_17-08-21.png` alt=打开设置文件 width=75% >}}

**第七步** 在打开文件中添加下面以下代码，`Ctrl + S`保存即可；

```Text
"channels":
    [
       "C:\\Users\\ASUS\\AppData\\Roaming\\Sublime Text 3\\Lib\\channel_v3.json"
    ],
```

{{< imgcapcdn src=`/Posts/Z-Turn/Sublime_Text_02/2021-10-15_17-11-07.png` alt=添加代码 >}}

{{< admonition type=warning title=" 注意:" open=true >}}

路径就是刚才粘贴 json 文件的地址，根据自己电脑改动填写；

{{< /admonition >}}

**第八步** 重启 `Sublime Text3`，问题解决。

## 参考链接

- [package_control --> issues#1220](https://github.com/wbond/package_control/issues/1220)
