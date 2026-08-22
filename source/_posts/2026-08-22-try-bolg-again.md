---
title: 博客系统重新启动
date: 2026-08-22 14:52:28
tags: [blog; 技术;hexo]
---
尝试重新开始记录生活和写博客。


## 最简完整一套（每次更新博客就依次敲这三组）
1 本地预览测试
hexo clean && hexo s

2 备份源码（新开终端，或者Ctrl+C关掉预览后执行）
git add .
git commit -m "更新描述"
git push

3 发布线上网站
hexo clean && hexo g && hexo d


## 以后换电脑恢复博客（备用，记下来）
git clone -b source git@github.com:lukezhg/lukezhg.github.com.git myblog
cd myblog
npm install
hexo s



## 重要注意事项

1. **永远不要手动切换本地 master 分支**，master 交给`hexo d`内部`.deploy_git`处理。本地只操作`source`分支。
2. 只做本地修改，没有上传 github：只执行 `hexo s`，不要执行 git push 和 hexo d。
3. `.gitignore`不要改动，避免上传`node_modules`、`public`。
4. **git push = 备份源代码；hexo d = 发布网页**，两件事分开，不要混淆。