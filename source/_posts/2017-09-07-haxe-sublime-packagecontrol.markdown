---
layout: post
title: "Haxe Sublime PackageControl"
date: 2017-09-07 09:50
comments: true
categories: [编程]
tags: [sublime,haxe,openfl]
---
Flash已经慢慢被H5取代，但是最近缺还是用flash编制了一个小游戏，一个太空穿越游戏。  

因此，想尝试将其转化为H5，最直接的方法就是手动改，这种方法最有效直接，也最靠谱。  

但是本着懒人的精神，google了其他的方法，方法有很多种，比如swiffy就是一种能将swf转化成h5的应用，而且特别是对于只有动画的flash和as2.0特别好用。但是对于我用AS3写的游戏，不靠谱。  

于是又找到了一种方法，就是用haxe这种跨语言的程序语言，它继承了很多AS的特性，因此很容易改写代码，然后也很容发布称为H5，不过还是绕不开人工改写。其实有一个AS3HX的插件可以自动转化代码，我是一了一下，出现错误。也就放弃了。  

但是，我却对Haxe产生了兴趣，并且安装了haxe和openfl，还找了一个[现成的代码](http://haxecoder.com/post.php?id=14)玩了一下，还是挺容易上手的。  

大体过程bash如下：   
<pre><code>
openfl create project ProjectName #新建项目
cd ProjectName #进入项目目录
sublime Source/Main.hx #修改代码
openfl test html5 #测试，或者 openfl test neko 或者 openfl test flash
</code>></pre>>

这个例子打开了Haxe的窗口，用这种程序代码就不担心发布的产品因为受到语言软件限制而必须改写，因为直接换一种形式发布就ok了。  

下面是展示一张图片的代码，来自：[openfl官网](http://www.openfl.org/learn/tutorials/displaying-a-bitmap/)  
<pre><code>
package;

import openfl.display.Bitmap;
import openfl.display.Sprite;
import openfl.Assets;

class Main extends Sprite {

    public function new () {

        super ();

        var bitmapData = Assets.getBitmapData ("assets/openfl.png");
        var bitmap = new Bitmap (bitmapData);
        addChild (bitmap);

        bitmap.x = (stage.stageWidth - bitmap.width) / 2;
        bitmap.y = (stage.stageHeight - bitmap.height) / 2;

    }


</code></pre>

要注意的是，展示的图片，放在assets文件夹中，然后直接调用即可。  

下面是一个推球游戏代码：  
http://haxecoder.com/post.php?id=14
我们需要修改项目目录下的application.xml文件，来修改窗口大小和背景等属性。  
下面的两行代码就是设定窗口大小为 500x500，背景色为#333333:  

<pre><code>
<window background="#333333" fps="60" />
<window width="500" height="500" unless="mobile" />
</code></pre>


在测试这些代码的时候，我发现在sublime、终端、文件夹之间切换效率特别低，于是专门搜索了一下sublime的用法，其实sublime有很多插件可用，比如sidebar enhancement，haxe，markdown，terminal等，只需要从preference-package control进去，然后install相应的插件即可。这里大有文章可做。  

为了提高文件夹切换的效率，可以通过添加文件夹到项目的办法，这样sublime侧边栏就可以直接切换多个文件。  

为了让自发布博客更有效，我还在自己的~/.bash_profile中添加了alias语句，它的格式是：  
alias [别名]='[指令名称]')  

目的是在终端输入 rake的时候，系统会自动解读为 bundle exec rake。  
<pre><code>
alias rake='bundle exec rake'
</code></pre>

通过这么一番折腾，mac的使用效率提升了不少。  

昨夜西风凋碧树
独上高楼，望断天涯路



