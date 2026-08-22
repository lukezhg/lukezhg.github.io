---
layout: post
title: "信息技术在生物教学中的应用"
date: 2015-07-28 07:49
comments: true
categories: [课程]
tags: 
---
###课件下载  
[信息技术课件](http://pan.baidu.com/s/1hq91Mfi)  
下载密码：rm5n  


###课程考核  
【目标】
flash制作目的在于评价flash的基本动画制作技能以及应用技能解决实际教学问题的能力。  

主要评价学员：  
    基本技能的灵活运用  
    解决实际问题的能力  
    创意   

提交内容：  
    文本文件：描述制作该动画的目的以及该动画的价值或用途，以及遇到的问题和解决办法。以及动画制作的思路和使用的关键技术。
    fla源文件和swf演示文件。

###网络资源连接  
概念图软件：Inspiration; xmind; freemind; [wisemapping](http://wisemapping.com/)   
演示文稿制作：[prezi](http://prezi.com/)  
印象笔记：evernote  
在线问卷：问卷星；调查派  
课程平台软件：moodle  
网络课程：网易公开课；爱课程；Coursera; Edx; Udacity;[novoed](https://novoed.com/)  
录屏软件：CamtasiaStudio  
社会性书签：diigo  
虚拟世界：[Omosa](http://comp.mq.edu.au/vworlds/omosa_cn.html); secondlife  


###第一部分 Flash 制作  
Adobe Flash CS3 官方简体绿色版下载:  
[http://www.flashline.cn/down/1/flash-cs3.html](http://www.flashline.cn/down/1/flash-cs3.html)  
Flash基本概念与操作  
Flash基本概念：  
1 位图和矢量图  
2 场景  
3 图层  
4 帧  
5 元件  
6 库  


Flash基本操作：  
基本操作： 文档 界面 面板 场景  
基本操作： 绘图 色彩 元件  
基本操作： 帧 图层  
视频教程：[http://www.tudou.com/programs/view/SrEik5SbYQo/](http://www.tudou.com/programs/view/SrEik5SbYQo/)  

Flash 快捷键  
Ctrl + Z 撤销  
Ctrl + B 打散  
Ctrl + G 群组  
F6 插入关键桢  
F5 插入普通桢  
F7 插入空白关键桢  
F8 转变为元件  
F9 打开动作脚本  

Flash动画类型与实例制作  
1.逐帧动画[http://www.tudou.com/programs/view/SW2JopHSvU0/](http://www.tudou.com/programs/view/SW2JopHSvU0/)  
![dog image](https://raw.github.com/lukezhg/Freyja/master/dog.png)  

蝴蝶和小船图片：链接：http://pan.baidu.com/s/1bni7WK3 密码：lon9

2.动作补间[http://www.tudou.com/programs/view/A_h3o4SxnVA/](http://www.tudou.com/programs/view/A_h3o4SxnVA/)  
3.形状补间[http://www.tudou.com/programs/view/o559fimXAqQ/](http://www.tudou.com/programs/view/o559fimXAqQ/)  
4.引导层动画[http://www.tudou.com/programs/view/L9MvoGCSZfQ/](http://www.tudou.com/programs/view/L9MvoGCSZfQ/)  
5.遮罩动画[http://www.tudou.com/programs/view/SrEik5SbYQo/](http://www.tudou.com/programs/view/SrEik5SbYQo/)  

###[第二部分 flash动作脚本简明教程](http://zhangchunlei.com/blog/2014/11/27/flash-as3-zip-manual/)  
flash实例下载：  
box 链接: [http://pan.baidu.com/s/1sj2xZMd](http://pan.baidu.com/s/1sj2xZMd) 密码: x3qd
<pre/><code/>
box.x = 100;
box.y = 150;
box.rotation = 30;
box.scaleX = 1.5;
box.scaleY = 1.5;

btnStop.addEventListener(MouseEvent.CLICK,btnStopClick);//给btn注册事件帧听器
//点击Stop按钮事件处理函数
function btnStopClick(e:MouseEvent):void{
box.stop();
}

btnPlay.addEventListener(MouseEvent.CLICK,btnPlayClick);//给btn注册事件帧听器
//点击btnPlay按钮的事件处理函数
function btnPlayClick(e:MouseEvent):void{
box.play();
}
</code></pre>

mcFace 链接: [http://pan.baidu.com/s/1dDi3IDz](http://pan.baidu.com/s/1dDi3IDz) 密码: 7yku

<pre/><code/>
mcFace.addEventListener(MouseEvent.MOUSE_DOWN,startDragFace);//添加监听
//startDragFace函数
function startDragFace(e:MouseEvent):void {
	mcFace.startDrag();
}

mcFace.addEventListener(MouseEvent.MOUSE_UP,stopDragFace);
function stopDragFace(e:MouseEvent):void {
	mcFace.stopDrag();
}
</code></pre>

练习和自测：  
1 会行走的小鸭子；  
2 小船沿着河流行驶；  
3 放大镜效果（提示：使用遮罩）；  

###第三部分 教学资源利用  
[PhET: Free online physics, chemistry, biology, earth science and math simulations](http://phet.colorado.edu/)  

[STEM Resource Finder | The Concord Consortium](http://concord.org/stem-resources)  
[Molecular Workbench - An Interface to the Molecular World](http://mw.concord.org/modeler/)  
[虚拟显微镜考核](http://www.udel.edu/biology/ketcham/microscope/scope.html)  

