---
layout: post
title: "在ubuntu中部署octopress发布博文"
date: 2013-02-04 12:17
comments: true
categories: [github,技术技巧]
tags: [ubuntu,github,octopress] 
---
以前使用的是windows下git环境更新octopress，现在想把所有与编程有关的东东都在ubuntu下完成。于是开始了折腾，并且折腾了很长时间。  
终于安装好了ubuntu并且初步使用布置好的git和ruby环境来更新博客。  

其实我是把windows下的所有博客项目有关的文件都拷贝到了ubuntu中来，然后在布置好环境的基础上实现正常使用的，居然真的可以。  

下面把遇到的问题记录汇总如下：  
一、安装和使用ubuntu过程中遇到的问题：  
1  安装ubuntu时遇到不能正常开机，或者进入系统后随机死机。  
2  安装ubuntu显卡驱动  
3  无线链接不能建立，尽管密码正确。  
4  如何安装和使用电池管理（tp-smapi）实现到达阈值自动停止充电  

二、安装git和ruby遇到的问题：  
1  更新git版本耗时过长以至于不能完成  
2  使用rvm安装ruby时找不到1.9.3版本  
3  如何设置让打开终端时自动加载rvm  

三、布置octopress遇到的问题：  
1 明明安装了gem bundler, 但是执行bundle install时仍然提示安装gem bundler  
2 使用rake generate命令时报错  

问题解决方法：  
1.1  选择了一个64位的amd版本的ubuntu进行安装。  
[Ubuntu 12.04.1 LTS](http://releases.ubuntu.com/12.04/)  

1.2  我的显卡是amd的，所以需要在amd官方网上下载闭源驱动进行安装。  
[AMD Catalyst™ Proprietary Display Driver - Linux x86 & Linux x86_64](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English)  

1.3  取消“启用无线”的勾选，然后在从新勾选上。 
但是这样治标不治本，于是参考了[这个网址](http://www.linuxdiyf.com/viewarticle.php?id=101861)  
> ppp 的很多选项都是默认的，其中lcp-echo-failure次数被设为4，而lcp-echo-interval设为30秒。也就是说，如果120秒钟之内，ADSL服务器没有给回echo-reply信号，UBuntu便会认为网络已经出了问题，就会断开网络，搞得人非常不爽。症结找到了，问题就要解决了，打开配置文件/etc/ppp/options，将lcp-echo-failure次数设为一个较大的数值就行了，我将该值修改为10。 

1.5  安装tp-smapi
参考：[http://www.linuxdiyf.com/linux/201108/688.html](http://www.linuxdiyf.com/linux/201108/688.html)  
但是始终无法完成最后一步：sudo modprobe tp_smapi  
但是反复安装和尝试了之后不知道为什么电池终于冲到71%就补充电了。原因还在继续查找中。  

2.1  使用https:而不是git:, 有可能是git被封造成的。  
参考：[Ubuntu git 安装和使用](http://www.linuxidc.com/Linux/2012-09/71193.htm)
将git clone git://git.kernel.org/pub/scm/git/git.git  
改为：git clone https://git.kernel.org/pub/scm/git/git.git  

2.2  跟换gem源，使用淘宝提供的源。  
参考：[在ubuntu中安装ruby 1.9.3_kingwmj_新浪博客](http://blog.sina.com.cn/s/blog_565e192a01013xjp.html)  
替换 gem 的 source：  
$ gem source -r http://rubygems.org/;gem source -a http://ruby.taobao.org  

2.3  更改.bash_profile  
参考：[在ubuntu中安装及使用rvm管理ruby版本 - 边晓宇@CSDN - 博客频道 - CSDN.NET](http://blog.csdn.net/abbuggy/article/details/8170899)  
在$HOME/.bash_profile文件中添加如下内容：  
[[ -s "$HOME/.rvm/scripts/rvm" ]] && . "$HOME/.rvm/scripts/rvm" # This loads RVM into a shell session.    
以便在开启一个终端会话时候加载RVM  
或者手动键入：$ source ~/.rvm/scripts/rvm  
在或者将该内容添加到~/.bashrc文件末尾。  

3.1  更换源后从新安装gem bundler，此外我顺便安装了rails。参考同上。    

3.2  检查所有博文以及设置文件冒号后面都应该有一个空格。  我的就是在tag：后忘了留空格，结果rake generate总是报错。  


参考文章：  
1  [在ubuntu中安装ruby 1.9.3_kingwmj_新浪博客](http://blog.sina.com.cn/s/blog_565e192a01013xjp.html)  
2  [使用Octopress遇到的问题 - 长老的 Octopress Blog](http://yangdd.github.com/blog/2012/09/14/issue/)
