---
layout: post
title: "Clustering Maps by Similarity"
date: 2014-06-30 19:17
comments: true
categories: "统计"
tags: [network analysis,R,en]
---
I wonder how to divide people into clusters by the similarity of their concept maps. I googled but found no good answers. If you know, please tell me by leaving a comment.  

Although there was no direct solutions for me, but I did find something. I can use UCINET to do cluster analysis -- the problem is I must provide a similarity/dissimilarity matrix for this software.  

There are at least two ways to create the matrix. First, use Pearson correlations. I can easily get the table by SPSS. Second, I have to figure out a way to count the similarity or dissimilarity myself. Well, it is not too hard, if I just consider the different links and the same links, and give values to different situations, such as 11, 00, 10, 01, then I can count the dissimilarity. I can use R to count the matrix and then use [Multidimensional Scaling in R](http://zhangchunlei.com/blog/2014/05/29/mds-in-r/) to plot out the people. In this way, I can have a look whether clusters exist obviously. Then I can use UCINET to do the rest job.  

I have to consider both the links and the notes at the same time, otherwise I can not make full use of the information in the data. In other words, I need to compare the stuctures rather than the dots. If two people have linked similar structures, they should score higher than two people have the same number of similar links but not connected. I use the following abbreviation:  
    bh(both have)
    bl(both lack)
    hl(one have one lack)
    lh(one lack one have)
    ss(similarity score)

    ss=bh*2+bl-hl-lh-breaks(可以参考序列比对)


References:  
[Equivalence: Measures of similarity and structural equivalence](http://faculty.ucr.edu/~hanneman/nettext/C13_%20Structural_Equivalence.html)  