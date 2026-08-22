---
layout: post
title: "Ubuntu crash on graphic driver"
date: 2013-11-08 22:14
comments: true
categories: "Ubuntu"
tags: [diver,Ubuntu,en]
---
Today I updated ubuntu, and then I can't start it any more. It show tyy1 login. In fact I met this problem several times before, I know it is caused by the graphic driver update. I have to reinstall the right driver. But I forget where is the driver file and how to setup it.  

I tried many times and finially I got it back to normal. The solving process:  
	#login with your username and password
	cd Downloads # where my dirver is
	sudo sh amd-driver-64.run
	setup it (always select the first selection and ok)
	#restart

I have copied the driver in the folder dirver. so next time I can found it more easily.  

The problem I have to solve:  
1.	How to stop the update for the graphic driver?  
2.	How to recover my ubuntu quickly?  


