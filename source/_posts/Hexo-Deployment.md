---
title: Hexo博客部署Github方案
tags:
  - Hexo
categories:
  - 教程
keywords: Hexo
cover: 'https://www.notion.so/images/page-cover/met_william_morris_1877_willow.jpg'
abbrlink: 6be29b87
date: 2024-06-23 00:00:00
copyright: false
---


# Hexo部署

# 准备

## 本地环境

- nodejs（>16 版本，最新的应该有 20 版本）：[Node.js — Run JavaScript Everywhere](https://nodejs.org/en)
- git（2.44.0）：[Git – Downloads](https://github.com/git-for-windows/git/releases/download/v2.44.0.windows.1/Git-2.44.0-64-bit.exe)

## Hexo

```bash
npm install -g hexo-cli
```

## Github

新建一个Repository，命名为`用户名.github.io`

# 本地配置

## 初始化Hexo

```bash
hexo init
npm install
```

## 部署本地看一下

```bash
hexo clean && hexo g && hexo s
```

# 远程Github推送

## 安装`deployer`

```bash
npm install hexo-deployer-git --save
```

打开`F:\blog\_config.yml`,找到 `deploy`。修改如下，其中`repo`填写你自己的仓库名字

![Image](/posts/6be29b87/1.png)

生成公私钥

```bash
ssh-keygen -t rsa -C "注册git使用的邮箱"
```

找到生成的 `id_rsa.pub` 公钥文件（在C:\Users\pc\.ssh下），复制公钥内容。

在 GitHub **头像下的 Settings** 里找到添加 SSH key，点击**New SSH key，**将刚刚生成的公钥 `id_rsa.pub` 文件里的内容复制到 Key 里面

```bash
ssh -T git@github.com
```

此时会显示以下内容，说明成功了

![Image](/posts/6be29b87/2.png)

## 部署到Github Pages

```bash
hexo clean && hexo g && hexo d
```

# 安装Butterfly主题

```bash
npm install hexo-theme-butterfly
```

## 应用主题

修改 Hexo 根目錄下的`_config.yml`，把主題改為`butterfly`

```bash
theme: butterfly
```

在 hexo 的根目錄創建一個文件`_config.butterfly.yml`，並把主題目錄的`_config.yml`內容複製到`_config.butterfly.yml`去。( 注意: 複製的是主題的`_config.yml`，而不是 hexo 的`_config.yml`)