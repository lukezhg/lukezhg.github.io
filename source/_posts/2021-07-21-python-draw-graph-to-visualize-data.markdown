---
title: python draw graph to visualize data
date: 2021-07-21 22:06:00
tags: []
---

在线教学在疫情期间成为唯一教学选择，那么教师真实的教学体验如何？通过问卷我们收集到了一些老师的回答，量化数据分析还好说，但是对于老师们的文字反馈，确实让人头疼。

如果严格的分析，需要使用质性分析的方法，通过逐句逐句阅读和编码，形成初步的一级编码，然后对一级编辑进行概括和联系形成二级编码，最后识别主要的theme，进而对问题形成解释模型。但是，时间关系我根本来不及做这样的分析，我只想得到一个大体的结果，形成一个具有概括性的图示来揭示问题。

于是我首先对每个回答进行的标签标记，再经过3个半天的工作后，终于完成了对1000多条反馈的初步标记。最终形成18个重要的类别，不同的教师反馈的标签组合也不同。我最终获得的数据就是1000X18的一个数据表，某个标签出现标记为1，否则0。标签工作是做完了，但是我总不能把这么大的一个表展示给同行吧，于是任务的关键变成了如何将这个数据表可视化。于是我想到了python。我在做博士论文数据可视化的时候就用过，但是还是zoom quite帮我编的程序，这次又需要它救场了。

首先我查了一下python可视化的方法，很多，比较常用的法案是matplotlib+pandas+networkx，其中pandas对接数据，networkx对接网图，matplot对接制图。

可视化的关键是找到绘图思路，我的思路就是如果哪些关键词同时出现，那么这些关键词之间就存在联系，如果同时出现的频率越高，联系也就越紧，所以我想用数据绘制一个关键词网络，进而反应关键词之间的关系和主体划分。

下面我解释一下代码实现过程，下面就是完整的代码：

```
#!/usr/bin/python
# -*- coding: UTF-8 -*-
```

声明编码类型，这里选择UTF-8是为了兼容中英文。

```
# libraries
import pandas as pd
import numpy as np
import networkx as nx
import matplotlib.pyplot as plt
```

导入相应的库，python就一个优点，库多，没有找不到的，只有你想不到的，扩张了：）。

```
df = pd.read_csv('map.csv')
#print df[1]
```

使用pd阅读csv文件，确保文件与程序文件在相同目录。

```
df=df.fillna(np.random.rand()*0.1)
```

填充缺省值，数据表中很多数据缺失，这里使用了一个小于0.1的随机数进行替换。

```
print(df.loc[0,:])
```

检测一下数据是否成功获取

```
# Calculate the correlation between individuals. We have to transpose first, because the corr function calculate the pairwise correlations between columns.
corr = df.corr()

# Transform it in a links data frame (3 columns only):
links = corr.stack().reset_index()
links.columns = ['var1', 'var2', 'value']
```

计算相关系数，并把计算结果储存在links中

```
# Keep only correlation over a threshold and remove self correlation (cor(A,A)=1)
links_filtered=links.loc[ (links['value'] > 0.1) & (links['var1'] != links['var2']) ]
```

筛选相关系数大于特点临界值的关联。

```
# Build your graph
G=nx.from_pandas_edgelist(links_filtered, 'var1', 'var2')
# Plot the network:
nx.draw(G, with_labels=True, node_color='orange', node_size=400, edge_color='black', linewidths=1, font_size=10)
```

基于links_filtered，利用nx构建和绘制网图

```
plt.show()
```

如果你的图没显示出来，上面的命令就是把绘制好的图展示出来。
