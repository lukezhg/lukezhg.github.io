---
layout: post
title: "How to run JS node and appche"
date: 2017-11-27 11:50
comments: true
categories: [webdev]
tags: [node,Js,appche]
---
最近接触了不少Java script的代码，但是如何让这些代码运行起来呢？  

有两个办法最可行，一个是node，一个是开服务器appche。  

对应的可以参考这两个网页：  
node.js-->[https://nodejs.org](https://nodejs.org)  
appche-->[http://www.jianshu.com/p/d006a34a343f](http://www.jianshu.com/p/d006a34a343f)  

Node可以直接在本地运行javascript，比如读写文件。  
appche直接开服务器来实现数据的储存，可以配合mysql一起使用。  


比如Node读文件的代码(demo_readfile.js)：  

    var http = require('http');
    var fs = require('fs');
    http.createServer(function (req, res) {
      fs.readFile('demofile1.html', function(err, data) {
        res.writeHead(200, {'Content-Type': 'text/html'});
        res.write(data);
        res.end();
      });
    }).listen(8080);

再比如Node写文件的代码（demo_fs_write.js）： 

    var fs = require('fs');
    //create a file named mynewfile3.txt:
    fs.writeFile('mynewfile3.txt', 'Hello content!', function (err) {
      if (err) throw err;
      console.log('Saved!');
    });


Mac系统自带了Apache，需要设置和启动即可，具体设置可以查考上面简书的文章。  

常用端口命令：  

    httpd -v #查看apache的版本信息
    sudo apachectl start
    sudo apachectl stop
    sudo apachectl restart
    sudo apachectl -t #检测配置文件语法是否有错

