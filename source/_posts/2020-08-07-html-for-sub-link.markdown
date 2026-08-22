---
layout: post
title: "用Html实现脚注跳转"
date: 2020-08-07 15:36
comments: true
categories: [电脑技巧]
tags: [markdown]
---
很久以前就用过Markdown，但是一直没有实现脚注功能。[1](#1d)<a id="1u"></a>
中间是若干文字

中  
间  
是  
一.   
大.  
段.  
文.  
字.  



<a id="1d"></a>[1](#1u)：我的注释

代码如下： 

```
[1](#1d)<a id="1u"></a>

[1](#1u)<a id="1d"></a>：我的注释

```