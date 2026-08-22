---
layout: post
title: "Repeated Measures Correlation Mixed Model"
date: 2014-04-17 09:02
comments: true
categories: "统计"
tags: [SPSS,repeated measures,missing,en]
---
How to do it?  
Analysis==>Mixed Model, then you got diaogue 1 as follows. ID shuold be put be included as subjects. Year should be included as repeated, cause I measured multiple times by different year. 
![Mixed Model Dialouge 1](https://raw.github.com/lukezhg/Freyja/master/mixed-model-d1.png)  
The most hard decision to make is which Repeated Covaricance Type to select, there are a lot of choices, the most used ones are:  
1. Unstructured: you have no idea of the correlation of repeated measures, SPSS we estimate all the correlation independantly (r12,r13,r23,r14,r24,r34).  
2. Scaled Identity: no correlations at all, r=0.  
3. Compound Symmetry: all correlations equals r.  
4. AR1: (r, r^2, R^3)  
![Auto Regression 1](https://raw.github.com/lukezhg/Freyja/master/mixed-model-AR1.png)  
5. Toeplitz:(a,a,a,b,b,c)  
![Toeplitz](https://raw.github.com/lukezhg/Freyja/master/mixed-model-toepliztz.png)  
6. Another choice is "diagonal" which assumes no correlation between the random effects.  

Then you determing the fixed effect variable:  
![Mixed Model Dialouge 2](https://raw.github.com/lukezhg/Freyja/master/mixed-model-d2.png)  

And the random effect variable:  
![Mixed Model Dialouge 3](https://raw.github.com/lukezhg/Freyja/master/mixed-model-d3.png)  