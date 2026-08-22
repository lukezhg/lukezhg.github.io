---
layout: post
title: "在Ubuntu中布置和使用GAE"
date: 2013-08-31 18:07
comments: true
categories: "技术技巧"
tags: [Ubuntu,GAE]
---
本来在windows下我是建立了GAE开发环境的，但是python的版本是2.5,GAE的数据库又升级了，但是我又不想再windows下从新布置，觉得很麻烦。所以开始在Ubuntu中布置GAE。事实上在Ubuntu中的布置简单的难以相信。  
首先，下载[Google App Engine SDK for Python](https://developers.google.com/appengine/downloads#Google_App_Engine_SDK_for_Python)  
然后解压到你设定的目录（如 /home/）。布置就完成了。  

当然有些人喜欢再修改环境变量或者[使用In建立字符链接](http://www.php100.com/html/webkaifa/Linux/2010/0807/6386.html)，不过其实不做这些复杂的设置一样很好用。  

所以我就什么都没有做。当然前提你已经安装好python2.7了。  

下面简单说说，如何发布和测试你的第一个app。过程与windows下差不多，具体可以参考[这里](http://zhangchunlei.com/blog/2010/02/18/knowlege-of-gae/)。  

首先建立在解压好的google_appengine文件夹中建立一个myapps文件夹用于存放我自己的项目，然后在myapps文件夹下建立一个helloworld文件夹，并在这个文件夹下新建两个文件：helloworld.py以及app.yaml。两个文件的代码可以从[这里](https://developers.google.com/appengine/docs/python/gettingstartedpython27/helloworld)拷贝。  
测试你的项目，在google_appengine文件下打开终端，使用如下命令：  
<pre><code>
$ python dev_appserver.py myapps/helloworld
</code></pre>
打开[http://localhost:8080/](http://localhost:8080/)查看效果。  

ctrl+C 终止测试。  

使用如下命令上传项目（前提是你已经申请并在GAE上建立好了hellowrld应用）：  
<pre><code>
$ python appcfg.py update myapps/helloworld
</code></pre>
这样你的app就上传好了，打开地址欣赏一下吧。  

