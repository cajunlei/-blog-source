---
title: "Git - 使用手册"
subtitle: ""
date: 2021-10-20T13:24:51+08:00
lastmod: 2021-11-05T13:24:51+08:00
author: "守正"
authorLink: ""
description: ""
slug: "git_manual"
tags: ["Git"]
categories: ["Z-Turn"]
featuredImage: "https://cdn.chiga.ga/Posts/Z-Turn/01_Git/Cover.jpg"
---

在使用 Git 过程中学习的一些笔记分享……

<!--more-->

## Git 使用技巧

### 配置多个SSH-Key

#### 背景

当有多个 `git` 账号时，比如：

> a. 一个 `gitee` ，用于公司内部的工作开发；  
> b. 一个 `github` ，用于自己进行一些开发活动；

#### 解决方法

**第一步** 生成一个公司用的 `SSH-Key`

```git
ssh-keygen -t rsa -C 'xxxxx@company.com' -f ~/.ssh/gitee_id_rsa
```

**第二步** 生成一个 `github` 用的 `SSH-Key`

```git
ssh-keygen -t rsa -C 'xxxxx@qq.com' -f ~/.ssh/github_id_rsa
```

**第三步** 在 `~/.ssh` 目录下新建一个 `config` 文件（没有后缀）；

添加如下内容（其中 `Host` 和 `HostName` 填写 `git` 服务器的域名，`IdentityFile` 指定私钥的路径）

```git
# gitee
Host gitee.com
HostName gitee.com
PreferredAuthentications publickey
IdentityFile ~/.ssh/gitee_id_rsa

# github
Host github.com
HostName github.com
PreferredAuthentications publickey
IdentityFile ~/.ssh/github_id_rsa
```

{{< admonition type=info title=" 提示" open=true >}}

如果自动生成了以上内容，则不用自己修改，保持不动即可。

{{< /admonition >}}
**第四步** 用 `ssh` 命令分别测试

```git
ssh -T git@gitee.com
ssh -T git@github.com
```

### 同步代码至github和gitee

我们有时候开发代码需要把代码同步到多个远程库中，该如何操作呢？

`Git` 是分布式版本控制系统，同步到多个远程库时，需要用不同的名称来标识不同的远程库；而 `Git` 给远程库起的默认名称是 `Origin` ,所以我们需要修改、配置名称，以关联不同远程库，以 `Github` 和 `Gitee` 为例；

#### 同步方式

##### 一、命令方式同步

**第一步** 删除已关联的名为 `origin` 的远程库：

```git
git remote rm origin
```

**第二步** 再关联 `github` 的远程库：

```git
git remote add github git@github.com:chloneda/demo.git
```

**第三步** 再关联 `gitee` 的远程库：

```git
git remote add gitee git@gitee.com:chloneda/demo.git
```

##### 二、配置方式同步

修改 `.git` 文件夹内的 `config` 文件：

```Text
[core]
    repositoryformatversion = 0
    filemode = true
    bare = false
    logallrefupdates = true
[remote "origin"]
    url = git@github.com:chloneda/demo.git
    fetch = +refs/heads/*:refs/remotes/github/*
[branch "master"]
    remote = origin
    merge = refs/heads/master
```

将上述文件内容 `[remote "origin"]` 内容复制，修改 `origin` 名称，内容如下：

```Text
[core]
    repositoryformatversion = 0
    filemode = true
    bare = false
    logallrefupdates = true
[remote "github"]
    url = git@github.com:chloneda/demo.git
    fetch = +refs/heads/*:refs/remotes/github/*
[remote "gitee"]
    url = git@gitee.com:chloneda/demo.git
    fetch = +refs/heads/*:refs/remotes/gitee/*
[branch "master"]
    remote = origin
    merge = refs/heads/master
```

#### 查看远程库

通过以上两种方式的任一种方式配置完成后，我们查看以下远程库信息：

```git
git remote -v
```

可以看到两个远程库，说明配置生效了。

> gitee　 git@gitee.com:chloneda/demo.git (fetch)  
> gitee　 git@gitee.com:chloneda/demo.git (push)  
> github git@github.com:chloneda/demo.git (fetch)  
> github git@github.com:chloneda/demo.git (push)

#### 上传代码

```git
git add .
git commit -m "update"
```

#### 提交到github

```git
git push github master
```

#### 提交到gitee

```git
git push gitee master
```

#### 更新代码

```git
# 从github拉取更新
git pull github

# 从gitee拉取更新
git pull gitee
```

#### 踩到的坑

上述过程中，更新或提交代码时可能会遇到 `fatal:refusing to merge unrelated histories` (拒绝合并无关的历史) 错误，解决办法：

首先将远程仓库和本地仓库关联起来。

```git
git branch --set-upstream-to=origin/remote_branch  your_branch
```

其中，`origin/remote_branch` 是你本地分支对应的远程分支，`your_branch` 是你当前的本地分支。

然后使用 `git pull` 整合远程仓库和本地仓库。

```git
git pull --allow-unrelated-histories  # (忽略版本不同造成的影响)
```

重新更新、提交即可。

#### 强制提交

```git
# 强制推送到gitee
git push -f gitee master

# 强制推送到github
git push -f github master
```

{{< admonition type=danger title=" 注意" open=true >}}

不到万不得已，非常不推荐使用。

{{< /admonition >}}

### Git Bash 设置中文

`Git Bash` 本身就支持中文，只需要在打开 `Git bash` 后命令窗口右键「Options」 --> 「Windows」 --> 「UI languages」下拉选择 `zh_CN` 保存即可！！

{{< imgcapcdn src=`/Posts/Z-Turn/01_Git/2021-10-21_23-13-53.png` alt=右键菜单 >}}

{{< imgcapcdn src=`/Posts/Z-Turn/01_Git/2021-10-21_23-14-37.png` alt=设置界面 >}}

我为了使用方便，设置了「选中」 --> 「选中后立即复制」 ，「鼠标」 --> 「右键（粘贴）」、「中键（回车）」；

{{< imgcapcdn src=`/Posts/Z-Turn/01_Git/2021-10-21_22-47-28.png` alt=选中后立即复制 width=80% >}}

{{< imgcapcdn src=`/Posts/Z-Turn/01_Git/2021-10-21_22-47-23.png` alt=快速粘贴、回车 width=80% >}}

这时候就无法右键弹出菜单 -> 「设置」选项了；

可以用鼠标单击窗口左上角的图标 -> 「选项」进行设置；

{{< imgcapcdn src=`/Posts/Z-Turn/01_Git/2021-10-21_22-47-53.png` alt=弹出菜单 >}}

### Git GUI 汉化

**第一步** 下载汉化文件 [**zh_cn.msg**](https://files.cnblogs.com/files/chenghu/git-gui-zh-master.zip)

**第二步** 解压缩后得到 `zh_cn.msg` 文件。

{{< imgcapcdn src=`/Posts/Z-Turn/01_Git/2021-10-21_23-08-18.webp` alt=下载解压后的文件 >}}

将其放到 `/mingw64/share/git-gui/lib/msgs/zh_cn.msg` 路径下；

{{< imgcapcdn src=`/Posts/Z-Turn/01_Git/2021-10-21_23-09-35.webp` alt=将其放入此文件夹 >}}

如果没有 `msgs` 这个文件夹就自己创建之后再将这个汉化文件放进去；

重新打开 `Git GUI` ，你就会发现界面已经变成了中文了。

<img class=l-img src={{< param cdnPrefix >}}/Posts/Z-Turn/01_Git/2021-10-21_23-12-03.png alt=img width=95% >

## Git 疑难杂症

### SSH Key 突然失效

#### 出现的问题

2021 年 09 月 26 日发布的 `OpenSSH 8.8` 中移除了对 `RSA-SHA1` 的支持

- 最新的 `git for windows 2.33.1` 版本已使用 `OpenSSH 8.8`;
- `arch` 和 `manjaro` 等发行版的滚动升级比较激进，使用 `pacman -Syu` 就会升级所有软件到最新版本;
- 此时的表现就是之前还可以正常使用，`pacman -Syu` 或升级到 `git for windows 2.33.1` 之后使用 `git pull` 就出现 fatal: 无法读取远程仓库的提示;

如果您升级到 `OpenSSH 8.8` 或以上版本，则使用 `ssh` 推拉 `Gitee` 代码时会出现校验不通过的问题;

#### 临时解决方案

**第一种** 配置 `OpenSSH` 服务允许使用 `RSA-SHA1key`

在`~/.ssh/config`加上如下配置

```Text
Host gitee.com 
HostkeyAlgorithms +ssh-rsa 
PubkeyAcceptedAlgorithms +ssh-rsa
```

{{< admonition type=info title=" 提示" open=true >}}

这种方式不需要更换 `ssh key`，推荐 `Linux` 和 `windows git bash` 用户使用。

{{< /admonition >}}

**第二种** 换用其他算法生成 `ssh key`

```Text
ssh-keygen -t ed25519 -C "your@example.email"
```

之后到 `Gitee` 重新添加公钥即可

{{< admonition type=info title=" 提示" open=true >}}

这种方式需要更换 `ssh key`，推荐 `windows` 用户使用

{{< /admonition >}}

**第三种** 暂时不要使用 `OpenSSH 8.8` 及以上版本

### Hugo Server 报错

{{< imgcapcdn src=`/Posts/Z-Turn/01_Git/2021-10-24_13-19-12.png` alt=命令执行失败 width=75% >}}

```Text
$ hugo server
Start building sites … 
hugo v0.88.1-5BC54738+extended windows/amd64 BuildDate=2021-09-04T09:39:19Z VendorInfo=gohugoio
ERROR 2021/10/24 13:14:34 Failed to read Git log: fatal: your current branch 'master' does not have any commits yet
WARN 2021/10/24 13:14:34 

Current environment is "development". The "comment system", "CDN" and "fingerprint" will be disabled.
当前运行环境是 "development". "评论系统", "CDN" 和 "fingerprint" 不会启用.
Error: Error building site: logged 1 error(s)
Built in 306 ms
```

{{< admonition type=abstract title=" 解决方法" open=true >}}

先在 `Blog` 项目文件夹中右键 `git bash here` 输入命令；

```Text
git init 
```

接着尝试在 `git` 中执行命令；

```Text
hugo server
```

如果依然报错，请将 `Public` 中的 `.git` 文件夹中的内容复制 `Blog` 文件夹下面的 `.git` 文件夹中，选择「不覆盖」粘贴；

再次执行命令；

```Text
hugo server -D -e production
```

{{< /admonition >}}

成功执行，问题解决。

{{< imgcapcdn src=`/Posts/Z-Turn/01_Git/2021-10-24_13-35-31.png` alt=成功执行 width=75% >}}

## Git 命令

在开始前，我们先做出如下约定：

```Text
<localBranch>    指本地分支
<originBranch>   指远程分支
<branchName>     指分支名称
<repoAddress>    指仓库地址
<commit>         指某个commit记录
<tagName>        指标签名
```

### 设置命令别名

```Text
git config --global alias.st status         // git status ==> git st
git config --global alias.ci commit         // git commit ==> git ci
git config --global alias.co checkout       // git checkout ==> git co
git config --global alias.br branch         // git barnch ==> git br
git config --global alias.sh stash          // git stash ==> git sh
git config --global alias.pop "stash pop"   // git stash pop ==> git pop
```

### 查看

```Text
# 查看git版本
git --version
# 查看用户配置
git config --global  --list
# 查看当前分支信息
git status
# 查看本地提交历史
git log
# 查看本地最后n次提交
git log -n
# 查看本地分支
git branch
# 查看远程分支
git branch -r
# 查看所有分支
git branch -a
# 查看本地分支与的远程分支的关联情况
git branch -vv
# 查看标签
git tag
# 查看标签与之对应的提交信息
git show <tagName>
```

### 新建

```Text
# 新建一个本地分支，但不会切换到该分支上
git branch <localBranch>
# 为某个commit记录创建一个分支
git branch <brancName> <commit>
# 从某个分支新建一个分支
git branch <brancName> <localBranch>
# 新建一个本地分支，并切到该分支
git checkout -b <brancName>
# 新建一个本地分支，同时切换到该分支，并且关联该远程分支
git checkout -b <branchName> origin/<originBranch>
# 新建一个和远程同名的分支，同时切换到该分支，并且关联该远程分支
git checkout --track origin/<originBranch>
# 新建一个附注标签，并添加标签信息
git tag -a <tagName> -m "some message"
# 新建一个轻量标签
git tag <tagName>
# 给某一个commit他标签
git tag <tagName> <commit>
```

### 切换

```Text
# 切换到本地的另一个分支
git checkout <localBranch>
# 强制切换到本地的另一个分支，该操作会丢失在当前分支所做的修改，慎用
git checkout <localBranch> -f
# 新建一个本地分支，并切到该分支
git checkout -b <localBranch>
# 新建一个本地分支，同时切换到该分支，并且关联该远程分支
git checkout -b <branchName> origin/<originBranch>
# 切换到某个tag
git checkout <tagName>
```

### 删除

```Text
# 删除(一个或多个)本地该分支（不能删除当前所在的分支，不能删除没有合并到master上的分支）
git branch -d <localBranch> ...
# 删除(一个或多个)本地该分支（不能删除当前所在的分支，可以删除没有合并到master上的分支）
git branch -D <localBranch> ...
# 删除远程分支
git push -d origin <originBranch>
# 删除远程分支
git push origin -d <originBranch>
# 删除最新提交，只能删除本地的提交记录
git reset --hard HEAD^
# 删除本地tag
git tag -d <tagName>
# 删除远程tag
git push origin --delete <tagName>
```

### 拉取

```Text
# 拉取与当前分支关联的远程分支代码并进行合并
git pull
# 拉取与当前分支关联的远程分支代码并通过变基进行合并
git pull --rebase
# 拉取远程某个分支的代码并与当前分支进行合并
git pull origin <originBranch>
# 拉取远程某个分支的代码并与本地分支进行合并
git pull origin <originBranch>:<localBranch>
```

### 推送

```Text
# 推送到已关联的远程分支
git push
# 推送当前分支到指定远程分支
git push origin <originBranch>
# 推送某个本地分支到某个远程分支
git push origin <localBranch>:<originBranch>
# 推送指定tag到远程
git push origin <tagName>
# 推送所有不在远程的tag到远程
git push --tags
```

### 关联

```Text
# 推送并与远程分支建立联系，若远程不存在该分支则自动创建
git push --set-upstream origin <originBranch>
# 与远程分支建立关系，远程必须存在该分支
git branch --set-upstream-to=origin/<originBranch> <localBranch>
# 被废弃的方式 与远程分支建立关系
git branch --set-upstream <localBranch> origin/<originBranch>
# 将本地仓库与远程仓库关联
git remote add origin <repoAddress>
# 新建一个本地分支，同时切换到该分支，并且关联该远程分支
git checkout -b <branchName> origin/<originBranch>
```

### 暂存

```Text
# 贮存当前改动
git stash
# 查看贮存列表
git stash list
# 应用某个贮存（默认第一个），即git stash pop stash@{0} 
# 可修改最后的数字，来指定应用某个贮存，该命令同时会将应用的贮存删除
git stash pop
# 应用某个贮存（默认第一个），即 git stash apply stash@{0}
# 可修改最后的数字，来指定应用某个贮存，该不会删除贮存
git stash apply
# 删除某个贮存（默认第一个），即git stash drop stash@{0} 
# 可修改最后的数字，来指定删除某个贮存
git stash drop
# 查看某个贮存（默认第一个）做了那些改动，即 git stash show stash@{0} 
# 可修改最后的数字，来指定查看某个贮存
git stash show
# 删除所有贮存
git stash clear
```

### 克隆

```Text
# 克隆master分支代码
git clone <repoAddress>   
# 克隆某个分支的代码
git clone -b <originBranch> <repoAddress>
```

### 修改

```Text
# 修改分支名称 <oldBranch>原始分支名称 <newBranch>新分支名称
git branch -m <oldBranch> <newBranch>
```

### 合并

```Text
# 将某个分支合并到当前分支
git merge <branchName>
# 将当前分支变基到某分支
git rebase <branchName>
```

## 参考链接

- [git同步代码至GitHub和gitee（码云）](https://zhuanlan.zhihu.com/p/71163868)

- [根据功能分类Git命令](https://juejin.cn/post/7021034348077908005)

- [Git GUI汉化包来源](https://github.com/stayor/git-gui-zh)
