---
title: "Blog 搭建笔记"
subtitle: ""
date: 2021-10-18T22:02:45+08:00
lastmod: 2022-09-20T22:35:45+08:00
author: "守正"
authorLink: ""
description: ""
slug: "blog_building_notes"
tags: ["Blog"]
categories: ["Z-Turn"]

hiddenFromHomePage: true
hiddenFromSearch: false
---

<!--more-->

## hugo优点

常见的静态网站生成工具对环境依赖过多，性能较差，于是使用`Go`语言写了一个静态网站生成器`Hugo`。

不仅解决了环境依赖、性能较差的问题，还有使用简单、部署方便等诸多优点，通过`LiveReload`实时刷新，极大的优化文章的写作体验。

## hugo安装

`Hugo`的安装有很多方式 [Install Hugo](https://gohugo.io/getting-started/installing/) 根据个人喜好可以自行安装。

{{< admonition type=note title=注意 open=true >}}
使用 `Hugo` 前需要安装 [Git](https://git-scm.com/) 和 [Go](https://golang.org/) 语言开发环境。
{{< /admonition >}}

**第一步** 打开 [hugo官网](https://gohugo.io/) → [下载hugo](https://github.com/gohugoio/hugo/releases)，选择符合自己环境的版本下载；

**第二步** 解压`hugo`安装文件，比如到 `C:\hugo`

管理员身份打开`cmd`，切换到 `C:\hugo\` 目录下，输入：

```Text
hugo version
```

显示 `hugo` 版本号，说明安装成功了；

将`Hugo`添加到`Windows`的环境变量 `PATH` 中；

**步骤** 计算机 --> 属性 --> 高级系统设置 --> 环境变量 --> 系统变量 --> `Path`。

{{< admonition type=tip title=技巧 open=true >}}
按快捷键`win + R`，输入：`sysdm.cpl`快速打开环境变量配置;
{{< /admonition >}}

现在在任意位置，右键打开 `git bash` 输入 `hugo version` 同样也会得到 `hugo` 版本号；

## 开始使用

### 创建本地站点根目录

在任意目录下，然后输入如下命令，进行创建本地站点根目录

```
hugo new site hugoblog
```

### 下载hugo主题

因为`hugo`没有内置主题，所以你需要去下载一个

```
git clone https://github.com/reuixiy/hugo-theme-meme.git themes/meme
```

### 创建第一个测试文件

```
hugo new post/first.md
```

### 本地预览

```
hugo serve -e production
```

在浏览器打开如下链接，http://localhost:1313/ 查看效果

## 推送到github仓库

### github上创建仓库

登录 [Github](https://github.com/)

点击`Your repositories` → 点击`new` → 填写仓库名，选择`Public`，添加一个`Readme`文件 → 点击`Create respository`

完成仓库创建。

### 将本地文件推送到远程仓库

1. 在博客根目录，执行`hugo -D`生成下网站所需数据；

2. 可以看到`public`目录下，生成可很多文件，这个就是后续生成网站所需要的数据；

3. 来到`public`目录下，执行如下命令；

```
cd public
git init
git add .
git commit -m "first commit"
git remote add origin git@github.com:cajunlei/test.git
git push -u origin
```

此时来到`github`仓库下，数据已经被推送上来了

最后在`github`上设置下`gitpages`功能

## Node.js安装

打开[Node.js](https://nodejs.org/zh-cn/)，选择合适的版本下载安装即可；

<img class=l-img src={{< param cdnPrefix >}}/Posts/Z-Turn/00_03_Blog_Building/2021-11-15_21-22-11.png alt=img width=75% >

我安装的**长期维护版**，安装过程一路点击下一步即可；

## PicGo 配置(Gitee)

### 安装插件

在左侧 **插件设置** 选项中，搜索 `Gitee` 即可出现对应的插件，点击安装即可；

<img class=l-img src={{< param cdnPrefix >}}/Posts/Z-Turn/00_03_Blog_Building/2021-11-15_21-24-44.png alt=img width=95% >

我选择的是 `gitee-uploader 1.1.2` ；

### 配置gitee

点击左侧 **图床设置** --> `gitee` ；

<img class=l-img src={{< param cdnPrefix >}}/Posts/Z-Turn/00_03_Blog_Building/2021-11-17_19-45-36.png alt=img width=95% >

{{< admonition type=abstract title=填写说明 open=true >}}
- **repo：** 仓库名称，填写你在创建图床时的仓库名字，这里注意带上你的用户名，比如我的是 cajunlei/ImageBed;
- **branch：** 填写分支名称，一般默认 master；
- **token：** 这个比较重要，就是上面创建仓库后创建的私人令牌明文，直接粘贴上去就行，如果忘记了那么直接删除重新再创建了；
- **path：** 填写仓库下面某个文件夹名字，也就是你存放图片的位置，比如我的是在images,这个名字要和你仓库中创建的对应；
- **customPath：** 保持默认可不用修改；
- **customUrl：** 保持默认可不用修改；
{{< /admonition >}}

最后「确认」后直接就可以使用了，记得点击下「设置为默认图床」。

## Blog 配置

### 为自己的博客添加运行时间

**第一步** 将以下代码中的日期和时间，修改为你博客或者网站的运行开始日期和时间；

```html
<!-- 修改此行日期及时间 -->
new Date("9/24/2021 22:52:50");
```

**第二步** 将修改过后的代码，放到你网站喜欢的位置就好啦。

```html
<span id="runtime_span"></span>
<script type="text/javascript">
    function show_runtime(){window.setTimeout("show_runtime()",1000);
    X=new Date("9/24/2021 22:52:50");
    Y=new Date();T=(Y.getTime()-X.getTime());
    M=24*60*60*1000;a=T/M;
    A=Math.floor(a);b=(a-A)*24;
    B=Math.floor(b);c=(b-B)*60;
    C=Math.floor((b-B)*60);
    D=Math.floor((c-C)*60);
    runtime_span.innerHTML="本站已运行:"+A+"天"+B+"小时"+C+"分"+D+"秒"}show_runtime();
</script>
```

我的放在 `/layouts/pratials/footer.html` 文件中：

### 加入不蒜子统计

在根目录的 `config.toml` 文件中加入以下代码：

```toml
[params]
...
# 以下为需添加内容 #
# busuanzi
busuanzi = true
busuanzi_site_offset = 100000
```

在 `/layouts/pratials/footer.html` 文件中加入以下代码：

```html
{{- if ne .Site.Params.footer.enable false -}}
    <footer class="footer">
        <div class="footer-container">
            ...
            <!-- 以下为需添加内容 -->
            <span id="busuanzi_container_site_pv">
                本站访问量：<span id="busuanzi_value_site_pv"></span>次
            </span> | 
            <span id="busuanzi_container_site_uv">
                您是本站第 <span id="busuanzi_value_site_uv"></span> 位访问者
            </span>
            <!-- 以上为需添加内容 -->
        </div>
    </footer>
{{- end -}}
```

### 用于站长SEO

无需上传验证文件到根目录，直接修改配置文件；

网站验证代码修改，根目录 `config.toml` 文件；

```toml
# Site verification code for Google/Bing/Yandex/Pinterest/Baidu
# 网站验证代码，用于 Google/Bing/Yandex/Pinterest/Baidu
[params.verification]
  google = "google699009ae438f1e4d"
  bing = "0AA62D35A93C9239B95F5187EC12FAF1"
  yandex = ""
  pinterest = ""
  baidu = "3f7de7fba11a61559c21d907904d0a1b"
```

## jsDelivr 加速

### 操作步骤

**第一步** 新建`Github`仓库；

**第二步** 将需要`cdn`加速的静态资源上传到`github`仓库；

**第三步** 点击`release`发布版本，自定义发布版；

**第四步** 应用资源文件路径：

```
https://cdn.jsdelivr.net/gh/user/repo@version/file

https://cdn.jsdelivr.net/gh/你的用户名/你的仓库名@发布的版本号/文件路径
```

以我的为例，访问仓库目录下的`logo.jpg`文件，为以下链接：

https://cdn.jsdelivr.net/gh/AyagawaSeirin/BlogAssets@1.3/logo.jpg

{{< admonition type=warning title=注意 open=true >}}
版本号不是必需的，是为了区分新旧资源，如果不使用版本号，将会直接引用最新资源，
{{< /admonition >}}

### CDN 缓存

当网站更新时，如果`CDN`节点上数据没有及时更新，即便在浏览器使用`Ctrl+F5`的方式强制刷新浏览器的缓存，也会因为`CDN`节点没有同步最新数据而导致访问不到最近资源。

我们可以通过`CDN`服务商提供的**刷新缓存**接口来达到清理`CDN`边缘节点缓存的目的，这样在更新数据后，可以使用「刷新缓存」功能来强制`CDN`节点上的数据缓存过期，保证在访问时，拉取到最新的数据。

### jsDelivr 缓存刷新

对于`jsDelivr`，缓存刷新的方式也很简单，只需将想刷新的链接的开头的

```
https://cdn.jsdelivr.net/...
```

替换成

```
https://purge.jsdelivr.net/...
```

即可实时刷新。刷新成功后，浏览器会返回缓存刷新成功的信息，如下：

```
{
  "id": "I2ZhNWYqdXev0Dmh",
  "status": "finished",
  "timestamp": "2021-12-05T01:54:57.948Z",
  "paths": {
    "/gh/cajunlei/ImageBed/Posts/1.jpg": {
      "throttled": false,
      "providers": {
        "fastly": true,
        "bunny": true,
        "cloudflare": true,
        "quantil": false
      }
    }
  }
}
```

## 为图标添加动画效果

### 示例代码

```html
<div class="fa-3x">
  <i class="fas fa-spinner fa-spin"></i>
  <i class="fas fa-circle-notch fa-spin"></i>
  <i class="fas fa-sync fa-spin"></i>
  <i class="fas fa-cog fa-spin"></i>
  <i class="fas fa-spinner fa-pulse"></i>
  <i class="fas fa-stroopwafel fa-spin"></i>
</div>
```

### 显示效果

<div class="fa-3x" style="text-align: center;">
  <i class="fas fa-spinner fa-spin"></i>
  <i class="fas fa-circle-notch fa-spin"></i>
  <i class="fas fa-sync fa-spin"></i>
  <i class="fas fa-cog fa-spin"></i>
  <i class="fas fa-spinner fa-pulse"></i>
  <i class="fas fa-stroopwafel fa-spin"></i>
</div>

## 自定义模板

**第一步** 将`\themes\LoveIt\layouts\posts\single.html`文件复制到`\layouts\_default`文件夹下；

**第二步** 按需要修改`single.html`模板文件；

**第三步** 最后在文章头部引用模板即可；
   ```toml
   ---
     title: "XX"
     layout: "journal"
   ---
   ```

## Twikoo 版本升级（Vercel）

1. 进入`Vercel`仪表板 →`twikoo`→`Settings`→`Git`；
2. 点击`Connected Git Repository`下方的仓库地址；
3. 打开`package.json`，点击编辑；
4. 将"`twikoo-vercel`":"`x.x.x`"其中的版本号修改为最新版本号。点击`Commit changes`；
5. 部署会自动触发，可以回到`Vercel`仪表板，查看部署状态；

{{< admonition type=note title=提示 open=true >}}
`Vercel`更新部署成功后，请不要忘记同时更新前端的`Twikoo CDN`地址中的`x.x.x`数字版本号，使之与云函数版本号相同，然后部署网站。
{{< /admonition >}}

## 一些问题

### 背景设置透明度后文章图片也被透明化的解决方法

因为增加了背景图片，故正文部分填充颜色设置了透明度，但是发现文章的「图片」也被透明了；

**解决办法：** 在设置透明度的时候改用`rgba`形式就可以了，只需要在设置颜色的透明度的时候可以先找到`16`进制颜色对应的`rgb`值，如：`255,255,255`然后通过`rgba(255,255,255,0.9)`来实现透明度；

## 参考链接

- [jsDelivr - Open Source CDN](https://github.com/jsdelivr/jsdelivr)
- [jsdelivr 缓存刷新](https://www.cnblogs.com/xieqk/p/jsdelivr-cache-refresh.html)
- [如何使用jsDelivr+Github 实现免费CDN加速?](https://zhuanlan.zhihu.com/p/346643522)
- [实战：手把手带你从0到1搭建自己的hugo博客站点](https://blog.csdn.net/weixin_39246554/article/details/124573538)