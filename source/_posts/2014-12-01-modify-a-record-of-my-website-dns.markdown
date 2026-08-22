---
layout: post
title: "Modify A record of my website DNS"
date: 2014-12-01 21:28
comments: true
categories: [github]
tags: [github,log,DNS]
---
我的Email收到页面发布失败通知，原因是github更新了服务，需要永久性调整服务器IP地址，需要我相应更改DNS。一直没有时间修改，一直也不是特别清楚如何修改，今天终于把这个问题解决了。  

###Page build failure  
The page build failed with the following error:  

The custom domain for your GitHub Pages site is pointed at an outdated IP address. You must take immediate corrective action to ensure that your site remains available after December 1st, 2014. Additional details can be found at https://github.com/blog/1917-github-pages-legacy-ip-deprecation. For more information, see https://help.github.com/articles/setting-up-a-custom-domain-with-github-pages.  

###How do I know if I'm affected?  
[GitHub Pages Legacy IP Deprecation · GitHub](https://github.com/blog/1917-github-pages-legacy-ip-deprecation)  
The following helps!  
    On a Windows machine, you'll want to run nslookup your-domain.com and ensure that the output does not include any of the deprecated IP addresses (207.97.227.XXX, 204.232.175.XX, or 199.27.73.XXX).
    If you're on a Mac or Linux machine, simply paste this command into a terminal window, replacing your-domain.com with, your site's domain. dig your-domain.com | grep -E '(207.97.227.245|204.232.175.78|199.27.73.133)' || echo "OK". If you see the word "OK", you're all set.

###Configuring an A record with your DNS provider
[Tips for configuring an A record with your DNS provider - User Documentation](https://help.github.com/articles/tips-for-configuring-an-a-record-with-your-dns-provider/)  

关键信息  
With your DNS provider, create A records that resolve to the following IP addresses:
    192.30.252.153
    192.30.252.154


###修改DNS的A记录  
我的域名 - DNSPod  
https://www.dnspod.cn/Domain#zhangchunlei.com  

按照新的IP地址添加两条新的A记录，删除原来的A记录即可。