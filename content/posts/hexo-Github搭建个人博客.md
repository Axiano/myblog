---
title: hexo+Github搭建个人博客
date: 2020-05-27 09:41:29
published: true
license: true
slug: hexo-get-github
cate: 教程
tags: [Hexo, GitHub]
cover_image: "./images/github.png"
canonical_url: false
description: "这个是我最早整理的搭建教程，有一些瑕疵"
---

## Hexo简介
Hexo是一款基于Node.js的静态博客框架,依赖少易于安装使用,可以方便的生成静态网页托管在GitHub和Coding上,是搭建博客的首选框架.大家可以进入<a href="https://hexo.io/zh-cn/" target="_blank" style = "text-decoration:none">hexo官网</a>进行详细查看,因为Hexo的创建者是台湾人,对中文的支持很友好,可以选择中文进行查看.


### Hexo搭建准备
<li>环境准备</li>
<a href="https://git-scm.com/" target="_blank" style = "text-decoration:none">Git官网<br><a>
<a href="https://nodejs.org/en/download/" target="_blank" style = "text-decoration:none">Node.js官网<br><a><br>

Git和Node.js,安装完以后,重启一下电脑,然后鼠标右键任意文件夹,会出现两个新的选项,选第二个,打开git bash.
输入<strong>git --version</strong> 查看git版本
分别输入<strong>ndoe -v</strong>,<strong>npm -v</strong 查看是node和npm否安装成功

<li>GitHub创建个人仓库</li>
<a href="https://github.com/" target="_blank"  style = "text-decoration:none"> GitHub官网<br></a>
注册完登陆后,新建仓库,仓库名必须要与你的刚才注册用户名相同,创建仓库只需要输入仓库名.


### 安装Hexo
创建一个文件夹,文件名任意,这个文件夹上直接右键git bash打开
输入命令

```
npm install -g hexo-cli
```
等待安装完毕,输入<strong>hexo -v</strong>查看版本.
接下来初始化一下hexo

```
hexo init myblog
```
myblog可以换自己的名,然后关闭git bash窗口.
点开你刚创建的文件夹,里面有一个myblog,右键git bash打开myblog.
安装hexo

```
npm install
```
安装完成以后，打开myblog文件夹下有:

```
node_modules: 依赖包
public：存放生成的页面
scaffolds：生成文章的一些模板
source：用来存放你的文章
themes：主题
_config.yml: 博客的配置文件
```

输入<strong>hexo g </strong>
输入<strong>hexo server</strong>    
开启本地hexo服务,浏览器输入<strong>localhost:4000</strong>就可以看到你生成的博客了.


### 生成SSH添加到 
回到你的git bash中

```
git config --global user.name "yourname"
git config --global user.email "youremail"
```
PS:这里的yourname输入你的GitHub用户名,youremail输入你GitHub的邮箱.</br>
然后创建SSH,一路回车.</br>
<strong>ssh-keygen -t rsa -C "youremail"</strong>youremail输入你GitHub的邮箱.</br>
这个时候它会告诉你已经生成了.ssh的文件夹。在你的电脑中找到这个文件夹.</br>
文件里有两个文件,用文本编辑器打开<strong>id_rsa.pub</strong>,然后复制.</br>
打开你的GitHub创建创建的仓库,点开setting,找到SSH keys的设置选项,点击New SSH key</br>
把你的<strong>id_rsa.pub</strong>,里面的信息复制进去.</br>
在git bash中,查看是否成功.</br>

```
ssh -T git@github.com
```
这里查看是否成功可以复制百度翻译查看.

### 将hexo部署到GitHub
这一步，我们就可以将hexo和GitHub关联起来，也就是将hexo生成的文章部署到GitHub上，打开站点配置文件<strong> _config.yml</strong>，翻到最后，修改,YourgithubName就是你的GitHub账户.

```
deploy:
type: git
repo: https://github.com/YourgithubName/YourgithubName.github.io.git
branch: master
```
```
hexo clean 清除了你之前生成的东西.
hexo generate 简化命令；hexo g :生成静态文章.
hexo deploy  简化命令；hexo d :部署文章.
```

