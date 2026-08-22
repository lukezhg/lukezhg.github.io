---
layout: post
title: "fighting with the problem in my coumputer"
date: 2013-07-30 07:51
comments: true
categories: "技术技巧"
tags: [en,Display Card, ICT, troubleshooting,error,os,windows]
---
These days I am fighting with the Display Card Problem of my computer. Befor coming to Georgia, My coumputer can not start normaly, the screen is black, athough you can hear the sound of login. I try to ingnore this problem by using another OS Ubuntu in my comuputer.  BUT, unfortianaly, I can't use the PAWS wireless network of UGA in Ubuntu. So I have to solve the Display problem in WIN7 or the wireless connection problem in Ubuntu. Guess what, neither of the problem is easy to trackle.  

Finally, I solved the Display Problem using following steps:  
+   setup the two display driver software in my drivers folder("display/amd & amd2") in C disk.  
+   setup the downloaded display controler("E:\DRIVERS\chunleidownload\13-9_win7_win8_64_dd_ccc_whql.exe"), uncheck the quick stream function(20131104 I didn't do this but did it in previsous steps, then I use black but swichable mode)  
+   everything comes to normal although I still can't use swticheable display mode in BIOS  

最终的解决方案  
首先我重新安装了drivers文件包下的所有驱动，并下载和安装了一个最新的controler。 
其实这并不是问题的实质，因为电脑每次并不是不能启动，而只是会自动进入投影仪模式，按切换键后才能自动切换回来。  
但是这究竟是什么问题导致的却不清楚，我尝试了很多方法：  
1 重新安装驱动：不管用（一次我成功的用单显卡启动了一阵，但毕竟不是最佳的显示性能）  
1 重装系统：这招肯定管用，但是太累了  
1 后来有人提到说把显示器中的一个“隐藏该显示器无法显示的模式”设置勾掉就行了，结果我发现我的显示器设置中，这项是灰色，而且本来就没有勾选。  
1 再后来有个哥们在笔记本休眠到一半的时候按了启动键，结果也遇到了跟我一样的问题，而且也尝试了很多办法，后来发现这个问题跟硬盘的虚拟文件有关。我的电脑只有C盘有虚拟文件，由于我的内存有6G，我就限制了一下虚拟文件的大小，这次我把它改为系统托管。问题就解决了。  
2014年1月7日，这次着急关电脑，可能再睡眠的状态按了电源键，结果又出了同样的问题，尝试了多次，最后在虚拟内存设置选项卡中勾选“系统托管”全部硬盘，问题就解决了。

总结一下  
遇到问题 还是要自己思考所有可能相关的细节 进而列出可能的尝试解决方法。  
还要看看遇到同样问题的人是如果解决的，也可进行尝试。  

这就像做研究一样：  
最开始是很实际的需求，碰巧解决了，也不会寻根问底。  
但是反复遇到这个问题，有的时候有效，有的时候无效，这就让人想彻底解决这个问题。  
于是自己开始不断探索，不断查阅别人的探索经验，总结教训，寻找逻辑关系。  
最好终于问题解决，缘由寻到。  

解决问题的技巧：  
显示主要到是什么事件引发了问题？（休眠，连接投影仪，更新，）  
接下来问题的表现是什么？（启动时黑屏，但是可以听到windows正常启动的声音，并且可以通过显示模式变为正常）  
如何解决这个问题（不解决并加以利用，反正你自己会用就行；自己尝试；看看别人的尝试；思考前因后果并提供更可能的假设）  
总结、记录和分享。  

你看是不是跟做研究一样一样的。  

###What I learn from this:  
+   never buy a computer with two display card fire together  
+   if you have important thing just leave these problems there, important thing come frist  
+   reflect and record your problem solving process  

<add>于2014-05-10  
两三个月前，又出现了同样的问题，但是这次无论使用什么办法都不管用了。于是我就学着适应这种改变，虽然开机是黑屏的，但是我仍然能正常启动，反而增加了系统的安全性，于是我就听之任之。  

前两天，突然屏幕的图标变大了，我曾经使用过会议室的投影仪，开机的时候连着投影仪，关机的时候已经拔出了，结果回到宿舍，发现屏幕休眠后可以正常唤醒，于是重新启动定闹，结果久违的登陆页面一下子又自己出来了。</add>  

<add>17May2014  在没有插电源的情况下，电脑进入了待机状态，唤醒时黑屏，不能正常回复。强制关机后，采用最后一次正确配置，变为正常。</add>  

###windows开始菜单单击无反应  
可能是宝宝连续按电脑开关，导致的windows开始菜单无法打开：搜索了一下解决方案，第一种是建议右键系统盘选择工具，检查错误。一开始有效，后来不知怎么这招也不管用了。于是再次搜索，发现第二种解决方案：开始/运行输入regedit回车，打开注册表编辑器定位（按Windows键+R打开运行窗口） [HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Policies\Explorer] 在右侧选新建DWORD值，命名为 NoWinKeys，并双击将这个键值设为“0”按确定，在按F5刷新或重启电脑。这个管用。  