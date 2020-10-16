---
title: Hexo搭建个人博客网站
date: 2020-07-09 17:42:38
tags:
categories: 
---

[toc]

## 1. Github创建个人仓库

登录[Github](https://github.com/)，点击New repository创建新仓库，Repository name填`username.github.io`，username即为GitHub账号名称。创建成功后为：

![](https://i.loli.net/2020/07/09/HyvpZsXWePKfJgG.png)

## 2. 安装Git

安装[Git](https://git-scm.com/download)，用于本地和Github之间的同步。

## 3. 安装Node.js

下载[Node.js](https://nodejs.org/en/download/)并安装（包含环境变量及npm），Hexo是基于Node.js的。

安装完成之后，打开命令行，输入`node -v`查看node版本号，检测Node.js是否安装成功；输入`npm -v`查看npm版本号，检测其是否安装成功。

## 4. 安装Hexo

创建一个文件夹，存放Hexo框架和以后发布的网页。进入文件夹，打开命令行，使用npm安装Hexo：

```
npm install -g hexo-cli
```

安装完成后，初始化博客：

```
hexo init blog
```

此时blog文件夹存放Hexo框架。

测试网站雏形，输入以下命令：

```
hexo g  #hexo generate 生成
hexo s  #hexo server 启动服务预览
```

打开浏览器地址栏输入localhost:4000，可预览网站。

## 5. 部署网站

进入blog文件夹，_config.yml文件为配置文件，打开配置文件，修改最后的deploy部分：

```
deploy:
	type: git
	repo: https://github.com/regina23/regina23.github.io.git
	branch: master
```

其中repo为Github创建仓库的地址。

安装Git部署插件，命令行中输入：

```
npm install hexo-deployer-git --save
```

此时，命令行中输入：

```
hexo clean  #清除缓存 
hexo g  #生成
hexo d  #hexo deploy部署
```

部署完成，打开浏览器地址栏输入username.github.io，即可看到网站。

## 6.发布文章

在命令行中输入：

```
hexo new "title"
```

其中title为文章标题，尤其标题有空格时，需要加引号。此时blog/source/_post文件夹中多了一个title.md文件，用Markdown编辑器打开编辑即可。



