---
layout: post
title: "Python简明手册"
date: 2013-07-30 14:25
comments: true
categories: "技术技巧"
tags: [Python]
---
使用Python已经有几年了，也写过很多文本分析的程序，包括输入输出，写文案，抓网页等。最大的体会是Python的简洁性，你可以用最好的代码做最多的事儿，前提是你知道怎么做。Python可以让你实现人工智能、大数据分析、网页开发，几乎无所不能。所以，如果你想进入码农行业，你要认真的考虑一下是否要学习Python。  

本文列举了个人常用的命令，并不系统。后面期望不断改善。    

Python重要用法示例

    dir(list)#显示关键字相关的函数
    help(list.reverse)#查询某个函数的功能

set 让一个list变成无重复元素的set
例如：

    shapes = ['circle','square','triangle','circle']
    setOfShapes = set(shapes)
    setOfShapes 
    set(['circle','square','triangle']) 
     setOfShapes.add('polygon') 
    'rhombus' in setOfShapes 
    False 
    setOfShapes - setOfFavoriteShapes 
    setOfShapes & setOfFavoriteShapes 
    setOfShapes | setOfFavoriteShapes 


map和lambda

    map(lambda x: x * x, [1,2,3])
    [1, 4, 9]
    filter(lambda x: x > 3, [1,2,3,4,5,4,3,2,1])
    [4, 5, 4]

Object 先定义一个类，然后给类生成实例
定义如：

    class FruitShop:
    def __init__(self, name, fruitPrices):
        """
            name: Name of the fruit shop
            
            fruitPrices: Dictionary with keys as fruit 
            strings and prices for values e.g. 
            {'apples':2.00, 'oranges': 1.50, 'pears': 1.75} 
        """
        self.fruitPrices = fruitPrices
        self.name = name
        print 'Welcome to the %s fruit shop' % (name)
        
    def getCostPerPound(self, fruit):
        """
            fruit: Fruit string
        Returns cost of 'fruit', assuming 'fruit'
        is in our inventory or None otherwise
        """
        if fruit not in self.fruitPrices:
            print "Sorry we don't have %s" % (fruit)
            return None
        return self.fruitPrices[fruit]
        
    def getPriceOfOrder(self, orderList):
        """
            orderList: List of (fruit, numPounds) tuples
            
        Returns cost of orderList. If any of the fruit are  
        """ 
        totalCost = 0.0             
        for fruit, numPounds in orderList:
            costPerPound = self.getCostPerPound(fruit)
            if costPerPound != None:
                totalCost += numPounds * costPerPound
        return totalCost
    def getName(self):
        return self.name

调用winsound 函数  
<pre><code>
import winsound
# press a make a beep
if event.KeyID==65: winsound.Beep(200,9)
# press ESC play exit sound
if event.KeyID==27: winsound.PlaySound("SystemExit", winsound.SND_ALIAS)
</code></pre>


使用pyHook监听鼠标和键盘事件  
<pre><code>
import pythoncom
import pyHook

def onKeyboardEvent(event):
	global switch
	# 监听键盘事件
	if switch:
		print "Key:", event.Key
		print "KeyID:", event.KeyID
	return True #监听函数的返回值

def main():
	# 定义一个实例
	hm = pyHook.HookManager()
	# 监听所有键盘事件
	hm.KeyDown = onKeyboardEvent
	# 设置键盘监听器
	hm.HookKeyboard()
	# 循环并保持一直处于监听状态
	pythoncom.PumpMessages()
</code></pre>

用pyenv的基本操作命令管理python版本

    pyenv versions# 查看当前已安装的 python 版本
    pyenv install ... #安装指定版本的 python
    pyenv global python版本 #切换全局 python 版本
    source ~/.bash_profile
    pyenv local python版本 #切换当前文件夹下的 python 版本
    pyenv shell python版本 #切换当前 shell 中的 python 版本
    pyenv version #查看当前使用的 python 版本

python 数据库开发

取消所有8000进程：
    sudo lsof -t -i tcp:8000 | xargkill -9

创建项目
    django-admin startproject demoproject

创建应用
    cd demoproject
    python manage.py startapp TestModel

打开 mysql服务器
    mysql -u root -p

参考：[手册](http://djangobook.py3k.cn/chapter05/)


现在我们可以创建数据库表了。首先，用下面的命令对校验模型的有效性：

    python manage.py validate

模型确认没问题了，运行下面的命令来生成 CREATE TABLE 语句：

    python manage.py sqlall books
    python manage.py syncdb

打开服务器
    python manage.py runserver
    python manage.py migrate
    python manage.py makemigrations


查看sql服务是否启动

    ps -ef | grep mysqld#查看MySQL服务器是否启动
    service mysqld status#查看服务运行的状态

Mysql
mysql -u db_user -p
SHOW DATABASES;
CREATE DATABASE blog_data;
drop database mydb;
SHOW DATABASES;
Whenever you'd like to exit MySQL server, press CTRL + D.

show variables like '%char%’;
set character_set_server=utf8;
set character_set_database=utf8;

show variables like '%char%’;

ALTER DATABASE classlinkr DEFAULT CHARACTER SET utf8 COLLATE utf8_general_ci

use my_db;
show tables;

show full columns from clips_clip;  

ALTER TABLE classlinkr.clips_clip MODIFY COLUMN concept VARCHAR(255) CHARACTER SET utf8 COLLATE utf8_general_ci NOT NULL;

闲来无事，随便看看Python 3.0的文档，发现了一个很pythonic的模块：声音播放 for windows；凑个流行语叫做“很傻很天真”，不过挺好使得。

1 winsound.Beep

每一个都有不同的用法，一个一个来看吧。

    winsound.Beep(frequency, duration)
PC扬声器滴的一声，就是它了。第一个参数frequency表示分贝数，大小在37到32767之间。第二个参数是持续时间，以毫秒为单位(有耐心的话可以试试winsound.Beep(32767,9999999)，嘿嘿)。

2 winsound.PlaySound

    1. import winsound
    2. # Play Windows exit sound.
    3. winsound.PlaySound("SystemExit", winsound.SND_ALIAS)
    4. # Probably play Windows default sound, if any is registered (because
    5. # "*" probably isn't the registered name of any sound).
    6. winsound.PlaySound("*", winsound.SND_ALIAS)
    不过只能播放wav,不能播放wma和mp3文件，这2种还需要其他包的支持。

网站维护：  
使用Django框架  
前端口用h5和JS开发  
替换该文件之后，需要跑一下systemctl restart httpd命令才能生效

