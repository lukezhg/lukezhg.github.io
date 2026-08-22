---
layout: post
title: "Swf send data to Java Script"
date: 2017-12-29 19:21
comments: true
categories: [computer]
tags: [flash,swf,JS]
---
Flash制作动画非常便捷，但是如何能够把用swf文件收集的数据发送給JS处理呢？下面是一个简单的例子：  
1、首先在html网页中通过object嵌入swf文件  

```
{% raw %}
    <body>
    <object type="application/x-shockwave-flash" data="{% static "flash/test.swf" %}"  name="test" width="550" height="400">
    <param name="allowScriptAccess" value="sameDomain" /> 
    <param name="movie" value="{% static "flash/test.swf" %}" />
    </object>
    </body>
{% endraw %}
```


2、在网页的头部嵌入要调用的函数hello  

```
    <script>
        function hello(v){ 
            alert("hello: "+v);
            document.location.href = '/search';
        } 
        function thisMovie(movieName) { 
            if (navigator.appName.indexOf("Microsoft") != -1) { 
                return window[movieName] 
            } 
            else { 
                return document[movieName] 
            } 
        }
    </script>
```

3、编辑fla文件，建立一个文本框txt1和一个提交submit按钮  

```
    package {
    import flash.net.*;
    import flash.events.Event;
    import flash.events.MouseEvent;
    import flash.display.MovieClip;
    import flash.external.ExternalInterface; 
    public class test extends MovieClip {
        public function test(): void {
            submit.addEventListener(MouseEvent.CLICK, postForm);
        }
        private function postForm(evt: MouseEvent): void {
            ExternalInterface.call("hello", txt1.text); 
        }
    }
```

4、实现的效果如下：  
当你点击submit按钮时，swf文件会将txt1.text传递給hello函数，并且通过JS现实对话框“欢迎： 某某” 并且跳转到／search页面。  

5、原理解释  
fla文件中，导入了flash.external.ExternalInterface类，它是专门负责外部通信的。通过ExternalInterface.call方法，就可以调用object容器外部的函数hello。  

6、JS调用AS函数的实现方法。  
上面实现了AS调用JS并传递参数，那么反过来，JS是否可以调用AS函数呢？答案是肯定的。  

AS类这样写：  

```
    package {
        import flash.net.*;
        import flash.events.Event;
        import flash.events.MouseEvent;
        import flash.display.MovieClip;
        import flash.external.ExternalInterface;
        
        public class test extends MovieClip {
            public function test(): void {
                submit.addEventListener(MouseEvent.CLICK, postForm);
                ExternalInterface.addCallback("say", say); //regist 
            }
            
            private function say(txt: String) {
                txt2.text = txt;
            }
            
            private function postForm(evt: MouseEvent): void {
                //call js function
                ExternalInterface.call("hello", txt1.text);
            }
        }
    }
```

Html这样写：  


```html
{% raw %}
    <!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN">
    <html lang="en">
    <head>
        <title>As communicate with JS</title>
        <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.2.1/jquery.min.js"></script>
        <script>
            function hello(v){ 
                alert("hello: "+v);
                //document.location.href = '/search';
            }
            function thisMovie(movieName) { 
                if (navigator.appName.indexOf("Microsoft") != -1) { 
                    return window[movieName] 
                } 
                else { 
                    return document[movieName] 
                } 
            }
            $(document).ready(function(){
                $("#btn1").click(function(){
                    $("#test1").text("Hello world!");
                });
                $("#btn2").click(function(){
                    $("#test2").html("<b>Hello world!</b>");
                });
                $("#btn3").click(function(){
                    //$("#test3").val("Dolly Duck");
                    var txt=$("#test3").val();
                    thisMovie("test").say(txt);
                });
            });
        </script>
    </head>
    <body>
        <object type="application/x-shockwave-flash" data="{% static "flash/test.swf" %}"  name="test" width="550" height="400">
        <param name="allowScriptAccess" value="sameDomain" /> 
        <param name="movie" value="{% static "flash/test.swf" %}" />
        <embed src="{% static "flash/test.swf" %}" name="test" quality="high" allowScriptAccess="always" swLiveConnect="true" type="application/x-shockwave-flash" width="550" height="400"></embed>
        </object>
        <br>
        <p id="test1">This is a paragraph.</p>
        <p id="test2">This is another paragraph.</p>
        <p>Input field: <input type="text" id="test3" value="Mickey Mouse"></p>
        <button id="btn1">Set Text</button>
        <button id="btn2">Set HTML</button>
        <button id="btn3">Set Value</button>
    </body>
    </html>
{% endraw %}
```

7、遗留的问题：这样的写法谷歌浏览器没问题，但是火狐浏览器不成功，也就是不能把参数传到swf上。  

