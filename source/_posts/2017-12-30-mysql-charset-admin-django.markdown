---
layout: post
title: "mysql charset admin django"
date: 2017-12-30 22:37
comments: true
categories: [computer]
tags: [mysql,charset,django-admin]
---
中文乱码永远是程序猿的痛！！  

今天使用django-admin就遇到了乱码问题，是仿照[django book](https://djangobook.com/adding-models-to-django-admin/)的model用法，做一个资源管理平台出现的问题。  

代码提示：mysql不能正确处理中文字符，于是一路google找到几个可能的解决措施：  

1、修改admin.py

    import sys;   
    reload(sys);  
    sys.setdefaultencoding("utf8") 

这个办法曾经帮助我解决了chatbot项目的乱码问题。  

2、修改mysql的配置文件/etc/my.cnf  
方案一：  

    [mysqld]
    character-set-server=utf8 
    [client]
    default-character-set=utf8 
    [mysql]
    default-character-set=utf8

方案二：utf8mb4兼容utf8，且比utf8能表示更多的字符，是utf8字符集的超集。所以现在一些新的业务，比如ISO等，会将MySQL数据库的字符集设置为utf8mb4。  

    [client]  
    default-character-set=utf8mb4  
      
    [mysqld]  
    character-set-server = utf8mb4  
    collation-server = utf8mb4_unicode_ci  
    init_connect='SET NAMES utf8mb4'  
    skip-character-set-client-handshake = true  
      
    [mysql]  
    default-character-set = utf8mb4  

3、关键还是要会使用命令诊断问题所在。  
我的问题出在新建的数据库中表单变量的字符码设置不是utf8，后来把数据库drop掉，重新配置my.cnf文件，然后重建mysql数据库就没问题了。  

4、常用的mysql命令和django命令。   

    mysql -u db_user -p
    SHOW DATABASES;
    CREATE DATABASE blog_data;
    drop database mydb;
    SHOW DATABASES;

CTRL + D退出mysql。  

通过show variables 命令查看字符编码，发现部分变量的编码果然不是utf8，难怪乱码。 

    show variables like '%char%’;

尝试重制响应的字符编码设置。

    set character_set_server=utf8;
    set character_set_database=utf8;
    show variables like '%char%’;

结果无效，于是进一步查看响应的数据库及其表单：  

    use my_db;
    show tables;
    show full columns from table1; ／／这条命令可以看到table1中的变量情况，发现果然编码有问题。 

尝试修改这个表单中的变量设置,也就是my_db.table1表单中的my_var变量字符编码。

    ALTER TABLE my_db.table1 MODIFY COLUMN my_var VARCHAR(255) CHARACTER SET utf8 COLLATE utf8_general_ci NOT NULL;

错误代码位置发生了改变，这说明改动有效，于是重新建立数据库（见3）。  

5、Django的一些命令。  

    python manage.py createsuperuser #生成admin登陆的超级用户和密码
    python manage.py makemigrations #当更改model时，通过此命令把变动反应到数据库中
    python manage.py migrate