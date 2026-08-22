---
layout: post
title: "Hierarchical Linear Models"
date: 2020-06-26 07:43
comments: true
categories: 
tags: 
---
分层线性模型HLM  

以下是百度百科的解释摘录：  
    在社会科学研究中，调查得来的数据往往具有层次结构（嵌套结构）的特点。在教育学与心理学的研究中这种情况尤为常见，如关于学业成绩影响因素的研究中，我们可以考虑的预测变量有学生的入学成绩、学生性别、学生的社会经济地位、班级人数、班主任和任课教师、教室环境等，这些变量中有的是学生个体层面的变量，有的是班级层面的变量。这样的数据具有两个水平，第一水平是学生，第二水平是班级，学生嵌套于到级之中，称之为分层数据。  

    传统的线性回归模型假设变量间存在直线关系，变量总体上服从正态分布，方差齐性，个体间随机误差相互独立。前两个假设较易保证，但方差齐性，尤其是个体间随机误差相互独立的假设却很难满足。即不同班级的学生可以假设相互独立，但是同一班级的学生由于受相同班级变量的影响，很难保证相互独立。  

    因此在分析具有层次结构特点的数据时，应将传统回归分析中的误差分解为两部分，一部分是第一水平个体间差异带来的误差，另一部分是第二水平班级的差异带来的误差。可以假设第一水平个体间的测量误差相互独立，第二水平班级带来的误差在不同班级之间相互独立。  

所以层次分析主要适合层次结构数据，比如我要研究教师的教学体验，我会关注教师的个体因素、学校因素两个层次，也就是不同教师体验不同，不同学校教师教学体验也不同。  

一个很好的例子，是看这篇文章：Is inquiry possible in light of accountability?: A quantitative comparison of the relative effectiveness of guided inquiry and verification laboratory instruction  

在这片文章中，研究者想检验探究教学法的有效性，因变量是学生成绩，自变量包括3层，第一是成绩测评的时间，第二是学生个体情况比如性别、年龄等，第三层是研究者关心的探究还是传统教学法，教师能力水平，教师ROTP问卷得分，学生免费午餐情况等，主要为了研究不同教法、教师层次、教师教学倾向、学生背景对成绩的交互性影响。下面是这篇文章的方法部分：  

    Pretest, posttest, and delayed posttest scores were analyzed through a multilevel growth
    curve analysis (HMLM2)procedure throughHLM6.08 software (e.g., Raudenbush&Bryk, 2002). In this analysis, change within studentwasmodeled at Level 1, student characteristics were modeled at Level 2, and teacher/school characteristics were modeled as Level 3. At Level 1, we modeled time (test = 1, 2, or 3 or pretest, posttest, and delayed posttest, respectively) as well as the squared time term to allow for curvilinear effect modeling. All effects were centered at this level, meaning that intercepts are predicting average student scores at posttest (time 2). At Level 2, no variables were modeled because no student-level variables were included in the research. At Level 3, variables such as instructional method, level of the school (middle vs. high school), percentage of the school receiving free and reduced lunch, and teacher RTOP score, as well as their respective two- and three-way interactions, were modeled to predict not only average student scores but also growth and change in scores over test administrations. To answer our research question, three sets of analyses were performed:
    A. An initial analysis of student scores as a function of instructional method (method), level of school (middle vs. high school; level), and the interaction of method and level.
    B. An analysis of student scores as a function of teacher RTOP score, method, level, the two-way interactions RTOP × level, RTOP × method, and method × level, and the three-way interaction RTOP × level × method.
    C. An analysis of student scores as a function of school poverty (as operationalized by percentage of free and reduced lunch (FRL); method, level, the two-way interactions FRL × level, FRL × method, and method × level, and the three-way interaction FRL × level × method.

这个软件，这个步骤，这个方法，这个视角，相互匹配才是值得借鉴的。  

使用这种方法的步骤：  
1、明确要研究的问题和倾向性，比如这篇文章就是要研究排除其他因素的影响，到底科学探究是否有效，从学生学习成绩的角度  

2、区分自变量的层次，明确先后关系，比如这篇文章是把关心的影响因素最后放进去，那是不是意味着我也要把最关心的变量放在最后一层

3、使用的软件，spss可以做线性回归，但是不如HLM专业，似乎中心化处理这一步也没有，这个可以查一查。  