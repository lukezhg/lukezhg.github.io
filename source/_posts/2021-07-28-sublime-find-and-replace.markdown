---
title: sublime find and replace
date: 2021-07-28 21:39:02
tags: [sublime]
---

### [](#sublime-支持正则表达式 "sublime 支持正则表达式")sublime 支持正则表达式

```
#(#{1,})    #可以匹配##，###，####，#####等
```

更多可以参考廖雪峰的博客：[https://www.liaoxuefeng.com/wiki/1252599548343744/1304066080636961](https://www.liaoxuefeng.com/wiki/1252599548343744/1304066080636961)

### [](#sublime-支持多文件搜索和替换 "sublime 支持多文件搜索和替换")sublime 支持多文件搜索和替换

也就是你可以打开一个文件夹，然搜索该文件夹的所有文件中，是否有指定字符

### [](#sublime-支持在replace中使用捕获的字符 "sublime 支持在replace中使用捕获的字符")sublime 支持在replace中使用捕获的字符

find:

```
my name is (\w+)
```

replace:

```
my name used to be $1
```

在比如，我想把博文中所以##，###，####后面都加上一个空格

find:

```
"#(#{1,})"
```

replace:

```
"#$1 "
```

为了让大家看到那个空格，我都加了””，实际使用时去除””。
