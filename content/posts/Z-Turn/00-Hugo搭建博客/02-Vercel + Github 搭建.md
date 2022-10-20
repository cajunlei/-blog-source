---
title: "Vercel + Github 搭建个人博客"
subtitle: ""
date: 2021-10-23T20:39:56+08:00
lastmod: 2021-10-23T20:39:56+08:00
author: "徐艺扬"
authorLink: "https://www.cnblogs.com/xuyiyang"
description: "解决 Github pages 访问速度慢的问题"
slug: "vercel_github_building_blog"
tags: ["Vercel", "Github" ]
categories: ["Z-Turn"]
featuredImage: "https://cdn.chiga.ga/Posts/Z-Turn/00_02_vercel_github/Cover.jpg"
---

解决 Github pages 访问速度慢的问题……

<!--more-->

## 前言

一开始我的个人博客是用 `Gitee Pages` 访问的，但是长且丑，就购买了个人域名 [ll.sc.cn](http://ll.sc.cn) ；

后来发现，`Gitee Pages` 自定义域名需要企业版，也就是要花钱的；

但我的个人博客主要是用来记录一些自己学习的过程，并无收益，花钱买了个域名都已经破费了:joy: ；

所以转到 `Github Pages` 上，用了几天发现访问速度实在是太太太太太慢了，有些网络环境还直接不能访问；

经过一番搜索，有大佬推荐 [Vercel](https://vercel.com/) 来搭建。

{{< admonition type=note title=" 提示" open=true >}}

因为我已经注册好 `Vercel` 了，一开始只是想试一试，所以在注册过程中没有截图，故引用 [MTR-Static](https://www.zhihu.com/people/mtr-static-page) 大佬的图片了。

此文当一次温习和留存以便查阅。

{{< /admonition >}}

## 正文

注册 `Github` 账号就不多赘述，不会的找 [度娘](https://www.baidu.com/s?tn=02003390_hao_pg&ie=utf-8&wd=GitHub%E6%B3%A8%E5%86%8C) ；

### 注册 Vercel 账号

打开 <https://vercel.com/signup> ，点击 `Continue with Github`。

{{< imgcapcdn src=`/Posts/Z-Turn/00_02_vercel_github/8KLnqRom2IWXCEj.webp` alt=`Vercel注册` >}}

出现授权页面，点击 `Authorize Vercel`。

{{< imgcapcdn src=`/Posts/Z-Turn/00_02_vercel_github/fIScZko2CdbY9FQ.png` alt="授权 Github" width=75% >}}

### 创建博客

到了 `Select Vercel account` 的页面，在下面的 `Personal Account` 内点击你自己的账户，接着点击 `Continue`。

{{< imgcapcdn src=`/Posts/Z-Turn/00_02_vercel_github/ABtaLc6vNInKoQx.png` alt=选择用户 width=75% >}}

点击 `Import Project`。

{{< imgcapcdn src=`/Posts/Z-Turn/00_02_vercel_github/K4HW23ahntm1uol.png` alt=`导入项目` >}}

接着点击 `Select Template`。

{{< imgcapcdn src=`/Posts/Z-Turn/00_02_vercel_github/uG6wE8lxVM5ivTO.png` alt=选择模板 width=60% >}}

在模板选择页面向下滚动，可以找到 `Hugo`，点击它，现在我们将使用 `Hugo` 来生成静态网页。

{{< imgcapcdn src=`/Posts/Z-Turn/00_02_vercel_github/oPGiVfjZ2KTtHJe.png` alt=选择模板 width=75% >}}

保持默认，点击 `Continue`。

{{< imgcapcdn src=`/Posts/Z-Turn/00_02_vercel_github/5f2vpDYsRxBOMn1.webp` alt=`点击继续` >}}

点击 `Install Vercel for Github`。

{{< imgcapcdn src=`/Posts/Z-Turn/00_02_vercel_github/pOoguyDIb2JACZ6.jpg` alt="为 Github 安装 Vercel" width=75% >}}

点击绿色的 `Install`。

{{< imgcapcdn src=`/Posts/Z-Turn/00_02_vercel_github/WOTJpM7fqhnuzaY.webp` alt=`点击安装` >}}

保持默认，点击 `Continue`。

{{< imgcapcdn src=`/Posts/Z-Turn/00_02_vercel_github/4Cb6lXcvrZjp1oT.jpg` alt=点击继续 width=75% >}}

到了 `Create Git Repository` 页面，因为之前关联的是 `Github`，所以选择 `Github`。在 `Repository Name` 内填写你想要的仓库名称，`Vercel` 将在 `Github` 创建一个仓库用于托管文件。`Private Git Repository` 无论勾选与否都差不多，区别就在于创建的仓库是是私人仓库还是公开仓库，点击 `Continue`。

{{< imgcapcdn src=`/Posts/Z-Turn/00_02_vercel_github/aiWV1HfQ7OBCqvT.png` alt="创建 Git 存储库" width=75% >}}

`Import Project` 页面保持默认即可，点击 `Deploy`。

{{< imgcapcdn src=`/Posts/Z-Turn/00_02_vercel_github/XkIVwTEQ8Mype1j.png` alt=点击部署 width=75% >}}

现在就创建成功了，点击 `Visit` 就可以直接访问。但是界面十分粗糙，接下来需要做一些个性化设置。

{{< imgcapcdn src=`/Posts/Z-Turn/00_02_vercel_github/2lihNQDB9wszZHW.png` alt=`创建成功` >}}

{{< imgcapcdn src=`/Posts/Z-Turn/00_02_vercel_github/U5iVnl1hB6I2Cke.png` alt=`博客首页` >}}

{{< admonition type=success title=" 个人心得" open=true >}}

我第一次在创建的时候选择了 `Hugo` 模板，但是部署后打开网页 `404` ，然后我删除了刚刚在 `Vercel` 建的新库，重新导入 `Github` 项目，保持默认，没有选择 `Hugo` 模板，按刚刚的步骤完成，打开链接，成功了，网页显示正常。

{{< /admonition >}}

### 开始使用

你可以到 [GitHub Desktop](https://desktop.github.com/) 下载 `GitHub Desktop`，相比 CLI 的 `git`，配置起来更便捷。

登录号账号之后点击 `File`，接着点击 `Clone repositories`。

{{< imgcapcdn src=`/Posts/Z-Turn/00_02_vercel_github/1dshCNqYU6kxajG.png` alt=`GitHub Desktop` >}}

找到自己为创建 `Hugo` 创建的仓库，选中后点击 `Clone`。

{{< imgcapcdn src=`/Posts/Z-Turn/00_02_vercel_github/YNqydH7Ocu9DoK5.png` alt=`拉取自己博客的库` >}}

打开文件资源管理器，打开 `C:\Users\你的用户名\Documents\GitHub`，应该可以看到刚刚 `clone` 的仓库，此处为 `test`。

{{< imgcapcdn src=`/Posts/Z-Turn/00_02_vercel_github/tbaJYZCyvFoG8se.png` alt=`打开本地库文件夹` >}}

按照主题提供的方法做配置，例如： `even`。

修改完之后打开 `Github Desktop`，应该能看到更改，在左下角的 `Summary` 里填入做的修改（`upload theme` 或者别的什么，有内容即可），点击 `Commit to master`。

{{< imgcapcdn src=`/Posts/Z-Turn/00_02_vercel_github/VE2QIbgoud5GfAC.png` alt=`Github Desktop` >}}

点击右上角的 `Push origin`，把修改推送到 `Github`。

{{< imgcapcdn src=`/Posts/Z-Turn/00_02_vercel_github/6cyngiMOaRTWl3m.png` alt="推送到 Github" width=50% >}}

完成之后再等待半分钟，打开网站，改动应该已经生效了。

{{< imgcapcdn src=`/Posts/Z-Turn/00_02_vercel_github/XyVxH7AQztChT3c.png` alt=`博客首页` >}}

这是因为 `Vercel` 会检测到 `Github` 仓库改动之后会自动重新生成网页，之后更新文章可以直接在 `Github` 网页版上传到`./content/posts` 里，比在电脑上自己生成网页再 `Push` 方便不少。

{{< imgcapcdn src=`/Posts/Z-Turn/00_02_vercel_github/xN6idDFhAPm2Gbr.png` alt=`部署记录` >}}

### 绑定域名

这需要你自己有一个域名，如果不想花钱的话可以在 `freenom` 免费申请一个，这里不多赘述。

在 `Vercel` 的控制面板里打开你的项目（如此处的 test） > Settings > Domains，在输入框里输入你想绑定的域名，此处我用 `test.yxyy.top`。接着它会提示错误，这是因为我还没有设置域名解析。

{{< imgcapcdn src=`/Posts/Z-Turn/00_02_vercel_github/ygVKfw8NuPAvncF.png` alt=`自定义域名` >}}

你需要按照提示在域名提供商那里做 `CNAME` 解析，我是在阿里云注册的域名，其他的域名注册商应该也大同小异。

{{< imgcapcdn src=`/Posts/Z-Turn/00_02_vercel_github/bTpUJszoGcWOgKH.png` alt=`解析域名` >}}

现在回到 `Vercel` 控制面板，应该就不会报错了，它还会自动帮你申请 `Let's Encrypt` 的 `SSL` 证书。

{{< imgcapcdn src=`/Posts/Z-Turn/00_02_vercel_github/dalv63ZILAsiOKJ.png` alt=`自定义域名` >}}

现在可以带着域名访问了。

{{< imgcapcdn src=`/Posts/Z-Turn/00_02_vercel_github/jyUOH8Nk6CFluGr.webp` alt=`自己的域名打开博客` >}}

## 参考链接

- [使用Vercel+Github搭建个人博客](https://www.cnblogs.com/xuyiyang/p/13647069.html)

- [手把手教你搭建完全免费的个人博客](https://zhuanlan.zhihu.com/p/143389054)
