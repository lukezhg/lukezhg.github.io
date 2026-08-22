---
layout: post
title: "使用Octopress发布Github page博客"
date: 2012-12-27 21:05
comments: true
categories: [github,技术技巧]
tags: [github,标签云,octopress]
---
本来想尝试使用其他的文本编辑器，以后再说吧。我就用这个editplus干活了，先把使用github以及octopress搭建博客的整个过程梳理下来。

搭建的步骤如下：  
1.首先是准备工作，下载和安装必要的软件。  
2.然后是克隆octopress并安装   
3.接下来是将octopress配置好并发布博文。   
具体步骤可以重点参考[这篇](http://www.cnblogs.com/rubylouvre/archive/2012/06/10/2543706.html)文章。

## 具体步骤纪要：    
1. 准备工作，下载[gitinstaller](http://windows.github.com/), [ruby197](http://rubyforge.org/frs/?group_id=167), [devkit](https://github.com/downloads/oneclick/rubyinstaller/DevKit-tdm-32-4.5.2-20111229-1559-sfx.exe
), 然后安装。
gitinstalller和ruby197只要一路next过去就可以安装好，ruby我选择的都是c盘根目录。devkit解压到c盘根目录。安装如下：  
>     $ cd C:\DevKit  
      $ ruby dk.rb init  
      $ ruby dk.rb instal  

布置环境：
>     $ gem sources --remove http://rubygems.org/  
      $ gem sources -a http://ruby.taobao.org/  
      $ gem install rdoc bundler   
      $ vi Gemfile  #将行 ：source "http://rubygems.org/" 改为:source "http://ruby.taobao.org/"
      $ bundle install  #如果出错，改执行：bundle update; rake install   

2. 克隆远程octopress到本地文件夹，本地文件夹名称无所谓，比如我的就放在G:/github/myblog  
接下来进入git shell, 在命令行中执行一系列的命令来安装octopress，命令代码如下：  
>     $ git clone git://github.com/imathis/octopress.git myblog  
      $ cd myblog  
      $ rake setup_github_pages  
按照提示输入：git@github.com:username/username.github.com.git, 比如我的github用户名为lukezhg，那么我就需要输入 git@github.com:lukezhg/lukezhg.github.com.git   
>     $ rake generate   #生成本地文件
      $ rake preview  #实现本地预览 访问  http://localhost:4000 查看效果  （可选）
      $ rake deploy  #发布本地文件到服务器

保存博客源码到github source分支:
>     $ git add .  
      $ git commit -m 'blog source'  
      $ git push origin source

3. 初步配置octopress  
_config.yml文件：  

添加cname文件  
只需要在myblog\source目录下添加一个cname的文件，并在第一行写上你的域名，保存即可。

发布新博文（post）或者新页面（page）   
>     $ rake new_post["article name"]   
      $ rake new_page["page name"]

4. 继续完善  
添加侧边栏内容  

（1）添加导航  
修改myblog\source\_includes\custom目录下的navigation.html文件即可  

（2）添加分类  
[alswl/octopress-category-list](https://github.com/alswl/octopress-category-list)  

（3）自定义网站图标  
替换myblog\source目录下的favicon.png可以实现自定义网站图标  

5. 额外的说明   
（1）执行rake install如若出错：  
>     $ rake install
      $ rake aborted!
      $ You have already activated rake 0.9.2.2, but your Gemfile requires rake 0.9.2. Using bundle exec may solve this.
      $ (See full trace by running task with --trace)

==》修正办法为：
>     $ bundle update; rake install  

（2）添加CNAME文件后不生效==》手动在github网页上文件代码剪贴掉，保存，然后再粘贴回来，保存。

（3）atom.xml不生效==》使用同样的方法先把文件代码剪贴，保存，然后再粘贴回来。

（去除了Markdown语法，已经添加到octopress tips页面去了）

主要参考：
<a id="1"></a>[给 Octopress 加上标签功能](http://blog.log4d.com/2012/05/tag-cloud/)    
[利用GitHub Pages安装部署Octopress博客](http://www.cnblogs.com/rubylouvre/archive/2012/06/10/2543706.html)  
[在github上用octopress搭建博客过程纪要](http://www.cnblogs.com/rubylouvre/archive/2012/06/10/2543744.html)  
