---
layout: post
title: "如何使用Wingen和BILOG"
date: 2014-02-18 14:39
comments: true
categories: "IRT"
tags: [IRT]
---
如何使用Wingen，下图是用2PLM模型产生客观题的参数。大体上3个步骤：  
第一步：产生答题者  
第二步：产生题目  
第三部：产生答题者对题目的作答结果  
你只负责设置参数就可以，其他的程序帮你完成，设置第一步和第二部参数的时候，可以查看图形效果，进而作进一步的调整。  
![wingen](https://raw.github.com/lukezhg/Freyja/master/wingen.png)  

接下来可以利用BILOG对你的数据进行模型设定和估算  
实际上BILOG可以直接使用你用wingen产生的数据，因为都是纯文本，只是你需要建立自己的BLM文件，也并不困难，下图就是在例子的基础上修盖的BLM文件。只是要注意答题者数、题目数要与数据一致，此外文件中有一句要注意 （1A1,9x,30A1），这句表示的是数据的格式，意思是第一列为标号，后面有9列空行，再后面有30列的数据（也就是每个答题者对30到题目的作答情况），这个格式一定要与数据相互吻合。  
![bilog](https://raw.github.com/lukezhg/Freyja/master/bilog.png)