---
title: 使用github+hexo创建博客
date:  2018-12-18 13:16:45 +0800
category: blog
tags: blog
excerpt: 使用github、hexo和git创建个人博客。
---

##搭建Node.js环境

```
因为Hexo是基于'Node.js'编写的。
```

下载安装包后保持默认设置，一路next点击即可安装完成。win+R ——> CMD ——>（node -v）——>（npm -v）

出现对应的node的版本号和npm版本号，表明Node.js安装成功！

##创建Github仓库

右上角菜单栏新建一个repository仓库

Github Pages仓库命名规范是：yourname.github.io

选中Inltlallze...

点击Create Repository

##搭建Git环境

```
使用Git将本地的Hexo生成的网页代码push到GitHub上。
```

####安装Git bash

打开鼠标右键菜单栏Git Bash ,输入'git --version'

显示出对应版本，安装成功！

####配置SSH Key

右键打开Git Bash，输入：

```
git config --global user.name "yourname"          //github用户名   
git config --global user.email  "xxx@qq.com"         //github注册邮箱
ssh-keygen -t rsa -C "邮箱地址"           //配置SSH
```

回车后会提示输入密码，这个密码会在提交项目时使用，如果为空的话测试时可以不用输入。

打开'C:\Users\bxm09\.ssh\id_rsa.pub'，此文件里面内容为刚才生成的密钥。

复制这个文件的所有内容，粘贴到github右上角下拉菜单的Settings -> SSH and GPG keys -> New SSH key内

粘贴时Title随便命名，把复制好的内容粘贴到Key中。

打开Git Bash输入命令测试是否配置成功：

```
ssh -T git@github.com1
```

如果看到

```
You’ve successfully authenticated, but GitHub does not provide shell access1
```

表示当前已经成功地连接上了自己的GitHub账户。

##搭建本地Hexo

```
Hexo是一个快速、简洁且高效的博客框架。Hexo使用 Markdown（或其他渲染引擎）解析文章，在几秒内，即可利用靓丽的主题生成静态网页。
```

在一个磁盘上面创建一个目录，随便命名，再右键使用Git Bash定位到目录中。

```
npm install -g hexo       //安装Hexo（默认安装为4.0版本）
hexo init                 //初始化Hexo
npm install               //安装Hexo所需要的组件
hexo clean & hexo g & hexo s        //本地启动博客（用于测试）
```

'hexo clean'清除缓存,'hexo g'生成静态页面,'hexo s'启动本地项目

在浏览器上访问'localhost:4000'，如果看到博客说明成功。

若测试时报错，则说明当前Hexo默认端口4000被占用，切换新的空闲的端口即可，输入命令：

```
hexo server -p 5000
```

最后输入Ctrl+C退出测试

##配置Deployment

打开文件夹中的'_config.yml'文件，修改下列配置

```
url: https://yourname.github.io.git


# Deployment
## Docs: https://hexo.io/docs/deployment.html
deploy:
    type: git
    repo: https://github.com/yourname/yourname.github.io.git
    branch: master
```

##安装推送插件

在文件夹中右键打开Git Bash ,输入：

```
npm install hexo-deployer-git --save
```

若是无法下载的话将npm换为cnpm

##部署

```
hexo clean       // 清除缓存
hexo g           // 生成静态页面
hexo d           // 部署
```

部署时会弹出提示框要求输入账号密码，账号输正常名，密码需要如下操作：

github右上角下拉菜单的Settings ——> Developer settings ——> Personal access tokens ——> Generate new token

创建一个新指令，标题随意，多选框全选，之后生成的一串指令代码就是密码

###到此就成功生成了一个专属于自己的博客