---
layout: post
title: "Octopress的markdown语法"
date: 2014-10-05 19:37
comments: true
categories: [octopress]
tags: [log,octopress,tips,markdown]
---

###markdown语法示例
句子的尾部输入两个空格然后回车就可以断行   
句首加>进行引用，使用>>进行层级引用   
句首使用设定标题  
<code>###Title 1</code>  

插入图片代码：  
<pre><code>![Alt text](images\bird_32_gray.png)</code></pre>  

如何实现页内跳转
设定锚代码如下：  
<code><a id="1">[1]</a></code>

正文中引用[1](#1)代码：
<code>见参考文献[1](#1)</code>

More  
<code><!--more--></code>  

###Video Example  

[video](http://s3.imathis.com/video/zero-to-fancy-buttons.mp4)

###Flash example  
<object 
codebase="http://download.macromedia.com/pub/shockwave/
cabs/flash/swflash.cab#version=6,0,40,0" 
width="468" height="60" 
 id="mymoviename"> 
<param name="movie"  

value="http://www.biologymad.com/resources/kidney.swf" /> 
<param name="quality" value="high" /> 
<param name="bgcolor" value="#ffffff" /> 

<embed src="http://www.biologymad.com/resources/kidney.swf" quality="high" bgcolor="#ffffff"
width="468" height="60" 
name="mymoviename" align="" type="application/x-shockwave-flash" 
pluginspage="http://www.macromedia.com/go/getflashplayer"> 
</embed> 
</object>

