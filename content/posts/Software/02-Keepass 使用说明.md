---
title: "软件 - Keepass 使用说明"
subtitle: ""
date: 2022-08-30T14:42:07+08:00
lastmod: 2022-09-19T14:42:07+08:00
author: "守正"
slug: "keepass_manual"
tags: ["Keepass","密码管理器"]
categories: ["Software"]
---

`KeePass`是一款免费、小巧、绿色且开源的密码管理工具；

由于`KeePass`自身不带同步功能，所以如果有多设备使用需求的人，可以搭配坚果云进行使用；

<!--more-->

## PC 端

文件 --> 打开 --> 打开网址（URL）；

文件URL：https://dav.jianguoyun.com/dav/XXX

**XXX**：同步盘中`.kdbx`文件所在路径；

**用户名**：坚果云账户登录明；

**密码**：坚果云中添加的第三方授权密码；

简体中文语言包： https://keepass.info/translations.html

`View`（显示） --> `Change Language`（选择语言） --> `Chinese, Simp.`（简体中文） --> 重新启动软件；

## 安卓端

打开文件 --> `Https（WebDav）`；

文件URL：https://dav.jianguoyun.com/dav/XXX

**XXX**：同步盘中`.kdbx`文件所在路径；

**用户名**：坚果云账户登录明；

**密码**：坚果云中添加的第三方授权密码；

## 坚果云

**账户信息** --> **安全选项** --> **第三方应用管理** --> **添加应用并生成密码**；

坚果云第三方应用授权`WebDAV`开启方法： https://help.jianguoyun.com/?p=2064

## 使用技巧

### 自动输入

自定义击键顺序：

```
^{SPACE}{CLEARFIELD}{UserName}{TAB}{CLEARFIELD}{Password}{ENTER}
```

1. 打开登录界面；

2. 切换到`KeePass`选中需要填充的密码项，按快捷键`Ctrl+V`；

### KeeForm自动填充插件

#### 介绍

`KeeForm`是`KeePass`的一款易于使用且快速的表单填写器。

`KeeForm`允许您在`KeePass`中单击简单的双击，即可自动填写超级安全但难以记住/键入的密码。

1. 启动`KeePass`，然后双击某个网址。

2. `KeePass`将网址、用户名和密码传递给`KeeForm`。

3. 自动启动浏览器 → 打开网址 → 填写用户名和密码字 → 然后点击提交按钮

`KeeForm`是不记录有关您访问的登录的任何信息（并且您不必备份任何表单数据）。

#### 安装

安装包含两个步骤

##### 程序安装

下载最新版本的 `KeeForm Windows` 安装程序 https://keeform.org/keepass/keeform-for-chrome

打开程序安装包，进行安装步骤。

建议使用默认值（“只需单击每个步骤的”下一步“）。

{{< admonition type=info title=安装过程（点击展开） open=false >}}

{{< imgcapcdn src=`/Posts/Software/02_keepass_guidebook/2022-09-18_20-43-08.png` alt=用户协议 width=75% >}}

{{< imgcapcdn src=`/Posts/Software/02_keepass_guidebook/2022-09-18_20-43-28.png` alt=软件正在运行，需退出 width=50% >}}

{{< imgcapcdn src=`/Posts/Software/02_keepass_guidebook/2022-09-18_20-47-08.png` alt=设置安装路径 width=75% >}}

{{< imgcapcdn src=`/Posts/Software/02_keepass_guidebook/2022-09-18_20-47-25.png` alt=提示安装版本 width=75% >}}

{{< imgcapcdn src=`/Posts/Software/02_keepass_guidebook/2022-09-18_20-47-32.png` alt=设置安装文件夹名称 width=75% >}}

{{< imgcapcdn src=`/Posts/Software/02_keepass_guidebook/2022-09-18_20-47-37.png` alt=新安装or更新 width=75% >}}

{{< imgcapcdn src=`/Posts/Software/02_keepass_guidebook/2022-09-18_20-47-42.png` alt=手动选择浏览器 width=75% >}}

{{< imgcapcdn src=`/Posts/Software/02_keepass_guidebook/2022-09-18_20-48-03.png` alt=设置是否自动提交 width=75% >}}

{{< imgcapcdn src=`/Posts/Software/02_keepass_guidebook/2022-09-18_20-48-24.png` alt=专家模式 width=75% >}}

{{< imgcapcdn src=`/Posts/Software/02_keepass_guidebook/2022-09-18_20-48-37.png` alt=确认安装信息 width=75% >}}

{{< imgcapcdn src=`/Posts/Software/02_keepass_guidebook/2022-09-18_20-48-42.png` alt=正在写入文件中 width=75% >}}

{{< imgcapcdn src=`/Posts/Software/02_keepass_guidebook/2022-09-18_20-48-45.png` alt=安装完成 width=75% >}}

{{< /admonition >}}

默认情况下，`KeeForm`与`IP`地址`127.0.0.1` 端口`8484` 进行通信。如果需要，您可以更改它，但不要忘记在`KeeForm Chrome`扩展程序中设置相同的`IP`/端口。还要确保防火墙不会阻止该`IP`和端口。

##### 浏览器插件安装

您可以通过单击 https://keeform.org/keepass/keeform-for-chrome 页上的按钮来安装`KeeForm`扩展。

{{< imgcapcdn src=`/Posts/Software/02_keepass_guidebook/2022-09-18_20-52-00.png` alt= 商店插件主页 >}}

安装`KeeForm`扩展后，您应该注意到一个带有“蓝色图标指示器”的`KeeForm`工具栏图标。蓝色表示扩展正在初始化。如果一切安装正确，此指示器将变为绿色。如果它变为红色，则扩展程序无法“打开与`KeeForm`应用程序的连接”，很可能是因为防火墙阻止了它，或者其他浏览器已经在使用它。

就这样。从现在开始，当您双击`KeePass`中的`URL`时，`KeeForm`将打开一个浏览器会话并启动“表单填写过程”。

关于权限：
`Chrome`扩展程序：需要获得阅读/更改任何网站的权限。否则，它将无法填写表单。它还需要与`KeeForm`应用程序交换“本机消息”。

## 参考链接

- [Keepass 官网](https://keepass.info/)
- [PC 端项目地址](https://github.com/keepassx/keepassx)
- [安卓端项目地址](https://github.com/PhilippC/keepass2android)
- [坚果云官网](https://www.jianguoyun.com/)
- [KeeForm 官网](hhttps://keeform.org/)