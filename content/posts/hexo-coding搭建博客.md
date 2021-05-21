---
title: hexo+coding搭建博客
date: 2020-05-27 19:34:56
published: true
license: true
slug: hexo-get-coding
tags: [hexo,CODING]
cate: 教程
cover_image: "./images/coding.png"
canonical_url: false
description: "小白可以参照这篇文章，搭建一个属于自己的blog"
---
:::note 前言
因为CODING是国内的托管网站，所以打开网页的速度比GitHub快，但是各有各有优点，推荐使用CODING。
我搭建博客用的是hexo框架，因为这个框架比较简单轻便，而且依赖于node.js管理包文件，这里提一句，基于coding或者github搭建的博客都是静态页面，轻量简洁，相对的功能上不如Wordpress那样强大，但是我们也可以用第三方插件实现文章统计，网站计数，博客评论等功能，看自己喜好加吧。
好了，现在我们开始操作。
:::

<h2>
安装环境 
</h2>

环境三个：node,git和hexo，hexo最后装

<h3>
git
</h3>
去<a href="https://git-scm.com/" target="_blank" style = "text-decoration:none">Git官网</a>下载，安装步骤就不停next就好。
官下载的慢，可以去<a href="https://npm.taobao.org/mirrors/git-for-windows/" target="_blank" style = "text-decoration:none">淘宝源Git</a>下载
<h3>
node
</h3>
<span style="cursor:auto">去<a href="https://nodejs.org/en/download/" target="_blank" style = "text-decoration:none">Node.js官网</a>下载，安装步骤就不停next就好。

<h3>
检查是否安装成功
</h3>
这个很简单，<br>
鼠标右键，选择Git Bash Here,然后输入：<br>

```
it --version
ndoe -v 
label primary @npm -v
```
每一条指令回车都会显示自己版本号

<h3>
node
</h3>
鼠标右键，选择Git Bash Here,然后输入：<br>

```
npm install -g cnpm --registry=https://registry.npm.taobao.org
```
这里用cnpm是因为npm连接不太稳定，而cnpm是淘宝团队提供的一个npm镜像库，国内访问非常快，以后的npm命令就在前面加一个c，使用方法完全相同。然后：<br>

```
cnpm install hexo-cli -g 
```
在某个盘下新建一个文件夹，取名随意，我是blog。
然后在这个文件夹下右键，Git Bash Here，然后：<br>

```
hexo init
```
即在此初始化hexo源文件，需要这个blog文件夹初始为空。然后：

```
cnpm install 
```
<br>
这一步是安装通用的npm包文件，如果有特定的npm包需要额外添加。我们除了通用包，还要一个hexo部署博客的包文件：<br>

```
cnpm install hexo-deployer-git --save
```
<br>
现在需要的基础包就安装好了。

<h2>
 测试本地发布
</h2>

把hexo的核心，把md文件转为静态页面，并添加主题样式和必要的链接，生成的文件在public下。然后：

```
hexo g
```
打开本地服务：

```
hexo s 
```
这样，就是在本地预览博客，在浏览器地址栏中输入：

```
http://localhost:4000
``` 
就可以看到结果了。
现在只能自己浏览，想要让其他人也能看到，就需要部署到服务器上。租服务器不仅要花费，还要自己搭建web环境，太麻烦了，而且不适合学生党和技术不够的同学们，万幸GitHub和CODING都提供了静态页面解析的功能，所以我们把public文件夹下的内容push到一个git远程仓库就可以了。现在我们需要开始发布到CODING的步骤。

<h2>
 本地博客部署到CODING
</h2>
<h3>
注册CODING账号
</h3>
<a href="https://coding.net/" target="_blank" style = "text-decoration:none">CODING官网</a><span style="cursor:auto">去注册一个CODING账号。<br>

<h3>
设置CODING账号
</h3>
1.进去以后 全部项目- 新建项目，点第一个，项目名称就填你的用户名，勾选启用 README.md 文件初始化项目。<br>
鼠标放在右上角的头像上，点 团队管理-团队设置=高级设置-实名认证<br>
2.左下角，项目设置-功能开关-打开，持续集成 和 持续部署<br>
回到项目的主页面，在左侧，持续部署-静态网站-立即部署，上面的访问地址就是你自己的域名。

<h3>
本地仓库和远程仓库关联
</h3>
现在有了远程仓库，就要把本地仓库和远程仓库关联起来，首先在blog目录下Git Bash Here，然后输入：<br>

```
 git config --global user.email "你的邮箱" 
git config --global user.name "你的手机号"
```
<br>
然后我们给本地添加一个SSH key，这样的话每次部署就不用输密码。在Git Bash Here中输入：<br>

```
ssh-keygen -t rsa -b 4096 -C "你的邮箱" 
```
<br>
接下来一直回车就可以了。
成功会出现以下代码：

```
-# Creates a new ssh key, using the provided email as a label
-# Generating public/private rsa key pair.
Enter file in which to save the key (/Users/you/.ssh/id_rsa): [Press enter]  // 推荐使用默认地址,如果使用非默认地址可能需要配置 
```

本地地打开 id_rsa.pub 文件（一般在c盘用户文件夹下，进入你的用户文件夹，在.ssh文件里），复制其中全部内容。
回到CODING，把鼠标放在右上角的头像上，进入 个人设置-SSH公钥-新增公钥，然后输入密码可添加完成。PS:公钥名称可以写key.
现在验证一下是否添加SSH公匙成功，在Git Bash Here中输入:
<span class="label label-primary">&nbsp;&nbsp; ssh -T git@你的手机号.coding.net &nbsp;&nbsp;</span><br>
如果成功，会出现以下代码：

```
Are you sure you want to continue connecting (yes/no)? yes 
Warning: Permanently added ‘git.coding.net,61.146.73.68’ (RSA) to the list of kn own hosts.
Enter passphrase for key ‘/c/Users/xxx/.ssh/id_rsa’: Coding.net Tips : [ Hello xxx! You have connected to Coding.net by SSH successfully! ]
```


<h2>
部署博客到CODING
</h2>

回到CODING，打开项目的主页面，在右下测有 HTTPS 选择成 SSH，然后复制后面的链接。

百度下载  Notepad++ 
用‘Notepad++’打开blog文件夹下的_config.yml文件，把_config.yml翻到最后有下面几行行代码：

```
deploy:
type: git
repo: 刚才复制的SSH链接 
branch: master
```


还有就是要注意这里yml文件是用的yaml脚本语言，对语法要求很严格，每个:后面要加上空格，没空格会编译出错。
现在我们就可以开始部署博客了,记得部署之前最好清理一遍public文件夹,也就是这样：

```
hexo clean 
hexo g 
hexo d 
```
最后复制你的域名，打开就可以看到你的博客了。



