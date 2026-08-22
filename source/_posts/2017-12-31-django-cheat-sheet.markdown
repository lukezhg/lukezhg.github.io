---
layout: post
title: "Django cheat sheet"
date: 2017-12-31 09:50
comments: true
categories: [computer]
tags: [django,virtualenv,python]
---
1、通过创建一个新的 virtualenv 为部署 Django 应用程序设置环境：  

    mkvirtualenv DjangoApp

要退出新的 virtualenv，请使用 deactivate。您可以使用 workon 在环境之间切换。要加载或在 virtualenv 之间切换，请使用 workon 命令：  

    workon DjangoApp

在您的当前环境中安装 Django   

    pip install Django

2、使用 django-admin 命令创建项目  

    django-admin startproject demoproject

3、进入demo project文件夹，使用python manage.py startapp 创建应用.  

    cd demoproject
    python manage.py startapp demoapp

4、测试项目服务器，Ctrl+C退出服务器。  

    python manage.py runserver


或者指定服务器ip和端口。  

    python manage.py runserver 0.0.0.0:8000


5、创建超级用户用于登陆django admin后台管理平台。  

    python manage.py createsuperuser admin


6、编辑设置文件和项目相关文件。    
settings.py 控制项目参数。    

```
    INSTALLED_APPS = [
        'django.contrib.admin',
        'django.contrib.auth',
        'django.contrib.contenttypes',
        'django.contrib.sessions',
        'django.contrib.messages',
        'django.contrib.staticfiles',
        'clips',
    ]
    
    DATABASES = {
        'default': {
            'ENGINE': 'django.db.backends.mysql',#mysql.connector.django
            'USER': 'root',
            'PASSWORD': '123456',
            'NAME': 'demoproject',
            'HOST': '127.0.0.1',
            'PORT': '3306',
        }
    }
```


urls.py 控制访问请求路径  

    from django.conf.urls import url
    from django.contrib import admin
    from demoproject.views import hello
    urlpatterns = [
        url(r'^admin/', admin.site.urls),
        url(r'^hello/$', hello),
    ]

views.py 控制访问请求的应答  

    from django.http import HttpResponse
    def hello(request):
        return HttpResponse("Hello world")

demoapp/models.py 控制数据结构（表格、变量、变量属性） 
```
    from __future__ import unicode_literals
    from django.db import models
    
    class User(models.Model):
        user_name = models.CharField(max_length=30)
        password = models.CharField(max_length=40)
        email = models.EmailField()
        headshot = models.ImageField(upload_to='headshot',null=True,blank=True)
        brief = models.CharField(max_length=100)
        join_date = models.DateField()
        user_star = models.CharField(max_length=30)
        def __unicode__(self):
            return self.user_name
    ......
```
demoapp/admin.py 控制后台注册和数据呈现  

```   
    from __future__ import unicode_literals
    from django.contrib import admin
    from .models import User, Clip, Link
    import sys;  
    reload(sys);  
    sys.setdefaultencoding("utf8")
    
    class UserAdmin(admin.ModelAdmin):
        list_display = ('user_name', 'password', 'email')
        search_fields = ('user_name', 'email')
    ......
    admin.site.register(User,UserAdmin)
    ......
```

7、当你修改models.py时，需要通过makemigrations将修改反应到数据库中去。  

    python manage.py makemigrations
    python manage.py migrate

8、利用template来呈现页面。  

首先要修改settings.py  

    TEMPLATES = [
        {
            'BACKEND': 'django.template.backends.django.DjangoTemplates',
            'DIRS': [os.path.join(BASE_DIR,'templates')],
            'APP_DIRS': True,
            'OPTIONS': {
                # ...

接下来建文件夹templates  

    \demoproject
        \demoproject
        \demoapp
        \templates
        manage.py

修改demoproject\views.py  

    from django.shortcuts import render
    import datetime
    def current_datetime(request):
        now = datetime.datetime.now()
        return render(request, 'current_datetime.html', {'current_date': now})

在templates文件夹，新建html模版文件current_datetime.html。  

\mysite_project\mysite\templates\current_datetime.html

```
{% raw %}
<html>
    <body>
        It is now {{ current_date }}
    </body>
</html>
It is now {{ current_date }}.
{% endraw %}
```

模版的继承，比如我们建一个地层模版，然后在这个模版的基础上加载子模版，这样就可以避免重复。  
参考：https://djangobook.com/templates-in-views/  

base.html  
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


current_datetime.html  
```html
{% raw %}
{% extends "base.html" %}
{% block title %}The current time{% endblock %}
{% block content %}
    <p>It is now {{ current_date }}.</p>
{% endblock %}
{% endraw %}
```

hours_ahead.html  

```html
{% raw %}
{% extends "base.html" %}
{% block title %}Future time{% endblock %}
{% block content %}
<p>
    In {{ hour_offset }} hour(s), it will be {{ next_time }}.
</p>
{% endblock %}
{% endraw %}
```

9、利用form来获取用户数据。  

mysite_project\mysite\books\templates\books\search_form.html
```html
{% raw %}
<html>
<head>
    <title>Search</title>
</head>
<body>
    <form action="/search/" method="get">
        <input type="text" name="q">
        <input type="submit" value="Search">
    </form>
</body>
</html>
{% endraw %}
```

mysite\books\urls.py
```python
    from django.conf.urls import url
    from books import views
    urlpatterns = [
        url(r'^search-form/$', views.search_form),
        url(r'^search/$', views.search),
    ]
```

mysite\urls.py
```python
    from django.conf.urls import include, url
    urlpatterns = [
    # ...
        url(r'^', include('books.urls')),
    ]
```
books\views.py

    from django.shortcuts import render
    def search_form(request):
        return render(request, 'books/search_form.html')
    def search(request):
        if 'q' in request.GET:
            message = 'You searched for: %r' % request.GET['q']
        else:
            message = 'You submitted an empty form.'
        return HttpResponse(message)

参考：https://djangobook.com/django-forms/  

定义表单类，更简洁的获取用户数据的方法。  

mysite_project\mysite\mysite\forms.py
```python
    from django import forms
    class ContactForm(forms.Form):
        subject = forms.CharField()
        email = forms.EmailField(required=False)
        message = forms.CharField()
```

mysite_project\mysite\mysite\views.py

```python
    from django.http import Http404, HttpResponse, HttpResponseRedirect
    from django.shortcuts import render
    import datetime
    from mysite.forms import ContactForm    
    from django.core.mail import send_mail, get_connection
    
    
    def contact(request):
        if request.method == 'POST':
            form = ContactForm(request.POST)
            if form.is_valid():
                cd = form.cleaned_data
                con = get_connection('django.core.mail.backends.console.EmailBackend')
                send_mail(
                    cd['subject'],
                    cd['message'],
                    cd.get('email', 'noreply@example.com'),
                    ['siteowner@example.com'],
                    connection=con
                )
                return HttpResponseRedirect('/contact/thanks/')
        else:
            form = ContactForm()
        return render(request, 'contact_form.html', {'form': form})
```

mysite_project\mysite\templates\contact_form.html

```html
{% raw %}
<html>
<head>
    <title>Contact us</title>
    <style type="text/css">
        ul.errorlist {
            margin: 0;
            padding: 0;
        }
        .errorlist li {
            background-color: red;
            color: white;
            display: block;
            font-size: 1.2em;
            margin: 0 0 3px;
            padding: 4px 5px;
        }
    </style>
</head>
<body>
    <h1>Contact us</h1>
    {% if form.errors %}
        <p style="color: red;">
            Please correct the error{{ form.errors|pluralize }} below.
        </p>
    {% endif %}
    <form action="" method="post" novalidate>
        <table>
            {{ form.as_table }}
        </table>
        {% csrf_token %}
        <input type="submit" value="Submit">
    </form>
</body>
</html>
{% endraw %}
```

10、urls进阶  

\urls.py

    from django.conf.urls import include, url
    from . import views
    urlpatterns = [
        url(r'^hello/$', views.hello),
        url(r'^time/$', views.current_datetime),
              url(r'^time/plus/(d{1,2})/$', views.hours_ahead),
    ]

\urls.py

    from django.conf import settings
    from django.conf.urls import url
    from . import views
    urlpatterns = [
        url(r'^$', views.homepage),
        url(r'^(\d{4})/([a-z]{3})/$', views.archive_month),
    ]
    if settings.DEBUG:
        urlpatterns += [url(r'^debuginfo/$', views.debug),]

\urls.py

    from django.conf.urls import url
    from . import views
    urlpatterns = [
        url(r'^reviews/2003/$', views.special_case_2003),
        url(r'^reviews/([0-9]{4})/$', views.year_archive),
        url(r'^reviews/([0-9]{4})/([0-9]{2})/$', views.month_archive),
        url(r'^reviews/([0-9]{4})/([0-9]{2})/([0-9]+)/$', views.review_detail),
    ]

更多参考： https://djangobook.com/advanced-views-urlconfs/