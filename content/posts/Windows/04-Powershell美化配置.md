---
title: "Powershell - 美化配置"
subtitle: ""
date: 2021-10-29T11:30:21+08:00
lastmod: 2021-10-29T11:30:21+08:00
author: "守正"
authorLink: ""
description: ""
slug: "config_powershell"
tags: ["PowerShell"]
categories: ["Windows"]
---

原生的 PowerShell 界面太朴素了，配置一下焕然一新……

<!--more-->

## 使用 Winget 安装 PowerShell

`Windows` 包管理器 `Winget` 是一种命令行工具，开发人员可以使用它在 `Windows 10` 计算机上查找、安装、升级、删除和配置应用程序。 此工具是 `Windows` 程序包管理器服务的客户端接口。

{{< admonition type=info title=" 备注" open=true >}}

若要查看系统要求列表和安装说明，请参阅 [winget文档](#参考链接) 。

{{< /admonition >}}

通过以下命令，可使用已发布的 `winget` 包安装 `PowerShell`：

搜索最新版本的 `PowerShell`

```PowerShell
winget search Microsoft.PowerShell
```

提示是否同意条款，输入 `Y` 回车确认；

```Output
Name               Id                           Version  Source
----------------------------------------------------------------
PowerShell         Microsoft.PowerShell         7.1.5.0  winget
Powershell Preview Microsoft.PowerShell.Preview 7.2.0.10 winget
```

使用 `--exact` 参数选择安装 `PowerShell` 版本；

```PowerShell
winget install --name PowerShell --exact --source winget
winget install --name PowerShell-Preview --exact --source winget
```

{{< imgcapcdn src=`/Posts/Windows/04_PowerShell/2021-10-28_21-38-55.png` alt=安装成功 >}}

## 开始配置 PowerShell

### 安装 Oh-My-Posh

`Install-Module` 为 `PowerShell` 自带的程序安装工具；

```PowerShell
Install-Module oh-my-posh -Scope CurrentUser -SkipPublisherCheck
```

遇到提示不信任的存储库，我们输入 `Y` ，确认；

{{< admonition type=warning title=" 警告" open=true >}}

Untrusted repository

You are installing the modules from an untrusted repository. If you trust this repository,change its InstallationPolicy value by running the Set-PSRepository cmdlet. Are you sure youwant to install the modules from 'PSGallery' ?

{{< /admonition >}}

{{< imgcapcdn src=`/Posts/Windows/04_PowerShell/2021-10-28_21-57-58.png` alt=Oh-My-Posh安装成功 >}}

### 安装 Posh-Git

```PowerShell
Install-Module posh-git -Scope CurrentUser
```

同样的提示，重复上一步的操作，输入 `Y` ，确认即可；

{{< imgcapcdn src=`/Posts/Windows/04_PowerShell/2021-10-28_22-21-03.png` alt=Posh-Git安装成功 >}}

### 安装 PSReadLine

```PowerShell
Install-Module -Name PSReadLine -AllowPrerelease -Scope CurrentUser -Force -SkipPublisherCheck
```

{{< imgcapcdn src=`/Posts/Windows/04_PowerShell/2021-10-28_22-21-51.png` alt=PSReadLine安装成功 >}}

### 开启默认激活配置

**第一步** 使用记事本打开 `$PROFILE`，进行配置；

命令行继续输入：

```PowerShell
notepad.exe $PROFILE
```

第一次执行提示没有这个文件，点击「是」进行创建；

{{< imgcapcdn src=`/Posts/Windows/04_PowerShell/2021-10-28_22-45-38.png` alt=创建文件 width=65% >}}

复制一下内容到文档，保存；

```PowerShell
Import-Module posh-git
Import-Module oh-my-posh
Set-PoshPrompt -Theme robbyrussel
```

{{< imgcapcdn src=`/Posts/Windows/04_PowerShell/2021-10-28_22-46-17.png` alt=编辑文档内容 width=65% >}}

{{< admonition type=abstract title=" 代码解释" open=true >}}

Import-Module posh-git　　　　　　　　　//导入 Posh-Git 模块<br>
Import-Module oh-my-posh　　　　　　　//导入 Oh-My-Posh 模块<br>
Set-PoshPrompt -Theme robbyrussel　　　//设置主题

{{< /admonition >}}

重新启动 `Windows Terminal` ，即可看到效果；

### 安装特殊符号字体

当使用某些带有特殊符号的主题时，会显示乱码，如下：

```PowerShell
Set-PoshPrompt -Theme powerlevel10k_rainbow
```

{{< imgcapcdn src=`/Posts/Windows/04_PowerShell/2021-10-28_23-07-06.png` alt=符号未正常显示 >}}

下载字体文件后，双击打开，在左上找到「安装」或`Install`并点击；

#### 字体下载

{{< admonition type=info title=` 百度云` open=false >}}

- **链　接：** <https://pan.baidu.com/s/1ZXvAgqdKs1uXqfazHmA3Dg> 
- **提取码：** j3sv

{{< /admonition >}}

{{< admonition type=info title=` 蓝奏云` open=false >}}

- **链　接：** <https://cajun.lanzoui.com/im4FAwo4ioh>
- **密　码：** a9rj

{{< /admonition >}}

然后打开设置 --> PowerShell --> 外观 --> 字体选择带 `Nerd Font` 的 --> 保存即可。

{{< imgcapcdn src=`/Posts/Windows/04_PowerShell/2021-10-28_23-25-59.png` alt=设置字体 >}}

{{< imgcapcdn src=`/Posts/Windows/04_PowerShell/2021-10-28_23-26-20.png` alt=图标符号已正常显示 >}}

### 安装文件图标库

```PowerShell
Install-Module -Name Terminal-Icons -Repository PSGallery
```

同样的提示，输入 `Y` ，确认即可；

{{< imgcapcdn src=`/Posts/Windows/04_PowerShell/2021-10-28_23-40-21.png` alt=图标库安装成功 >}}

### 使用图标

```PowerShell
Import-Module -Name Terminal-Icons
```

{{< imgcapcdn src=`/Posts/Windows/04_PowerShell/2021-10-28_23-40-50.png` alt=图标显示成功 >}}

### 命令行自动补全和提示

```PowerShell
Set-PSReadlineKeyHandler -Key Tab -Function MenuComplete
```

输入命令其实字符，按 `tab` 键，跳出候选命令；

最后可以将这些代码都放到配置文件中；

```PowerShell
Import-Module posh-git
Import-Module oh-my-posh
Import-Module -Name Terminal-Icons
Set-PoshPrompt -Theme powerlevel10k_rainbow
Set-PSReadlineKeyHandler -Key Tab -Function MenuComplete
```

## 参考链接

- [在 Windows 上安装 PowerShell](https://docs.microsoft.com/zh-cn/powershell/scripting/install/installing-powershell-on-windows?view=powershell-7.1#winget)
- [从 Windows PowerShell 5.1 迁移到 PowerShell 7](https://docs.microsoft.com/zh-cn/powershell/scripting/whats-new/migrating-from-windows-powershell-51-to-powershell-7?view=powershell-7.1)
- [Oh-My-Posh 文档](https://ohmyposh.dev/docs)
- [更多 Oh-My-Posh 主题](https://ohmyposh.dev/docs/themes)
- [winget文档](https://docs.microsoft.com/zh-cn/windows/package-manager/winget/) 

### 视频教程

{{< bilibili id=BV12u411Z7Zo >}}
