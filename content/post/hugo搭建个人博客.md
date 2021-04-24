---
title: "Hugo"
description: "用hugo搭建个人博客"
date: 2021-04-24T21:05:28+08:00
draft: true
---

## 环境部署

1. 安装git

   ```shell
   sudo apt-get install git
   ```

2. 安装hugo

   ```shell
   sudo apt-get install hugo
   ```



## 项目搭建

1. 创建hugo 项目

   ```shell
   hugo new site myblog
   ```

   注：

   - myblog为创建的hugo项目的根目录名称

2. 克隆一个主题

   ```shell
   cd myblog
   git clone https://github.com/vaga/hugo-theme-m10c.git themes/m10c
   ```

   注：

   - 如果cd到项目根目录，clone的地址后面需加上路径 “themes/主题名”
   - 如果cd到themes目录，直接git clone 地址

3. 新建一个博客

   ```shell
   hugo new post/blog.md
   ```

   注：

   - 在post目录下新建一个名为blog.md的博客文件
   - .md为Markdown格式的文件

4. 修改配置文件

   ```
   baseURL = "https://tian_828.gitee.io/"
   languageCode = "zh-cn"
   title = "靖哥的博客"
   theme = "m10c"
   ```

   注：

   - baseURL：需要部署到云端的地址
   - languageCode：语言，英文为en，中文为zh-cn
   - title：标题，浏览器标签栏将会显示的内容
   - theme：此项目所使用的主题的名称，必须与themes目录下的主题文件夹的名称一致

5. 编译

   ```shell 
   hugo -D
   ```

   注：

   - 此操作将整个项目编译成能够在浏览器显示的网页
   - 编译后会生成一个public文件夹，里面便是博客网页相关的文件

6. 本地启动

   ```shell
   hugo server -D
   ```

   或

   ```shell
   hugo server -t m10c --buildDrafts
   ```

   注：

   - -t：主题，themes文件夹下的主题文件夹名称

   - 指定地址：

     ```shell
     hugo --theme=m10c --baseURL="https://cjj.github.io" --buildDrafts
     ```



## 部署到码云或GitHub

1. 将生成public文件夹的内容推到远程仓库

   ```shell
   cd public/
   git init
   git commit -m " "
   git remote add blog https://gitee.com/code_from_cjj/blog.git
   git push -u blog master
   ```

2. 或者直接将整个项目目录推到远程仓库

   ```shell
   cd myblog
   cd ..
   git init
   git commit -m " "
   git remote add blog https://gitee.com/code_from_cjj/blog.git
   git push -u blog master
   ```

注：

- 第二种方式在部署的时候部署目录一定要到达public文件夹，如：

  /myblog/public

- 第一种方式无需设置部署目录，默认就好

  