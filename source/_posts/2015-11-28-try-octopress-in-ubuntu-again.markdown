---
layout: post
title: "尝试在ubuntu系统中使用octopress"
date: 2015-11-28 17:43
comments: true
categories: [Ubuntu]
tags: [Ubuntu,octopress,rake]
---
实际上Ubuntu14.04上安装和使用octopress会更容易，因为大部分的程序已经安装好或系统自带。  
比如git,ruby等  

安装的过程基本可以参照：  
rominyue的[Ubuntu14.04下搭建Octopress](http://blog.rominyue.com/blog/2014/10/04/ubuntuxia-an-zhuang-octopress/)  

其中最容易出问题的是这里：  

	$ gem install bundler #要在gemfile中更新用taobao的https源  
	$ bundle install #出错提示版本号不对  
	$ rake install  

我遇到的麻烦是提示rake版本不对，显示错误提示：  
rake aborted! You have already activated rake 10.0.2, but your Gemfile requires rake 0.9.7.3  
后来删除了10.0.2新版本，就好了。  
	$ gem uninstall rake #之后选择要删除的版本即可  

参见：[控制rake版本](http://stackoverflow.com/questions/13489953/rake-aborted-you-have-already-activated-rake-10-0-2-but-your-gemfile-requires)  

多人协作时，编辑前先获得最近版本  
	$ cd octopress  
	$ git pull origin source  
	$ cd ./_deploy  
	$ git pull origin master  

保存博客源码到github source分支:
>     $ git add .  
      $ git commit -m 'blog source'  
      $ git push origin source  


最后重新建立ssh密钥，参见：[这里](https://help.github.com/articles/generating-ssh-keys/)  
