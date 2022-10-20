---
title: "Github - 使用笔记"
subtitle: ""
date: 2021-10-24T12:27:12+08:00
lastmod: 2021-10-24T12:27:12+08:00
author: "守正"
authorLink: ""
description: ""
slug: "github_use_notes"
tags: ["Github"]
categories: ["Z-Turn"]

hiddenFromHomePage: true
hiddenFromSearch: false
---

<!--more-->

## Github 管理

### 删除历史版本

**问题**：旧项目提交到 `Git` 上，历史记录中会包含项目密码等敏感信息，或者强迫症感觉不舒服，或者是 `Pull` 的时候文件太大，访问速度又比较感人，这时候我们可以删除这些历史记录，保留最新一次版本。

#### 操作步骤

**第一步** 切换分支：

```git
git checkout --orphan latest_branch
```

<img class=l-img src={{< param cdnPrefix >}}/Posts/Z-Turn/03_Github_note/2021-10-24_12-24-26.png alt=img width=75% >

**第二步** 添加所有文件到暂存区：

```git
git add -A
```

<img class=l-img src={{< param cdnPrefix >}}/Posts/Z-Turn/03_Github_note/2021-10-24_12-24-48.png alt=img width=75% >

**第三步** 提交更改：

```git
git commit -am "commit message"
```

<img class=l-img src={{< param cdnPrefix >}}/Posts/Z-Turn/03_Github_note/2021-10-24_12-25-28.png alt=img width=75% >

**第四步** 删除分支：

```git
git branch -D master
```

<img class=l-img src={{< param cdnPrefix >}}/Posts/Z-Turn/03_Github_note/2021-10-24_12-25-52.png alt=img width=75% >

**第五步** 重命名分支：

```git
git branch -m master
```

<img class=l-img src={{< param cdnPrefix >}}/Posts/Z-Turn/03_Github_note/2021-10-24_12-26-03.png alt=img width=75% >

**第六步** 强制提交到远程仓库：

```git
git push -f origin master
```

<img class=l-img src={{< param cdnPrefix >}}/Posts/Z-Turn/03_Github_note/2021-10-24_12-26-20.png alt=img width=75% >
