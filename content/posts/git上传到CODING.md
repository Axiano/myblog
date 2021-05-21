---
title: git上传到CODING
date: 2020-07-29 16:30:54
published: true
license: true
slug: git-coding
tags: [教程,git,CODING]
cate: 笔记
cover_image: "./images/git.png"
canonical_url: false
description: "用git命令上传到coding"
---

:::note 前言
今天看到git可以上传代码到coding.net，感觉还是不错的，于是自己动手上传了一次，在期间发现了很多的问题，在这里总结一下，希望能帮到未上传成功的程序员们！
:::


<h2>先自己注册coding.net账号！</h2>
<h2>安装git 客户端</h2>
 先安装Git软件：<a href="http://git-scm.com/" target="_blank">Git for Windows下载</a>。  
 安装过程中的详细说明可参考：  
 https://jingyan.baidu.com/article/9f7e7ec0b17cac6f2815548d.html  
<h2>创建本地git 仓库</h2>
 现在本地创建一个文件夹，例如：D:\VS2017\Git\NETCORE  
 以<strong>管理员省份运行bash.exe</strong></span>（在安装的git bin文件夹下面）  
 切换到需要操作的目录下：cd D:/VS2017/Git/NETCORE  
 在该文件夹下面创建需要上传的文件  
<h2>输入命令：</h2>

```git
git init （会在此文件夹下生成一个隐藏的.git后缀文件)
git add . 
git commit -m "项目描述"
则在隐藏文件.git -->config用记事本打开
在ignorecase = true后面增加
[user]
email = yourname@me.com
name = yourname
则可以成功提交
```
<h3>将本地文件推送到coding服务器</h3>
git remote add origin https:// git.coding.net/用户名/项目名.git </br>
 （用户名是你登陆时的用户名，项目名称是你创建的一个项目名称）  </br>
<h3>上传到CODING</h3>
push origin master</br>
用户名和密码输入登陆coding.net的登陆用户名和密码：</br>
可以直接用-f（强制推送）</br>
push f origin master</br>
更新下coding.net 页面，发现已经将文件上传上去了
<h3>
总结一下用到的命令，主要有
</h3>

```git
git init
git add .
git commit -m "项目描述"
git remote add origin https://git.coding.net/用户名/项目名.git
git push origin master
```