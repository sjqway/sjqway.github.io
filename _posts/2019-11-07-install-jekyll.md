---
layout: post
title: '在linux中安装常用插件和软件'
date: 2019-11-07
author: zsc
cover: 'http://on2171g4d.bkt.clouddn.com/jekyll-banner.png'
tags: zsc
---

> Transform your plain text into static websites and blogs.

### 分布式版本控制系统

- 配有上述两个仓库，在你的**电脑上有一个本地仓库**，在远程的**服务器上有一个远程仓库**。
- 我们在提交文件的时候会**先提交到本地仓库**，然后在有网络的情况下，**再从本地仓库提交到网络上的远程仓库**。
- `Git 就是一个典型的分布式版本控制系统，并且是免费的开源 的`

### 什么是 GitHub？

GitHub 就担任了上述的**远程仓库**这一角色，就是一个存放在外网服务器上的一个文件夹。

当然远程仓库除了 **GitHub** 之外，还有 Gitee（**码云**）。

### 安装git

- yum install git   安装git
- git --version 查看安装的Git版本，验证是否安装成功

### 源码编译安装Git

①　获取[github](https://github.com/git/git/releases)最新的Git安装包下载链接，进入Linux服务器，执行下载，命令为： wget https://github.com/git/git/archive/v2.17.0.tar.gz ；

②　压缩包解压，命令为： tar -zxvf v2.17.0.tar.gz ；

③　安装编译源码所需依赖，命令为： yum install curl-devel expat-devel gettext-devel openssl-devel zlib-devel gcc perl-ExtUtils-MakeMaker 耐心等待安装，出现提示输入y即可；

④　安装依赖时，yum自动安装了Git，需要卸载旧版本Git，命令为： yum remove git 出现提示输入y即可；

⑤　进入解压后的文件夹，命令 cd git-2.17.0 ，然后执行编译，命令为 make prefix=/usr/local/git all 耐心等待编译即可；

⑥　安装Git至/usr/local/git路径，命令为 make prefix=/usr/local/git install ；

⑦　打开环境变量配置文件，命令 vim /etc/profile ，在底部加上Git相关配置信息：

PATH=$PATH:/usr/local/git/bin

export PATH 

然后保存，退出！

⑧、输入命令 git --version ，查看安装的git版本，校验通过，安装成功。

### Ruby包管理工具介绍

- `gem` 全局包管理工具，类似于Python的pip, Node.js的npm -g

  gem install               安装组件

  - gem install -v            安装特定版本
  - gem list                  列出已经安装组件
  - gem sources -a            添加源
  - gem sources --remove      删除源

- `bundle` 项目包管理工具，可以理解为一个独立的运行环境

  - bundle update             更新项目依赖包
  - bundle install            安装项目依赖包
  - sudo bundle clean --force 强制删除不相关的包
  - bundle exe                在指定环境中运行

### GitHub Page和Jekyll介绍

**`GitHub Pages`** 免费无限容量的站点数据托管工具(*国内访问速度较慢*)，内置Jekyll服务，能将特定名称的代码仓库动态编译为静态网页

**`Jekyll`** 基于Ruby的静态网页生成系统，采用模板将Markdown(或Textile)文件转换为统一的网页

**统计** 统计工具主要是为了方便查看站点的访问情况，目前支持[百度统计](https://link.jianshu.com?t=http://tongji.baidu.com)和[Google Analytics](https://link.jianshu.com?t=http://www.google.com/analytics/)(可同时使用)

**评论** 评论工具可以为静态页面增加评论和分享功能，目前支持国内的[多说](https://link.jianshu.com?t=http://duoshuo.com)和国外的[Disqus](https://link.jianshu.com?t=https://disqus.com)

### 安装Jekyll

- 安装之前要进行切换到管理员状态
  sudo bash 改为管理员状态

- 升级所有软件
  $ sudo apt-get update
  $ sudo apt-get upgrade

- 第一步安装Ruby
  apt-get install ruby ruby -v

- 第二部更新Ruby gem源

  gem sources –remove https://rubygems.org/ gem source -a https://gems.ruby-china.org/

- 第三部安装ruby-dev
  apt-get install ruby-dev

- 第四部安装Jekyll
  gem install jekyll

- 第5步安装Jekyll
  gem install jekyll –verbose

- 检测是否安装成功
  jekyll –version 查看当前版本

### 安装Vim

- #### 1.检测

  执行`rpm -qa|grep vim`命令，会返回你正确安装的类库；正常情况下会呈现以下几种：

  ```css
  vim-common-7.4.160-4.el7.x86_64
  vim-enhanced-7.4.160-4.el7.x86_64
  vim-filesystem-7.4.160-4.el7.x86_64
  vim-X11-7.4.160-4.el7.x86_64
  vim-minimal-7.4.160-4.el7.x86_64
  ```

- #### 2.安装

  1）如果类库缺失：比如vim-common缺失，则执行`yum -y install vim-common`进行对应安装。
  2）如果需要一次性安装或者更新的话，则执行`yum -y install vim*`，等待安装完成即可。

- #### ３．如果没安装成功，输入下面三段代码

  1. yum install -y vim-minimal
  2. yum install -y vim-common
  3. yum install -y vim-enhanced

### 使用Vim

- 命令模式
  a/i/o进入增加模式
  光标指向的位置可以进行操作
  yy可以整行复制,nyy多行复制
  粘贴p
  (剪切)删除x ,删除多个字节 nx
  (剪切)删除整行dd,删除多行ndd
  撤销 u
  反撤销 ctrl+r
- 增加模式
  点击ESC可以切换至命令模式
  增加模式,可以写入文本内容
- 末行模式(启用命令模式后方能启用末行模式)
  : wq 保存退出
  :w! 强制保存
  :q! 强制退出
  :wq!强制保存退出 (管理员使用)
  set nu 设置行号
  取消 行号set nonu
  全文查找 /内容,n 进行切换
  全文替换 :%s/什么/替换内容/g
  范围替换 :开头行号,结束行号s/什么/替换内容/g
  建立配置文件
  vim ~/.vimrc
  内容 set nu,可以设置为所有文件都附带有行号
  光标移动
  gg 光标移动到第一行 ,G光标移动到最后一行
  用箭头代表上下左右
- 取消注释：
  Ctrl + v 进入块选择模式，选中你要删除的行首的注释符号，注意 // 要选中两个，选好之后按 d 即可删除注释，ESC 保存退出。
- 批量注释：
  Ctrl + v 进入块选择模式，然后移动光标选中你要注释的行，再按大写的 I 进入行首插入模式输入注释符号如 // 或 #，输入完毕之后，按两下 ESC，Vim 会自动将你选中的所有行首都加上注释，保存退出完成注释
- 进入文件 vim + filename

### 安装Vscode

- https://code.visualstudio.com/Download　直接下载.dev版本

### 思维导图和流程图练习

https://www.processon.com/setting练习网址

### Teambition团队协作和个人任务清单

https://www.teambition.com/organization/5dc3d400f684eb000153e988　练习网址



