---
title: 利用github完成网站维护与更新
date: 2021-08-27 00:57:28
tags: [github]
---

自己写一个主页index.html，替代原有的padlet，原有是padlet间歇性无法访问。但是发现提交到服务器没有反应。

问题是网站使用的是python django框架，每次更新页面需要重启python manage.py。重启的办法是首先要找到并关闭该进程，然后再重新开启。

###找到服务进程、kill并重启

```
netstat -tnlp #查看端口
kill 18283 # 关闭python所在进程
nohup python manage.py runserver 0.0.0.0:3000 #重新开启
```

这时本地服务就开启了，但是还需要开启反向代理才能访问。注意，这一步需要新建一个端口，否则会导致刚开启的3000服务终止。

```
/bin/systemctl restart nginx.service
```

### [](#服务器上让代码生效 "服务器上让代码生效")服务器上让代码生效

至于上传代码，则可以依靠强大的github来完成，其原理是更新本地代码，然后推送到github，然后登录服务器pull远程代码到本地，这样就实现了代码上传服务器。

```
cd /var/djangoweb/ictweb/
git status
git pull
```

其实也快成自己上传代码到服务器，只不过不便于多人协作管理。

###遇到的问题：
图片无法正常显示，需要使用static/images/logo.png这样的相对路径。

git合并冲突，需要先手动解决冲突，然后commit，之后就正常了。可以参考[这里](https://www.liaoxuefeng.com/wiki/896043488029600/900004111093344)
