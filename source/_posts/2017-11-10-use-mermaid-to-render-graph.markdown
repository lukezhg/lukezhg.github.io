---
layout: post
title: "Use mermaid to render Graph"
date: 2017-11-10 17:48
comments: true
categories: 
tags: [mermaid]
---
Mermaid是一个可以把markdown格式代码，渲染成流程图的工具。  
git:https://github.com/knsv/mermaid/
在octopress上实现mermaid的方法参考：http://mostlyblather.com/blog/2015/05/23/mermaid-jekyll-octopress/


比如下面的代码：  

    graph TD
    A[Christmas] -->|Get money| B(Go shopping)
    B --> C{Let me think}
    C -->|One| D[Laptop]
    C -->|Two| E[iPhone]
    C -->|Three| F[Car]


渲染的结果如下：  
![mermaid graph](https://github.com/lukezhg/Freyja/raw/master/mermaid.png)

<div class="mermaid">
graph TD
A[Christmas] -->|Get money| B(Go shopping)
B --> C{Let me think}
C -->|One| D[Laptop]
C -->|Two| E[iPhone]
C -->|Three| F[Car]
</div>


<script src="/javascripts/mermaid.min.js"></script>
<script>mermaid.initialize({startOnLoad:true});</script>


sublime有一个[插件](https://packagecontrol.io/packages/Mermaid)可以在浏览器中预览效果：  
From the Command Palette: Mermaid: View In Browser

快捷键：shift+command+p

