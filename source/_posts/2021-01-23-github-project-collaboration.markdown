---
title: 如何使用github进行项目协作
date: 2021-01-23 13:45:00
tags: []
---

### [](#终端窗口Shell的切换 "终端窗口Shell的切换")终端窗口Shell的切换

改变默认的shell脚本：

```
chsh -s /bin/zsh
```

从 zsh 切换回 bash

```
chsh -s /bin/bash
```

zsh 和 bash 的环境变量
bash 的环境变量是~~/.bash_profile文件。
zsh 的环境变量是~~/.zshrc文件。

PS：如果从 bash 切换到 zsh，但想保留 bash 所设置的环境变量，可在 .zshrc文件末尾添加 source ~/.bash_profile即可。

参考：[MacOS 的 zsh 和 bash 切换](https://www.jianshu.com/p/8d822ce0d425)

### [](#github工作思路和流程 "github工作思路和流程")github工作思路和流程

项目负责人建立项目并且邀请合作者共同开发
合作者打开项目地址，接受邀请。
项目负责人将合作者ssh-pub添加到项目，便于合作者访问。

#### [](#如何查看ssh-pub公钥 "如何查看ssh-pub公钥")如何查看ssh-pub公钥

```
cd ~/.ssh
cat id_rsa.pub
```

复杂公钥给项目负责人，进行添加。建立合作关系。

#### [](#如何查看浏览器提交的数据 "如何查看浏览器提交的数据")如何查看浏览器提交的数据

command+alt+i 调出后台
在web交互实验页面上输入正确的答案
点击属性变为全局变量temp1
利用json.stringfy(temp1) 转变为字符

复制实验正确答案到文件位置

#### [](#上传代码 "上传代码")上传代码

```
git checkout ictweb-sf #转到ictweb-sf分支
git pull #继承合作的修改
git add .
git commit -m "index links"
git push #更新修改到远程文件
```

#### [](#合并分支 "合并分支")合并分支

为了让分支ictweb-sf生效，需要将ictweb-sf的更改合并到main上

```
git checkout main
git commit -m "message"
git merge ictweb-sf
```

#### [](#服务器上让代码生效 "服务器上让代码生效")服务器上让代码生效

```
cd /var/djangoweb/ictweb/
git status
git pull
#systemctl restart httpd.service
nginx启动、停止、无间断服务重启
```

#### [](#nginx启动、停止和重启 "nginx启动、停止和重启")nginx启动、停止和重启

```
[root@example ~]# service nginx start
[root@example ~]# service nginx stop
[root@example ~]# service nginx reload
```
