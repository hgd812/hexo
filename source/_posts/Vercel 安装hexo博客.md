---
title:  让我们用 GitHub Vercel 搭建一个 Hexo 站点
cover: https://pic1.zhimg.com/v2-41e1b825c51055f39c22b95777bc620b_1440w.jpg?source=172ae18b
---
> https://github.com
>
> https://vercel.com

## 安装准备

### Git

Git官网[Git for Windows](https://gitforwindows.org/) （如果官网下载慢，你可以到[npmmirror 中国镜像站](https://npmmirror.com/)下载）

### Node.js

下载[Node.js (nodejs.org)](https://nodejs.org/en/) 安装（如果官网下载慢，你可以到[npmmirror 中国镜像站](https://npmmirror.com/)下载）

### 验证安装

打开 `Git Bash` ，通过下面的代码查看版本 :

```
node -v
npm -v
```

## Git 设置

运行下方命令：

```
git config --global user.name 'Github name'
git config --global user.email '123456789@qq.com'
```


### 验证是否成功

打开 `Git Bash` ，运行下面的命令 :

```
ssh -T git@github.com # 此处邮箱地址不用改
```

如果提示 `Are you sure you want to continue connecting (yes/no)?` 请输入 `yes` 并回车。

如果提示下面即已经配置成功。

![img](http://tuchuang-10g.dongxiquan.cn/202209271143712.png)

看到这个信息则说明配置成功。

这时，本地环境配置完成。

### SSH and GPG keys

打开 Git Bash 运行下面的命令（修改下面自己的Github邮箱）

```
ssh-keygen -t rsa -C '123456789@qq.com'
```

连续回车3次，复制公钥（一般是 `C:/Users/{{你的用户名}}/.ssh/`）保存到 [SSH and GPG keys](https://github.com/settings/keys)


## 本地生成Hexo博客

首先安装hexo 如果已安装可跳过

```
npm install -g hexo
```

初始化hexo

```
hexo init
```

```
hexo g	#生成
hexo s	#启动服务
```



## 发布博客到互联网





[Butterfly 安装文档（一） 快速开始 | Butterfly](https://butterfly.js.org/posts/21cfbf15/)

## npm安装

```
npm i hexo-theme-butterfly
```

### 升级方法

在跟目录运行

```
npm update hexo-theme-butterfly
```

## 应用主题

修改 Hexo 根目录下的 _config.yml，把主题改为butterfly

```
theme: butterfly
```

## 安装插件

如果你没有 pug 以及 stylus 的渲染器，请下载安装：

```
npm install hexo-renderer-pug hexo-renderer-stylus --save
```

### vercel一键填写

```
npm i hexo-theme-butterfly ; npm install hexo-renderer-pug hexo-renderer-stylus --save
```

## 快速开始

### 写文章

创建新文章

```
hexo new 新文章
```

文件内容结构如下 :

```
---
title: {{文章名称}}
date: {{文章时间}}
categories: {{文章分类}}
tags: {{文章标签 [tag1,tag2,tag3]}}
description: {{文章摘要}}
---

{{文章正文}}
```

### 标签页

1. 前往你的 Hexo 博客的根目录
2. 输入 `hexo new page tags`
3. 你会找到 `source/tags/index.md`这个文件
4. 修改这个文件：

   记得添加 `type: "tags"`

   ```
   ---
   title: 标籤
   date: 2018-01-05 00:00:00
   type: "tags"
   ---

   ```

   ![image.png](https://api.onedrive.com/v1.0/shares/s!AsXA7AXl0Opo2UhLxYvOo3oFo0k-/root/content)

   ### 分类页


   1. 前往你的 Hexo 博客的根目录
   2. 输入 `hexo new page categories`
   3. 你会找到 `source/categories/index.md`这个文件
   4. 修改这个文件：

      记得添加 `type: "categories"`

      ```
      ---
      title: 分类
      date: 2018-01-05 00:00:00
      type: "categories"
      ---
      ```

### 常用命令

```
hexo new "postName"      # 新建文章
hexo new page "pageName" # 新建页面
hexo generate            # 生成静态页面至public目录
hexo server              # 开启本地预览服务器
hexo deploy              # 部署到远端
hexo help                # 查看帮助
hexo version             # 查看Hexo的版本
```

缩写

```
hexo s -g # 生成并本地预览
hexo d -g # 生成并上传
```
