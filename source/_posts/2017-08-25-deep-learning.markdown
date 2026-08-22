---
layout: post
title: "deep learning"
date: 2017-08-25 11:00
comments: true
categories: [machine learning]
tags: [deep learning, machine learning,keras,python]
---
机器学习是人工智能中非常重要的一个分支。而深度学习则是机器学习中一个重要的方向。所以人工智能、机器学习和深度学习三个概念的关系是：  
【人工智能【机器学习【深度学习】】】  

在教育领域和计算机科学领域的深度学习并不是一个概念。  

这里主要尝试利用keras和python来进行深度学习模拟。  

keras是一个深度学习模拟的良好平台，并且它完全基于python构建，具有简易性和扩展性。一个典型的keras模型如下：  
<pre><code>
from keras.models import Sequential
from keras.layers import Dense, Dropout, Activation
from keras.optimizers import SGD

# Generate dummy data
import numpy as np
x_train = np.random.random((1000, 20))
y_train = keras.utils.to_categorical(np.random.randint(10, size=(1000, 1)), num_classes=10)
x_test = np.random.random((100, 20))
y_test = keras.utils.to_categorical(np.random.randint(10, size=(100, 1)), num_classes=10)

model = Sequential()
# Dense(64) is a fully-connected layer with 64 hidden units.
# in the first layer, you must specify the expected input data shape:
# here, 20-dimensional vectors.
model.add(Dense(64, activation='relu', input_dim=20))
model.add(Dropout(0.5))
model.add(Dense(64, activation='relu'))
model.add(Dropout(0.5))
model.add(Dense(10, activation='softmax'))

sgd = SGD(lr=0.01, decay=1e-6, momentum=0.9, nesterov=True)
model.compile(loss='categorical_crossentropy',
              optimizer=sgd,
              metrics=['accuracy'])

model.fit(x_train, y_train,
          epochs=20,
          batch_size=128)
score = model.evaluate(x_test, y_test, batch_size=128)
</code></pre>

上面这个例子是一个贯序模型，它是一条道走到头的。如果是多口输出或者有分叉结构的模型，这需要用函数式模型，见[函数式模型文档](https://keras-cn.readthedocs.io/en/latest/getting_started/functional_API/)。

其他例子见：[官方文档](https://keras-cn.readthedocs.io/en/latest/getting_started/sequential_model/)

（1）数据定义  
定义训练数据和检验数据，必要的时候需要对数据进行处理，从而使的数据的形状和大小符合要求。  

（2）模型定义   
定义输入层、输出层以及中间的隐藏层，层的类别和神经元数量。  

（3）训练  
利用训练数据对模型进行fit，使得模型的参数与训练数据更好的吻合。  

（4）检验  
利用检验数据对模型及其参数进行检验，通常会依靠正确率以及gradient descent对模型进行评估和完善。  

（5）应用  
当一个模型经过训练之后能够很好的完成预测任务时，那么就可以保存模型以及相应的权重参数，在需要的时候直接调用完成任务即可。比如，讯飞的语言识别，其参数是经过大量数据的长时间训练得到的，但是我们输入语音后，后台可以及时给我们呈现文字，说明它也是调用了已有的参数，否者估计几天后才能收到讯飞发给我们的语音识别文字了。    

机器学习可以用于：分类、聚类、回归、异常识别等。  

还可以制作聊天记起，比如利用chatbot制作的聊天机器人，还具有学习新对话的能力。  
http://127.0.0.1:8000/chat/
