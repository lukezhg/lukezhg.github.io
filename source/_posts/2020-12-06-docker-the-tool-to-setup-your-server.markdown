---
layout: post
title: "用docker在服务器上布置虚拟环境"
date: 2020-12-06 12:49
comments: true
categories: [服务器]
tags: [docker,appche,chatterbot,nginx]
---
最近想在服务器上布置一个聊天机器人。
简书上有教程：  

https://www.jianshu.com/p/5997f73eccb9  
https://www.jianshu.com/p/e18fb2166178  

不过我其实很早就尝试过，甚至还自己在本地测试成功了。于是就想把它弄到服务器上，试一试。

    cd /webdev/chatterbot
    python manage.py runserver
    alice: http://127.0.0.1:8000/chat/
    ctrl + C 退出程序
    url.py 可以修改响应


但是，如果直接把它拷贝到服务器上，却不行。因为它是具有环境依赖的，它需要一套底层环境才能运行。于是第一想法就是在服务器上假设相同的环境，但是服务器上以及有运行的项目了，这样势必改变原有的环境。  
如何让它运行起来，并且原来的项目功能不受影响呢？  
docker提供了很好的解决方案。  

docker的用途在于，它可以在服务器上建立多个虚拟环境，而在这个虚拟环境中安装的软件环境，并不会相互影响，比如chatterbot这个项目需要python3，但是其他应用可能需要的是python2.7，两个应用无法在同一个环境下运行。实际的情况更复杂，因为依赖的环境不仅是python。  

如何使用docker，网上有很多教程，比如：  
详细教程：https://blog.csdn.net/baidu_37832943/article/details/105218649  
阮一峰提供的教程：   
docker：http://www.ruanyifeng.com/blog/2018/02/docker-tutorial.html  
nginx-docker：http://www.ruanyifeng.com/blog/2018/02/nginx-docker.html

简明教程：  

    docker search nginx 
    #查找 Docker Hub 上的 nginx 镜像

    docker pull nginx 
    #拉取官方的Nginx镜像

    docker images nginx 
    #查找 REPOSITORY 为 nginx 的镜像

    #基于已有镜像创建并运行一个容器并映射到特定端口
    docker run --rm --name nginx-test -p 8080:80 -d nginx
          --rm：容器终止运行后，自动删除容器文件。
          --name nginx-test：将容器命名为nginx-test
          -p: 端口进行映射，将本地 8080 端口映射到容器内部的 80 端口
          -d：容器启动后，在后台运行
    docker container ps 
    #查看启动的docker容器
    curl localhost:8080 
    #测试页面



常用docker命令：

    docker ps -a
    docker pull centos
    docker run -itd centos /bin/bash
    docker exec -it (输入容器ID) bash
    yum install -y httpd
    ctrl+d
    docker commit -m “install httpd” -a “keyuan_test” (输入容器ID) 新的镜像名
    docker run -itd -p 8080:80 新的镜像名 /bin/bash
    docker exec -it 新的镜像产生的容器ID bash
    httpd -k start
    curl localhost:80
    ctrl+d
    curl localhost:8080



    docker pull centos
    docker run -itd centos /bin/bash
    docker exec -it (输入容器ID) bash
    httpd -k start
    docker commit containerid chatbot/live
    docker run -d -p 8000:80 chatbot/live /bin/bash
    curl localhost:8000

##appche

编辑appche设置文件： vi /etc/httpd/conf/httpd.conf

1.查看版本
    apache -v
    httpd -v
2.开启apche服务：
    apachectl start 
    apachectl stop
3.启动和关闭httpd的命令
    systemctl start httpd
    systemctl stop httpd
    systemctl restart httpd

网页位置：/var/www/html/  

##编辑 nginx配置文件
    vi /etc/nginx/nginx.conf

    nginx -t                    # 查看nginx状态
    nginx -s reload            # 重新载入配置文件
    nginx -s reopen           # 重启 Nginx
    nginx -s stop               # 停止 Nginx

##控制防火墙
    systemctl stop firewalld  
    systemctl start firewalld  
    systemctl mask firewalld  

    添加端口  
    firewall-cmd --zone=public --add-port=80/tcp --permanent  （--permanent永久生效，没有此参数重启后失效） 
    firewall-cmd --zone=public --add-port=1000-2000/tcp --permanent  
    重新载入  
    firewall-cmd --reload  
    查看  
    firewall-cmd --zone=public --query-port=80/tcp  
    删除  
    firewall-cmd --zone=public --remove-port=80/tcp --permanent  

##阿里服务器端口控制  
进入阿里云管理 ECS 实例-安全组-添加安全组规则，将 80 端口设置为入站方向，暂时向所有 ip 开放（开发时），再次尝试通过。  

这个设置更改很容易被忽略，造成用curl测试正常，但是公网无法访问。  

##列出所有端口
netstat -ntlp

https://www.cnblogs.com/xqzt/p/4919191.html


##使用docker的方法
将需要改变的文件映射到主机  
把所有不变的环境变为运行的容器  
将容器运行起来之后，就可以ctrl+D退出  
应用就跑起来了  



