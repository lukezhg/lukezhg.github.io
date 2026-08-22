---
layout: post
title: "replace disqus with youyan"
date: 2015-11-24 09:43
comments: true
categories: 
tags: [youyan,discus,share button,log]
---
将jiathis的喜欢按钮以及分享按钮放在sharing.html文件末尾。  
将友言的代码放在share_comment.html文件中（source/_includes/post/share_comment.html），并通过disqus（source/_includes/disqus.html）加载，也就是在这个文件中加入下面的代码。  
<pre><code>
<!-- JiaThis Button -->
  /{/% if site.comment_share %}
    /{/% include post/share_comment.html %}
  /{/% endif %}
</code></pre>
别忘了自觉去掉/  


当然需要在_config.yml中添加开关：  
<pre><code>
#jiathis
comment_share: true
</code></pre>


修改_layouts中post.html文件中sharing的位置，将其放在上一篇和下一篇博文导航条的后面。  


友言网的验证  
这个不需要操心，现在只要你把代码粘贴好，剩下的事情就不用管了，友言已经能自动验证了，不需要再将一个什么验证文件放到自己的source目录中了，应该是凭借ID号。  