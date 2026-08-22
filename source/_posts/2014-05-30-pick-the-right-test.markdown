---
layout: post
title: "Pick the right test"
date: 2014-05-30 14:14
comments: true
categories: "统计"
tags: [SPSS,variables,analysis,en]
---
You have to pick a test to analysis your data. The question is which test is the right one. Well, it depends on your data and your hypothesis. Usually there are lot of choices, but only one solves your problem best.  

Here are some suggestions for selecting test by the types of your variables.  
Dependent and Independent Variables  
Dependent Variable(DV) is what you are care of. Independent Variable(IV) is what you think may affect your dependent variable. Usually you can control your independent variable, but not depedent variable.  

There are two basic types of variables:  
Continuous Variables(e.g. height,temprature)  
Discrete Variables(e.g. age, size, preferences)  

if IV=[0,1],DV=[~] then T test  
if IV=[0,1,2,],DV=[~] then one-way Anova or ANOCVA  
if IV1=[0,1,2,], IV2=[0,1,2,], DV=[~] then General linear model  
if IV1=[~], IV2[~],..., DV=[~], then Linear Regression & Pearson  
if IV=[0,1,...], DV=[0,1,...] then χ2  
if IV=[~], DV=[0,1,...] then Logistic regression

For more details look at the following pictures:  
![Choices of Test](https://raw.github.com/lukezhg/Freyja/master/choiceoftest.png)  
This picture comes from : [SOCR: Statistics Online Computational Resource](http://www.socr.ucla.edu/Applets.dir/ChoiceOfTest.html)  

References:  
[Types of Variables](http://www.unesco.org/webworld/idams/advguide/Chapt1_3.htm)  
[SOCR: Choice of Test](http://www.socr.ucla.edu/Applets.dir/ChoiceOfTest.html)  