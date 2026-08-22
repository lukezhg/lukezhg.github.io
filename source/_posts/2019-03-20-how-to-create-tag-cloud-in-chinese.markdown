---
layout: post
title: "如何制作中文标签云"
date: 2019-03-20 10:46
comments: true
categories: 
tags: 
---
###第一步：分词

与英文不同，为了制作标签云，中文必须分词，也就是从语料中提取词语，并统计词频。  
可以使用的工具：  
中文词频统计工具：[http://translation.education/topwords/](http://translation.education/topwords/)

语料库在线：[http://corpus.zhonghuayuwen.org/CpsTongji.aspx](http://corpus.zhonghuayuwen.org/CpsTongji.aspx)

通过这两个工具，就可以把一段文字的词频统计出来，接下来就是要图形化，形成一个合适的标签云了，这个时候我们要借助标签云可视化工具。  

###第二部：可视化

可视化，就是根据词频来设置词语的字体大小，从而在二维平面上形象的展示出预料中的词语的出现情况。  
可以使用的工具：  
wordart：[https://wordart.com/create](https://wordart.com/create)
这是一个英文词频可视化工具，可以制作很多高质量的标签云。它对英文支持的比较好，但是其实也可以支持中文，前提是上传和使用你自己的中文字体。  
比如微软雅黑字体下载：http://www.font5.com.cn/zitixiazai/1/36.html

操作步骤：  
首先，把中文词频工具获得的词频信息复制到剪切板。然后在wordart这个地方点击Create，点击words，Import，粘贴你的词频表格，记住要勾选CSV format。  

然后，在FONTS这个地方上传你的字体，选择你自己的字体，点击Visualize就可以实现中文词频的可视化了。  

比如我生成的标签云：  
![New teacher challenges](https://raw.github.com/lukezhg/Freyja/master/New-teacher-challenges.png)