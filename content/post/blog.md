+++
title = "使用hugo搭建个人博客网站"
tags = ['hugo','git']
categories = ['教程']
image = "/images/thumbs/0.jpg" 
draft = false
comments = true
toc = true
date = 2018-09-24
+++
接触github不久，前几天看到一个师兄十分简洁的博客网站，觉得很高大上，就开始去网上查找相关资料自己搭一个网站，下面就是我的搭建过程。想要模仿搭建一个属于自己的博客网站的话，只要把我的用户名“linwt”改成你的用户名即可。
# 安装

## Git
下载地址 https://git-scm.com/downloads

## hugo windows客户端
1. 下载地址 https://github.com/gohugoio/hugo/releases 
2. 下载后解压到任一目录（E:\\)
3. windows环境变量path添加hugo.exe所在路径（E:\hugo\_0.48\_Windows-64bit\）
4. 命令行中检查是否安装成功：hugo version

## github账户
熟悉基本的github操作

# 生成站点
1. 创建一个文件夹用于保存hugo要生成的文件（E:\hugo\）
2. 目录右键，选择git bash here，进入git命令行工具
3. 创建站点

		$ hugo new site mysite
	
	创建完成后会生成如图的目录结构  
![mysite](https://github.com/linwt/linwt.github.io/blob/master/images/post/mysite.png)
	
# 安装主题

## 克隆主题
/e/hugo/mysite/themes  

	$ git clone https://github.com/mjyi/Gemini.git

## 修改全局配置
mysite/config.toml

	baseurl = "https://linwt.github.io/"
	title = "Boy ln(～￣▽￣)～ "
	canonifyurls = true
	paginate = 3
	languageCode = "en-us"
	MetaDataFormat = "yaml"
	theme = "Gemini"
	disqusShortname = "" 
	googleAnalytics = "" 
	paginate = 6  
	
	[params]
	  Keywords = ""
	  Author = "Boy ln"
	  recentPostCount = 7
	  intro = ["知识改变命运","学习就是加速度"]
	
	[[params.social]]
	  title = "Email"
	  url = "mailto:boyln10086@gmail.com"
	[[params.social]]
	  title = "Github"
	  url = "https://github.com/linwt"
	[[params.social]]
	  title = "RSS"
	  url = "https://linwt.github.io/index.xml" #default index.xml
	
	[[menu.main]]
	  name = "Archives"
	  url = "/post/"
	  weight = -200
	[[menu.main]]
	  name = "Tags"
	  url = "/tags/"
	  weight = -180
	[[menu.main]]
	  name = "About"
	  url = "/about"
	  weight = -160  
	  
## 修改博客模板
mysite/themes/Gemini/archetypes/post.md

	+++
	title = ""
	tags = ['']
	categories = ['']
	image = "/images/thumbs/0.jpg" 
	draft = false
	comments = true
	toc = true
	date = 2018-09-24
	+++

	博客内容
	
# 博客预览

## 创建博客
/e/hugo/mysite  

	$ hugo new post/blog.md
	
创建完成后会在mysite/content/post下生成一个blog.md文件，可用Notepad编辑文件的博客内容
	  
## 启动hugo
/e/hugo/mysite  

	$ hugo server

## 浏览器访问
	localhost:1313

# 部署到github

## 新建库
库名必须为“用户名.github.io”（linwt.github.io）

## 生成静态网站文件
/e/hugo/mysite  

	$ hugo  
完成后会生成一个public文件夹，里面的文件就是要上传到github的静态网站文件

## 上传public
/e/hugo/mysite

	$ cd public
	$ git init
	$ git remote add origin https://github.com/linwt/linwt.github.io.git 
	$ git add -A
	$ git commit -m "hugo file"
	$ git pull origin master （若github上的库有修改的话要先pull）
	$ git push -u origin master
	输入用户名、密码

## 访问网站
https://linwt.github.io