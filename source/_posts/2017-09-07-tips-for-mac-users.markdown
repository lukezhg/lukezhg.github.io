---
layout: post
title: "tips for mac users"
date: 2017-09-07 18:10
comments: true
categories: 
tags: 
---
##快捷键： 
Finder
显示隐藏文件：shift + command + .  
回到主目录：shift+command+H

需要自己设置键盘快捷键，利用关键字 如 Copy， Cut， Paste， Select All。
复制：command+c
粘贴：command+v
拖拽的功能很厉害。


##bash命令：
复制：cp
目录：cd
列表：ls
移动：mv  源文件 目标文件

##批量重命名：  
Mac自带有这种功能，你只需要多选文件，然后右键，选择重命名这些文件，就会弹出批量重命名的窗口。  

#设置文件：  

    vi ~/.bash_profile  #编辑设置文件
    ls -l -a   列出指定目录下文件
               -l 显示文件的详细信息
               -a 显示目录下所有文件（包括隐藏文件）
               -d 显示指定目录pwd  显示当前的工作目录的路径
    touch 目录名：查看指定文件，若没有此文件则创建空文件；更改文件时间戳
    chmod 更改指定文件或目录的权限

##进程管理
    ps aux 静态查看进程
    top 动态查看进程
    kill 杀死进程
    kill -9 pid       杀死指定进程

##其他命令  
    man  显示帮助文件（按q退出）
    ifconfig 查看或修改ip地址
    sudo 以root权限执行一次命令
    clear / ctrl+L   清屏
    ctrl+C     无条件终止

##文件操作  

    rm –rf * 强制删除当前目录下所有文件
    rm -rf        删除文件或目录
    cp -r         复制文件
    mv         移动文件
    stat 文件名  查看文件详细信息
    find  查找文件
    find / -name *       查找文件
    mkdir   创建新目录
    rmdir   只能删除空目录

##修改文件：  
    echo:输出字符串或变量值
    echo “字符串” > file  #用>时，指定的文件若不存在，创建文件；若存在，覆盖原文件内容
    echo “字符串” >> file #用>>时，指定的文件若不存在，创建文件；若存在，在原文件内容后追加内容

##ssh文件同步  
同步到服务器

    scp -r localhome/* root@ip:/home/localhome/
同步到本地

    scp -r root@ip:/home/localhome/* localhome／

##多个Python共存

    pyenv versions #参看版本信息
    pyenv global 3.6.3 #切换3
    pyenv global 2.7.13 #切换到2
    source ~/.bash_profile