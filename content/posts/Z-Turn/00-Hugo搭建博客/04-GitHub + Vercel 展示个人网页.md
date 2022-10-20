---
title: "GitHub + Vercel 展示个人网页"
subtitle: ""
date: 2022-10-04T18:22:15+08:00
lastmod: 2022-10-04T18:22:15+08:00
# draft: true
author: "守正"
slug: "hugo_gitHub_vercel"
tags: ["个人网页","hugo","GitHub","Vercel"]
categories: ["Z-Turn"]
featuredImage: ''
---

不管是搭建静态博客，还是展示个人网页，我们都可以这个方法达到网络访问的目的。

<!--more-->

{{< admonition type=info title=提示 open=true >}}
静态博客需要先生成静态文件后将生成的静态文件上传至`GitHub`；

自己写的网页，所引用文件的目录要正确，上传`GitHub`即可。
{{< /admonition >}}

## Vercel部署

**第一步** 打开`Vercel`并登录

{{< imgcapcdn src=`/Posts/Z-Turn/00_04_GitHub_Vercel/2022-10-04_17-50-23.webp` alt=vercel个人页面 >}}

**第二步** 点击右侧`Add New…` → `Project`

{{< imgcapcdn src=`/Posts/Z-Turn/00_04_GitHub_Vercel/2022-10-04_17-50-41.webp` alt=新建工程 >}}

**第三步** 通过`GitHub`导入仓库；

{{< imgcapcdn src=`/Posts/Z-Turn/00_04_GitHub_Vercel/2022-10-04_17-50-46.webp` alt=导入GitHub仓库 >}}

**第四步** 选择我们在`GitHub`创建好并且已经`Push`网页文件的仓库

{{< imgcapcdn src=`/Posts/Z-Turn/00_04_GitHub_Vercel/2022-10-04_17-50-58.webp` alt=选择仓库 >}}

**第五步** 因为用`Hugo`框架`Push`的是`Public`文件夹下已经渲染好的`HTML`文件,所以直接保持默认,`FRAMEWORK PRESET`选项下面不要再去选择`Hugo`了,切记；

直接点击`Deploy`完成部署；

{{< imgcapcdn src=`/Posts/Z-Turn/00_04_GitHub_Vercel/2022-10-04_17-51-04.webp` alt=保持默认设置 >}}

**第六步** 通过预览窗可以看到已经显示网页的样子了；

{{< imgcapcdn src=`/Posts/Z-Turn/00_04_GitHub_Vercel/2022-10-04_17-53-16.webp` alt=部署成功 >}}

**第七步** 现在可以通过`Vercel`的域名进行访问,不过太长了,不容易记忆和输入,我们需要绑定到我们自己的域名来进行访问；

回到刚创建的新工程下,依次点击`Setting` → `Domains` → 输入我们的域名 → 点击`Add`完成操作；

{{< imgcapcdn src=`/Posts/Z-Turn/00_04_GitHub_Vercel/2022-10-04_17-54-13.webp` alt=绑定域名 >}}

然后会报错,因为我们输入的域名还没有解析；

**第八步** 接下来到我们自己域名的服务商进行`DNS`解析即可；