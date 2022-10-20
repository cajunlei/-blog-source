---
title: "Backblaze B2 + Cloudflare 搭建免费图床"
subtitle: ""
date: 2022-10-08T15:54:14+08:00
lastmod: 2022-10-08T15:54:14+08:00
# draft: true
author: "守正"
slug: "20221008155414"
tags: ["图床","Cloudflare","Backblaze"]
categories: ["Z-Turn"]
featuredImage: ''
---



<!--more-->

## Backblaze 部分

### 注册 Backblaze 账号

1. 打开 [https://www.backblaze.com/b2/sign-up.html](https://www.backblaze.com/b2/sign-up.html) ；

2. 输入 **邮箱**、**密码** 进行注册；

### 创建 B2 Bucket(存储桶)

1. 点击右上角`My Account`进入后台；

2. 选择`Buckets`（桶），然后点击`Create a Bucket`，创建一个存储桶。

{{< admonition type=info title=说明 open=true >}}
1. `Bucket Unique Name`（桶唯一名称）：自己取一个名称；

2. `Files in Bucket are`（桶里面的档案是）：`Public`（公众）；
{{< /admonition >}}

3. 点击`Create a Bucket`（创作一个桶）完成创建；

### 获取存储桶所在服务器

1. 回到`Buckets`(存储桶) ；

2. 在刚刚创建的存储桶上，点击`Upload/Download`(上传/下载)；

3. 上传一个任意文件到存储桶中；

4. 然后点击刚上传文件后面的 `i`（`information`，信息）;

5. 记住`Friendly URL`的前部分，如：`https://f004.backblazeb2.com/`

## Cloudflare 部分

### 注册 Cloudflare 账号

1. 打开[https://dash.cloudflare.com/sign-up](https://dash.cloudflare.com/sign-up)；

2. 输入 **邮箱**、**密码** 进行注册；

### 将域名接入 Cloudflare

1. 在`Websites`（网站）标签，点击`Add a Site`（添加站点）

2. 输入你的有效域名并点击`Add site`（添加站点）

3. `Select a plan`（选择计划）：选择最下方的`Free` $0(0 美元)，点击`Continue`（继续）

4. 到你的域名服务商将`DNS`服务替换未`cloudflare`的

{{< admonition type=info title=服务器地址 open=true >}}
（`Nameserver 1`）名称服务器 1：
`aldo.ns.cloudflare.com`

（`Nameserver 2`）名称服务器 2：
`leanna.ns.cloudflare.com`
{{< /admonition >}}

### 解析子域名

在接入的域名下，点击`DNS`标签，点击`Add record`（添加记录）

|类型|名称|内容|
|:--:|:--:|:--:|
|CNAME|img|f004.backblazeb2.com|

{{< admonition type=example title=说明 open=true >}}
**类型：** 为`CNAME`；

**名称：** 为子域名，一般有以下几种：

- `img`
- `images`
- `image`
- `assets`（不仅存放图片，还有存放 `css`、`js`）
- `static`（不仅存放图片，还有存放 `css`、`js`）

**内容：** 为[此处第5条](#获取存储桶所在服务器)我们获取的存储桶所在服务器；
{{< /admonition >}}

输入后点击`Save`（保存）；

完成后确保`Proxy status`（代理状态）下的橙色保护盾是开启的状态, 这代表请求是通过了`Cloudflare`的`CDN`代理；

`Cloudflare`默认的 `TTL` 将被设置为 `auto`(自动)；

### SSL/TLS

在接入的域名下，点击`SSL/TLS`标签，选择`Overview`（概述）设置为`Full (strict)`【完全（严格）】

### 添加规则

我们需要新建`2`个规则：

在接入的域名下，点击`Rules`（规则）标签，选择`Page Rules`（页面规则）；

点击`Create Page Rule`（创建页面规则）

**【规则一】**

- **URL：** https://解析的名称.域名/file/存储桶名称/*

```
例如：https://img.baidu.com/file/blog/*
```

- **Pick a Settin（选取设置）：** `Cache Level`（缓存级别）

- **Select Cache Level（选择缓存级别）：** `Standard`（标准）

**【规则二】**

- **URL：** https://解析的名称.域名/file/\*/*

```
例如：https://img.baidu.com/file/*/*
```

- **Pick a Settin（选取设置）：** `Forwarding URL`（转发URL）

- **Select status code（选择状态代码）：** `302 - Temporary Redirect`（302 - 临时重定向）

- **Enter destination URL（输入目标 URL ）：** `https://secure.backblaze.com/404notfound`

## 最后的 Backblaze 设置

1. 打开`Backblaze`并登录，点击右上角`My Account`进入后台；

2. 选择`Buckets`（桶），点击`Bucket Settings`（桶设定）

3. 在`Bucket Info`（桶信息）输入以下内容：

```
{"cache-control":"max-age=43200000"}
```

4. 点击`Update Bucket`（更新桶）；

5. 点击`CORS Rules`（CORS规则）选择`Share everything in this bucket with all HTTPS origins`（与所有HTTPS来源共享此存储桶中的所有内容）

6. 点击`Update CORS Rules`

至此，我们就拥有了一个自定义域名的免费图床。

**地址形式为：** https://解析的名称.域名/file/存储桶名称/上传的文件名

```
例如：https://img.baidu.com/file/blog/test.png
```

## 精简链接

### 目的

去掉`URL`中无用的`/file/<bucket-name>/`部分；
 
**原链接：** https://img.baidu.com/file/blog/test.png 

**精简链接：** https://img.baidu.com/test.png

### 创建 Workers 服务

1. 在`Cloudflare`控制台，点击`Workers`标签，选择`Overview`（概述）；

首次使用按提示开通即可；

2. 点击`Create a Service`（创建服务），输入自取`Service name`（服务名称）

`Select a starter`（选择启动器）：`HTTP router`（HTTP路由器）

3. 点击右下`Create service`（创建服务） → `Worker`右侧的`Quick edit`（快速编辑）

4. 清空窗口内默认的内容，并粘贴以下内容到窗口内；

```
'use strict';
const b2Domain = 'img.domain.com'; // configure this as per instructions above
const b2Bucket = 'bucket-name'; // configure this as per instructions above
const b2UrlPath = `/file/${b2Bucket}/`;
addEventListener('fetch', event => {
	return event.respondWith(fileReq(event));
});

// define the file extensions we wish to add basic access control headers to
const corsFileTypes = ['png', 'jpg', 'gif', 'jpeg', 'webp'];

// backblaze returns some additional headers that are useful for debugging, but unnecessary in production. We can remove these to save some size
const removeHeaders = [
	'x-bz-content-sha1',
	'x-bz-file-id',
	'x-bz-file-name',
	'x-bz-info-src_last_modified_millis',
	'X-Bz-Upload-Timestamp',
	'Expires'
];
const expiration = 31536000; // override browser cache for images - 1 year

// define a function we can re-use to fix headers
const fixHeaders = function(url, status, headers){
	let newHdrs = new Headers(headers);
	// add basic cors headers for images
	if(corsFileTypes.includes(url.pathname.split('.').pop())){
		newHdrs.set('Access-Control-Allow-Origin', '*');
	}
	// override browser cache for files when 200
	if(status === 200){
		newHdrs.set('Cache-Control', "public, max-age=" + expiration);
	}else{
		// only cache other things for 5 minutes
		newHdrs.set('Cache-Control', 'public, max-age=300');
	}
	// set ETag for efficient caching where possible
	const ETag = newHdrs.get('x-bz-content-sha1') || newHdrs.get('x-bz-info-src_last_modified_millis') || newHdrs.get('x-bz-file-id');
	if(ETag){
		newHdrs.set('ETag', ETag);
	}
	// remove unnecessary headers
	removeHeaders.forEach(header => {
		newHdrs.delete(header);
	});
	return newHdrs;
};
async function fileReq(event){
	const cache = caches.default; // Cloudflare edge caching
	const url = new URL(event.request.url);
	if(url.host === b2Domain && !url.pathname.startsWith(b2UrlPath)){
		url.pathname = b2UrlPath + url.pathname;
	}
	let response = await cache.match(url); // try to find match for this request in the edge cache
	if(response){
		// use cache found on Cloudflare edge. Set X-Worker-Cache header for helpful debug
		let newHdrs = fixHeaders(url, response.status, response.headers);
		newHdrs.set('X-Worker-Cache', "true");
		return new Response(response.body, {
			status: response.status,
			statusText: response.statusText,
			headers: newHdrs
		});
	}
	// no cache, fetch image, apply Cloudflare lossless compression
	response = await fetch(url, {cf: {polish: "lossless"}});
	let newHdrs = fixHeaders(url, response.status, response.headers);

  if(response.status === 200){

    response = new Response(response.body, {
      status: response.status,
      statusText: response.statusText,
      headers: newHdrs
    });
  }else{
    response = new Response('File not found!', { status: 404 })
  }

	event.waitUntil(cache.put(url, response.clone()));
	return response;
}
```

{{< admonition type=note title=注意 open=true >}}
粘贴前请修改`b2Domain`和`b2Bucket`这两个变量的值；

`b2Domain`：为图床的二级域名；

`b2Bucket`：为`bucket`存储桶的名字；
{{< /admonition >}}

5. 点击`Save and Deploy`（保存并部署），然后返回

### 添加 Worker 路由规则

使访问`subdomain.domain.com/*`时，请求先由`worker`来处理。

1. 在接入的域名下，点击`Workers Routes`（Workers路由）标签；

2. 点击`HTTP Routes`（HTTP 路由）右侧的`Add route`（添加路由）；

- **Route（路由）：** 解析的名称.域名/*

```
例如：img.baidu.com/*
```

- **Service（服务）：** 选择上一步创建的服务名称；

- **Environment（环境）：** 保持默认即可；

3. 点击`Save`（保存），完成设置。

## 防盗链

1. 在接入的域名下，点击`Security`（安全性）标签，选择`WAF`；

2. 点击`Firewall rules`（防火墙规则）右侧的`Create firewall rule`（创建防火墙规则）

`Rule name` （规则名称）： 自己取一个名称

**When incoming requests match…（当传入请求匹配时...）**

- `Field`（字段）：`Referer`（引用方）

- `Operator`（运算符）：`does not contain`（不包含）

- `Value`（值）：博客地址，如：[ll.sc.cn](https://ll.sc.cn)

点击右侧`And`，在下一行继续；

- `Field`（字段）：`URI Full`（URI 完整）

- `Operator`（运算符）：`contains`（包含）

- `Value`（值）：https://解析的名称.域名，如：https://img.baidu.com

**Then…（则...）**

`Choose an action`（选择操作）：`Block`（阻止）

最后点击`Deploy firewall rule`（部署防火墙规则）完成设置；






## 参考链接

- [利用Backblaze的B2云存储，结合Cloudflare……](https://zhujiwiki.com/14698/)
- [我的图床解决方案，超详细！](https://zhuanlan.zhihu.com/p/491649092)
- [使用 Backblaze B2 和 Cloudflare Workers……](https://blog.meow.page/archives/free-personal-image-hosting-with-backblaze-b2-and-cloudflare-workers/)