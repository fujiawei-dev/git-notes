---
date: 2020-07-14T16:20:00+08:00  # 创建日期
author: "Rustle Karl"  # 作者

# 文章
title: "Git 账号设置"  # 文章标题
description: "Git 多个账号设置、通过 SSH 访问、设置别名等"
url:  "posts/2020/10/04/gitconfig"  # 设置网页链接，默认使用文件名
tags: [ "git", "github", "gitlab", "config"] # 自定义标签
series: [ "Git 学习笔记"] # 文章主题/文章系列
categories: [ "学习笔记"] # 文章分类

# 章节
weight: 20 # 文章在章节中的排序优先级，正序排序
chapter: false  # 将页面设置为章节

draft: false  # 草稿
---

## 多账号共存

1. 清除全局设置

```shell
git config --global --list
git config --global --unset user.name "Rustle Karl"
git config --global --unset user.email "fu.jiawei@outlook.com"
```

2. 生成不同网站的 SSH Keys

- Github

```shell
ssh-keygen -t rsa -f c:/users/admin/.ssh/id_rsa.github -C "fu.jiawei@outlook.com"
```

- Gitlab

```shell
ssh-keygen -t rsa -f c:/users/admin/.ssh/id_rsa.gitlab -C "fu.jiawei@outlook.com"
```

然后添加到对应的网站中。

3. 配置 `~/.ssh/config` 文件

```conf
Host github.com
    HostName github.com
    User git 
    IdentityFile ~/.ssh/id_rsa.github

Host gitlab.com
    HostName gitlab.com
    User git
    IdentityFile ~/.ssh/id_rsa.gitlab
```

4. 验证是否成功

```shell
ssh -T git@github.com
```

```
Hi fujiawei-dev! You've successfully authenticated, but GitHub does not provide shell access.
```

```shell
ssh -T git@jixinwulian.cn:12053
```

## 设置别名

添加下列内容到 `$HOME` 目录的 `.gitconfig` 文件中：

```shell
[alias]
  co = checkout
  ci = commit
  st = status
  br = branch
  hist = log --pretty=format:'%h %ad | %s%d [%an]' --graph --date=short
  type = cat-file -t
  dump = cat-file -p
```

```shell

```

```shell

```

```shell

```

```shell

```
