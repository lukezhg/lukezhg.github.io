---
title: pyenv and virtualenv
date: 2021-07-24 11:17:00
tags: [python, virtualenv, pyenv]
---

pyenv是一个python环境版本管理器，当你有甚多项目，但是用的python版本不同时，为了让程序运行，你需要设定特点的py版本。这时pyenv就能发挥作用了。pyenv也能让你装多个py版本。

```
# 查看当前版本
pyenv version
# 查看所有版本
pyenv versions
# 查看所有可安装的版本
pyenv install --list
# 安装指定版本
pyenv install 3.6.5
# 安装新版本后rehash一下
pyenv rehash
# 删除指定版本
pyenv uninstall 3.5.2
# 指定全局版本
pyenv global 3.6.5
# 指定多个全局版本, 3版本优先
pyenv global 3.6.5 2.7.14
# 实际上当你切换版本后, 相应的pip和包仓库都是会自动切换过去的
```

virtualenv是一个虚拟环境管理器，当你的呈现需要不同的程序包版本支持的时候，而且它们往往还是相互排斥的，那么你就可以用它来解决，首先你创建一个虚拟环境，然后在这个环境下安装所需要的包，这样就可以运行相应的呈现了，前提是你需要先进入并激活对应的虚拟环境。

参考：[这里](https://zhuanlan.zhihu.com/p/137624513)

创建并进入虚拟环境

```
cd code/python_envs
# 方式1:
mkvirtualenv envname01  # 创建完毕会自动进入该虚拟环境
# 方式2:
virtualenv envname02
workon envname02  # 进入该虚拟环境
# 方式3:
virtualenv envname03
cd envname03
source bin/activate  # 激活并进入虚拟环境
```

配置环境

```
pip3 install flask
pip3 install django
pip3 install Scipy
```

退出环境

```
deactivate
```

基于某Python环境创建虚拟环境：

```
mkvirtualenv -p python2.7 envname01
mkvirtualenv -p python3.6 envname02
```

常用命令：

```
mkvirtualenv envname02 #创建并进入虚拟环境
mkvirtualenv -p python3.6 envname02 #基于某Python3.6环境创建虚拟环境
workon #列出虚拟环境：
deactivate #退出虚拟环境
workon envname02  # 切换虚拟环境2
pip3 install 模块名 #为虚拟环境安装模块
pip3 uninstall 模块名 #为虚拟环境卸载模块
lssitepackages  |  pip list  |  pip3 list #查看虚拟环境里安装了哪些包
cpvirtualenv env1 env2  # 复制环境 前面的是原文件 后面的拷贝后的新文件
rmvirtualenv env2  #删除虚拟环境
```

用pyenv安装python3.6.14遇到的坑

最近升级了Big Sur mac系统，但是用pyenv安装python3.6.14失活不成功，运行：

```
CFLAGS="-I$(brew --prefix openssl)/include -I$(brew --prefix bzip2)/include -I$(brew --prefix readline)/include -I$(xcrun --show-sdk-path)/usr/include" LDFLAGS="-L$(brew --prefix openssl)/lib -L$(brew --prefix readline)/lib -L$(brew --prefix zlib)/lib -L$(brew --prefix bzip2)/lib" pyenv install --patch 3.6.14 < <(curl -sSL https://github.com/python/cpython/commit/8ea6353.patch\?full_index\=1)
```

提示如下：

```
-c ./Modules/pwdmodule.c -o Modules/pwdmodule.o
./Modules/posixmodule.c:8210:15: error: implicit declaration of function 'sendfile' is invalid in C99 [-Werror,-Wimplicit-function-declaration]
        ret = sendfile(in, out, offset, &sbytes, &sf, flags);
              ^
./Modules/posixmodule.c:10432:5: warning: code will never be executed [-Wunreachable-code]
    Py_FatalError("abort() called from Python code didn't abort!");
    ^~~~~~~~~~~~~
1 warning and 1 error generated.
make: *** [Modules/posixmodule.o] Error 1
make: *** Waiting for unfinished jobs....
```

后来，参考了[这篇](https://www.cnblogs.com/weiweivip666/p/14396020.html)，运行了下面的代码：（功能是在bash_profile里添加环境判断）：

```
echo -e 'if command -v pyenv 1>/dev/null 2>&1; then\n  eval "$(pyenv init -)"\nfi' >> ~/.bash_profile #添加环境判断
source ~/.bash_profile #更新配置文件
```

最终才成功安装，这个坑很深。
