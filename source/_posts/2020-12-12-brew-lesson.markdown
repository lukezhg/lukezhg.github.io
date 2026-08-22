---
title: Homebrew出错的种种折腾
date: 2020-12-12 13:07:00
tags: [octopress, rake, homebrew, rvm]
---

我用的是一台2013年的旧mac，更新Homebrew时会提示2020年1月会停止支持的那种。这也没什么，但是前几天不小心掉进坑里了，一起都起源于贪婪。

你总是想安装更多的程序，直到磁盘不够用，直到系统版本不够，直到你不会安装。

本来是想安装一个知识图谱的机器人的项目，但是这个方案很复杂，而且依赖很多程序。于是开始折腾，mac部分程序需要依赖brew安装，但是我突然发现brew无法连接到库，愿意是网络不通。

于是只能换源，但是之后无法更新，于是之后重装，但是重装报错，于是开始运行brew doctor诊断，发现有些多余文件，尝试删除，无法删除，于是强制删除，结果就悲催了。原来的很多程序都出现了问题。比如我的Octopress、mysql都除了问题。

这次事故的诱因很多，比如电脑系统旧，网络不畅，人性贪婪，对程序原理一知半解，最后从一个瑕疵演变成一个事故，甚至是要重装电脑。我真打算重装了，结果发现因为磁盘空间不足，根本没有备份可以还原。

经过这次事件，总结几个道理：

- 不要瞎折腾，特别是一知半解的时候。
- 很多安装更新失败的问题多是网络不畅的问题。
- 要保持备份的习惯，这样万一出了问题，你还可以回去。（数据备份、系统备份、环境备份）
- 要系统的学习git和docker
- 很多的折腾可以放在服务器，使用docker选择以及布置好环境的repo去布置和测试

折腾之后学的的知识，都是一些常识，比如mac软件包的安装是有顺序的，不同软件存在依赖关系，本来brew就能解决这些问题，但是DNA被污染之后，你很难连到官方的服务器，进而产生一系列问题。

参考网址：
常用 Git 命令清单 by 阮一峰：
[https://www.ruanyifeng.com/blog/2015/12/git-cheat-sheet.html](https://www.ruanyifeng.com/blog/2015/12/git-cheat-sheet.html)

RVM安装：
GitHub访问不了，是获取不到安装的脚本文件。执行下面的脚本可以进行安装。

```
/usr/bin/ruby -e "$(curl -fsSL https://gitee.com/xueweihan/codes/vfrgh7z8qcjlx1ubwt6nk71/raw\?blob_name\=brew_install.sh)"
```

Homebrew安装与卸载：
安装脚本：

```
/bin/zsh -c "$(curl -fsSL https://gitee.com/cunkai/HomebrewCN/raw/master/Homebrew.sh)"
```

卸载脚本：

```
/bin/zsh -c "$(curl -fsSL https://gitee.com/cunkai/HomebrewCN/raw/master
```
