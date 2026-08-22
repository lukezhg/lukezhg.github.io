---
layout: post
title: "人脸定位和识别"
date: 2015-11-26 10:03
comments: true
categories: [code]
tags: [code,python.sklearn,opencv,face detection,face recognition]
---
现在很多智能手机或者照相机都有人脸检测的功能了。不仅如此，现在的人工智能还能对照片进行比对看两个照片是不是同一个人，或者基于一个样本库，直接识别照片中人的姓名，正确率一般能达到80%以上。  

###人脸定位  
功能：在一张照片中定位所有人脸的位置。  

实现：使用python sklearn和openCV进行人脸检测和定位。  

找到代码：face-boxer.py  
[https://gist.github.com/dannguyen/cfa2fb49b28c82a1068f#file-face-boxer-py](https://gist.github.com/dannguyen/cfa2fb49b28c82a1068f#file-face-boxer-py)  

使用时出现问题：  

**问题1**  
由于我在ubuntu上安装的是最新版本的openCV3.0.0，有些语句更改了，造成原始代码错误：  
<code>
"face_detect.py", line 21, in flags = cv2.cv.CV_HAAR_SCALE_IMAGE AttributeError: 'module' object has no attribute 'cv'
</code>

问题解决的办法：  

具体方法如下：  
   the cv2.cv submodule got removed in opencv3.0, also some constants were changed.  
   please use cv2.CASCADE_SCALE_IMAGE instead  
   (do a help(cv2) to see the updated constants)  
参见[opencv 3.0.0-dev python bindings not working properly - Stack Overflow](http://stackoverflow.com/questions/30013009/opencv-3-0-0-dev-python-bindings-not-working-properly)  

**实际上只需要将原来的cv2.cv.CV_HAAR_SCALE_IMAGE替换为cv2.CASCADE_SCALE_IMAGE**  

**问题2**  
之后又发现程序不报错，但是不能产生人脸识别好的图片  

处理：  
修改产生图片文件名的那一句，去掉/temp/等内容，之后就可以正常产生人脸检测的图片了。  

总结：下次遇到问题，特别是程序运行出错，去http://stackoverflow.com找答案会比较便捷。  

实际上我在安装openCV的时候也遇到了麻烦，最后参照下面教程安装成功：  
Installing OpenCV 3.0.0 on Ubuntu 14.04 » Rodrigo Berriel  
[http://rodrigoberriel.com/2014/10/installing-opencv-3-0-0-on-ubuntu-14-04/](http://rodrigoberriel.com/2014/10/installing-opencv-3-0-0-on-ubuntu-14-04/)  

这个教程提供了自动安装的脚本，但是我还是手动安装的。  

###人脸识别  

Python的好处就是可以用二三十行的语句就能完成几乎所有任务  

学习资源：  
[5.5.4. The Labeled Faces in the Wild face recognition dataset — scikit-learn 0.17 documentation](http://scikit-learn.org/stable/datasets/labeled_faces.html)  
这个资源介绍了LFW数据库和其用法，lfw是一个从互联网上获得的名人人脸数据库。  

Faces recognition example using eigenfaces and SVMs — scikit-learn 0.17 documentation
[http://scikit-learn.org/stable/auto_examples/applications/face_recognition.html](http://scikit-learn.org/stable/auto_examples/applications/face_recognition.html)

<b>我跑的代码也是上面这个，文件名face_recognition.py</b> 

对这个代码详细解释的教程见这里：  
Machine learning for facial recognition | EFavDB  
[http://efavdb.com/machine-learning-for-facial-recognition-3/](http://efavdb.com/machine-learning-for-facial-recognition-3/)  

###进一步学习  

下面是一个叫Frolian的程序员博客，介绍了如何通过类似的方法在摄像头中识别笑脸。有空可以好好研究一下。  

Smile Recognition Using OpenCV and scikit-learn  
[http://flothesof.github.io/smile-recognition.html](http://flothesof.github.io/smile-recognition.html)  


关于机器学习的另一个比较经典的学习资源：  
2.11. scikit-learn: machine learning in Python — Scipy lecture notes  
[http://www.scipy-lectures.org/advanced/scikit-learn/index.html](http://www.scipy-lectures.org/advanced/scikit-learn/index.html)  