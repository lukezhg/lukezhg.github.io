---
layout: post
title: "Ubuntu命令手册"
date: 2013-08-31 12:33
comments: true
categories: "Ubuntu"
tags: [Ubuntu,brief]
---
在摸索过程中经常使用的命令：   
安装和执行程序  
-  sudo apt-get install appname  安装程序应用
-  make install 编译并安装 .tar.gz2   
-  sh xx.sh  执行.sh文件  
-  sudo su 切换到root用户  
-  sudo exit 推出root用户  

python相关命令  
-  python xx.py 执行py文件  
-  python -V  

设置命令：  
设置工作台数量：（纵向数目1，横向数目4）  
	gconftool-2 --type=int --set /apps/compiz-1/general/screen0/options/vsize 1
	gconftool-2 --type=int --set /apps/compiz-1/general/screen0/options/hsize 4


察看RVM可供安装的ruby版本和现用版本  
-  rvm list known  
-  rvm list  

编辑文本文档  
-  vi filename  
-  gedit filename  

发布octopress博文  
-  rake generate  
-  rake preview  
-  rake deploy  
-  rake new_post["post title"]  

文件操作  
-  cp  复制文件 到另外一个目录  
-  mv 文件 文件目录  
-  rm 文件名文件名删除一个文件或多个文件  
-  rm –rf 非空目录名删除一个非空目录下的一切  

-  touch 文件名创建一个空文件  
-  mkdir 目录名创建一个目录  
-  rmdir 空目录名删除一个空目录  
-  lsusb 查看usb接口  
-  lspci 查看pci接口  

批量改名  
	rename 's/lecture/slide/' *.jpg  
将当前目录中所有jpg文件名中lecture替换为slide。  

批量替换文件内容  
	perl -pi -e 's|Windows|Ubuntu|g' `find ./ -type f`
> 查找当前目录下面的所有文件，把内容包含Windows的所有字符串替换成Ubuntu。如果要查找的字符窗包含特殊字符如 ()/*$&’`| 还得用 \ 转义
<http://www.linuxdiyf.com/viewarticle.php?id=90071>

