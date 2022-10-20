---
title: "v2rayN - 使用笔记"
subtitle: ""
date: 2021-10-22T16:39:13+08:00
lastmod: 2021-10-22T16:39:13+08:00
author: "守正"
authorLink: ""
description: ""
slug: "v2rayn_use_notes"
tags: ["v2rayN"]
categories: ["Z-Turn"]
hiddenFromHomePage: true
hiddenFromSearch: false
featuredImage: "https://cdn.chiga.ga/Posts/Z-Turn/02_v2rayN/Cover.jpg"
---

在使用 v2rayN 过程中学习的一些笔记分享……

<!--more-->

{{< admonition type=tip title=" 提示" open=true >}}

3.29 是最后一版支持 `PAC` 的，推荐使用；

{{< /admonition >}}

### 新版本实现 PAC 功能

{{< imgcapcdn src=`/Posts/Z-Turn/02_v2rayN/710.png` alt=参数解释 >}}

- 路由设置，复制以下代码，导入剪贴板；

```text
[
  {
    "inboundTag": [],
    "outboundTag": "block",
    "domain": [
      "geosite:category-porn"
    ]
  },
  {
    "inboundTag": [
      "http"
    ],
    "outboundTag": "direct",
    "ip": [
      "geoip:cn",
      "geoip:private"
    ]
  },
  {
    "inboundTag": [
      "http"
    ],
    "outboundTag": "direct",
    "domain": [
      "geosite:category-games@cn",
      "domain:edu.cn",
      "domain:steamcontent.com"
    ]
  },
  {
    "inboundTag": [
      "http"
    ],
    "outboundTag": "proxy",
    "domain": [
      "geosite:greatfire",
      "geosite:gfw",
      "geosite:steam",
      "geosite:google",
      "domain:lcc.edu",
      "domain:vmware.com"
    ]
  },
  {
    "port": "0-65535",
    "inboundTag": [
      "http"
    ],
    "outboundTag": "direct"
  },
  {
    "port": "0-65535",
    "inboundTag": [
      "socks"
    ],
    "outboundTag": "proxy"
  }
]

```

### V2Ray域名解析策略的含义、区别，以及最佳选择

`AsIs` 、 `IPIfNonMatch` 、 `IPOnDemand` 三个域名解析策略是什么意思，有什么区别？

{{< admonition type=abstract title=" 摘要" open=true >}}

- `AsIs`
只使用域名进行路由选择。快速解析，不精确分流。默认值。

- `IPIfNonMatch`
当域名没有匹配任何规则时，将域名解析成 IP（A 记录或 AAAA 记录）再次进行匹配；<br>
当一个域名有多个 A 记录时，会尝试匹配所有的 A 记录，直到其中一个与某个规则匹配为止；<br>
解析后的 IP 仅在路由选择时起作用，转发的数据包中依然使用原始域名；
理论上解析比 AsIs 稍慢，但使用中通常不会觉察到。

- `IPOnDemand`
当匹配时碰到任何基于 IP 的规则，将域名立即解析为 IP 进行匹配。解析最精确，也最慢。

{{< /admonition >}}

`V2Ray` 域名策略解析选择哪个更好？

虽然 `V2Ray` 官方解释 `AsIs` 是默认值，但是实际上，在几款主流客户端中，有的默认值是 `AsIs` ，有的是 `IPIfNonMatch` 。

因此，选择 `AsIs` 或 `IPIfNonMatch` 都可以。

{{< admonition type=warning title=" 注意" open=true >}}

如果在自定义路由设置规则时，添加了匹配 IP 的路由代理规则，比如 `geoip:cn`、`geoip:private`，或者直接添加的 IP 地址规则，则必须选择位于中间的 `IPIfNonMatch` ，不然，匹配 IP 地址的路由规则不会生效。

{{< /admonition >}}

```text
#以下三行是GitHub网站，为了提高下载速度走代理,
github.com,
githubassets.com,
githubusercontent.com,
#下一行谷歌产品图标,
googleusercontent.com
```

{{< admonition type=info title=" 订阅节点" open=false >}}

```text
freefq/free
https://raw.fastgit.org/freefq/free/master/v2
```

{{< /admonition >}}

## 参考链接

- [项目地址](https://github.com/2dust/v2rayN)

- [节点一](https://github.com/freefq/free)

- [节点二](https://github.com/littlekign/free)

- [使用说明](https://github.com/freefq/tutorials)

- [v2ray域名解析策略的含义、区别，以及最佳选择](https://baiyunju.cc/7256)

- [可以替代PAC模式的v2ray路由器策略代理规则配置](https://baiyunju.cc/7501)
