---
title: "Hugo + Algolia 实现站内搜索"
subtitle: ""
date: 2021-10-15T13:05:36+08:00
lastmod: 2021-10-17T00:05:36+08:00
author: "守正"
authorLink: ""
description: ""
slug: "hugo_algolia_site_search"
tags: ["Hugo", "Algolia",]
categories: ["Z-Turn"]
featuredImage: "https://cdn.chiga.ga/Posts/Z-Turn/00_01_Hugo_Algolia/Cover.jpg"
---

很多的 Hugo 主题是没有自带搜索功能的，但是们为了方便用户浏览和查找内容是需要在网站上提供搜索功能。

<!--more-->

主题 [LoveIt](https://github.com/dillonzq/LoveIt) 最新版已经内置了`Lunr.js`、`algolia`，这里我选择的是 **Algolia** ，只需要简单配置即可使用。

{{< admonition type=question   title="如何选择?" open=true >}}

以下是两种搜索的对比:

- `lunr`: 简单, 无需同步`index.json`, 没有 `contentLength` 的限制, 但占用带宽大且性能低 (特别是中文需要一个较大的分词依赖库)

- `algolia`: 高性能并且占用带宽低, 但需要同步 `index.json` 且有 `contentLength` 的限制

{{< /admonition >}}

## 在 Algolia 端创建应用和索引

### 创建新程序

点击 **NEW APPLICATION**，创建新程序，**Name**：自己起个名字，方案选择 **FREE（免费）**，点击下一步；

{{< imgcapcdn src=`/Posts/Z-Turn/00_01_Hugo_Algolia/2021-10-16_20-45-40.webp` alt=创建新程序 >}}

地区选择邻近地区（比如 **HongKong**）即可；

{{< imgcapcdn src=`/Posts/Z-Turn/00_01_Hugo_Algolia/2021-10-16_20-47-55.webp` alt=选择地区 >}}

确认信息，完成创建；

{{< imgcapcdn src=`/Posts/Z-Turn/00_01_Hugo_Algolia/2021-10-16_20-48-29.webp` alt=确认创建 >}}

### 创建Index

在引导界面，选择新手引导，进行下一步；

{{< imgcapcdn src=`/Posts/Z-Turn/00_01_Hugo_Algolia/2021-10-16_20-49-20.webp` alt="创建 Index" >}}

输入 **Index name**（例如自己的域名），提交即可；

{{< imgcapcdn src=`/Posts/Z-Turn/00_01_Hugo_Algolia/2021-10-16_20-49-56.webp` alt="命名Index name" >}}

### API Keys

点击左上的小房子回到主页，点击 **API Keys**，查看 **Key** 信息；

{{< imgcapcdn src=`/Posts/Z-Turn/00_01_Hugo_Algolia/2021-10-16_20-52-13.webp` alt="点击 API Keys" >}}

记住以下的 **Keys**，之后会用到；

{{< imgcapcdn src=`/Posts/Z-Turn/00_01_Hugo_Algolia/2021-10-16_20-52-48.webp` alt="记住 Key 信息" >}}

## 开始配置

### config.toml

把`\themes\LoveIt\exampleSite\config.toml` 文件，复制到**Hugo项目根目录**下（如果应用主题的时候已经操作过了可忽略这一步）修改以下信息，**Ctrl+S** 保存；

```toml
      [languages.zh-cn.params.search]
        ...
        [languages.zh-cn.params.search.algolia]
          index = "index.zh-cn"
          appID = "PASDMWALPK"
          searchKey = "b42948e51daaa93df92381c8e2ac0f93"
```

### 生成索引文件

导航到**Hugo项目根目录**下使用 `Git bat```batch` 执行 `Hugo` 命令；

```Text
hugo
```

便会在`\public\`文件夹下生成 `algolia.json`文件；

### 上传索引文件至 Algolia

将刚刚生成的`algolia.json`文件上传至 **Algolia** 刚刚创建的 `Index` 下即可；

不过这样操作太过于繁琐了，每次更新博客都要手动上传一次，我们可以通过一个插件 `atomic-algolia` 来一键同步数据；

**第一步** 安装 `atomic-aligolia` ；

我们需要先确保我们已经安装了 `npm` 或者 `yarn` 包管理工具。

导航到**Hugo项目根目录**下右键使用 `Git bat```batch` 执行以下命令；

```batch
npm install atomic-algolia --save
```

这会将 `atomic-algolia` 软件包安装到本地 `node_modules` 文件夹，并使其可用于您的 `Hugo` 项目。

**第二步** 配置完成以后，在**Hugo项目根目录**下右键使用 `Git bat```batch` 执行以下命令：

```batch
ALGOLIA_APP_ID={{ YOUR_APP_ID }} ALGOLIA_ADMIN_KEY={{ YOUR_ADMIN_KEY }} ALGOLIA_INDEX_NAME={{ YOUR_INDEX NAME }} ALGOLIA_INDEX_FILE={{ PATH/TO/algolia.json }} npm run algolia
```

这个时候我们在 `dashboard` 中打开 `Indices` ，可以看到已经有几十条数据了。

{{< imgcapcdn src=`/Posts/Z-Turn/00_01_Hugo_Algolia/2021-10-16_23-14-08.webp` alt=Indices界面 >}}

可还是不够便捷，请继续；

**第三步** Algolia 是支持 `.env` 文件的，在 **Hugo项目根目录**中创建一个名为 `.env` 的新文件（就是这个文件名），并添加以下内容：

```Text
ALGOLIA_APP_ID={{ YOUR_APP_ID }}
ALGOLIA_ADMIN_KEY={{ YOUR_ADMIN_KEY }}
ALGOLIA_INDEX_NAME={{ YOUR_INDEX_NAME }}
ALGOLIA_INDEX_FILE={{ PATH/TO/algolia.json }}
```

**第四步** 现在，您可以通过在**Hugo项目根目录**下右键使用 `Git bat```batch` 执行更简单的一条命令来更新索引：

```Text
npm run algolia
```

{{< admonition type=Tip title=" Tips:" open=true >}}

如果某篇文章不想被索引的话，我们只需要在文件的最前面设置 index 参数为 false 即可。

{{< /admonition >}}

## 参考链接

- [zhaoqiang's blog](https://www.nashome.cn/posts/hugo-algolia/#top)

- [水寒](https://dp2px.com/2019/09/07/hugo-algolia/)
