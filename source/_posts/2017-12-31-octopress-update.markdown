---
layout: post
title: "octopress update"
date: 2017-12-31 23:46
comments: true
categories: 
tags: 
---
升级导致的问题。  

octopress用了很长时间了，最进粘贴代码时遇到了一些问题，以为升级可以解决，但是升级却带了新的麻烦。  

找到的一篇貌似实用的讨论：https://stackoverflow.com/questions/5286117/incompatible-character-encodings-ascii-8bit-and-utf-8  

但是试过了对我无效。   

回顾一下问题出现的原因，首先出现错误代码是：   

```
Liquid Exception: Unknown tag 'static' in
```

原因是我潜入了html代码，rake以为我要render这些代码，结果误认为有一些非法tag，所以提示上面的错误。   

解决的方式是： 利用 raw 和 endraw标记。如下：   
```html
{% raw %}
    <!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN">
    <html lang="en">
    <head>
        <title>{% block title %}{% endblock %}</title>
    </head>
    <body>
        <h1>My helpful timestamp site</h1>
        {% block content %}{% endblock %}
        {% block footer %}
        <hr>
        <p>Thanks for visiting my site.</p>
        {% endblock %}
    </body>
    </html>
{% endraw %}
```

如果没有这个标记，系统就会渲染这些代码的效果，结果就是有未知tag错误。  

我以为可以通过升级gem或者rake来解决这个问题，于是升级gem，升级时提示rake版本不够高。这时octopress还能正常工作。于是又安装了rvm和rake结果悲剧了。提示错误：   

    Liquid error: incompatible character encodings: UTF-8 and ASCII-8BIT

这个错误很严重，直接rake generate吹产生错误的页面。   

网上查的各种方法都没用，最后看自己的博客，发现一招删除rake： 

    sudo gem uninstall rake  

之后选择要删除的版本，我直接是删除所有高级版本，原因是我的octopress是5年前的，肯定和高级版本不合拍。于是试了一下，问题解决了！！   
