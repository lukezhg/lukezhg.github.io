---
layout: post
title: "build a chat bot with ChatterBot Django"
date: 2017-10-21 22:27
comments: true
categories: 
tags: 
---
ChatterBot Django是基于Python和Django框架构建的一个聊天程序。  

其使用的基本方法可以查看[这个文档](http://chatterbot.readthedocs.io/en/stable/examples.html)。

根据已有的对话进行训练（其中对话数据储存在chatterbot_corpus文件夹中）  
    python manage.py train

打开服务器(访问[http://127.0.0.1:8000]浏览)  
    python manage.py runserver

<code>
目录：/webdev/chatterbot  
alice: http://127.0.0.1:8000/chat/  
ctrl + C 退出程序  
url.py 可以修改响应  
</code>

如果修改数据库文件的话，比如删除db.sqlite3文件，就需要运行下面的命令来从新配置框架。  
    python manage.py migrate


修改settings.py文件。  
<code>
    
    # ChatterBot settings
    CHATTERBOT = {
    'name': 'Django ChatterBot Example',
    'trainer': 'chatterbot.trainers.ChatterBotCorpusTrainer',
    'training_data': [
         'chatterbot.corpus.english.greetings',#set the traing data
         'chatterbot.corpus.custom.myown',
         'chatterbot.corpus.swedish.food',
    ],
    'django_app_name': 'django_chatterbot'
    }
</code>>

修改chatterbot_corpus文件夹中训练数据。  
训练数据格式如下
<code>
    categories:
    - greetings
    conversations:
    - - Hello
      - Hi
    - - Hi
      - Hello
    - - Greetings!
      - Hello
    - - Hello
      - Greetings!
    - - Hi, How is it going?
      - Good
    - - Hi, How is it going?
      - Fine
    - - Hi, How is it going?
      - Okay
</code>

###接下来可以做的  

可以尝试利用英语8000句来训练。  

如何为其添加三元组知识图谱？    

可以用她来做什么？练英语；学编程；或者其他。

如何把它迁移到平台上？

