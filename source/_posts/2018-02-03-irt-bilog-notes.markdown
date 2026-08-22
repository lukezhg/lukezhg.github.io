---
layout: post
title: "IRT BILOG equating notes"
date: 2018-02-03 15:55
comments: true
categories: [IRT,BILOG]
tags: [IRT,BILOG]
---
一、数据的格式  

DATA  
```
KEY  1111111111111111111111111111111111111111111111111111111111111111111   
NOT                                                                        
40001 1 011111011111111111011111011                                        
45137 1 011011111111011000001001100                                        
60001 2                     111111101101000111011110111                    
60002 2                     110011100000001001100110111                    
82913 3                                         111111011111000111000001111
82914 3                                         111111001110100000000101111
```

注释：  
第一列是答案。第二列是NOT。第三列开始都是数据。  

二、命令文件  
```
EXAMPL05.BLM - VERTICAL EQUATING OF TEST FORMS OVER THREE GRADE LEVELS
>COMMENT
Science test equating
>GLOBAL DFName = 'data.DAT', 
        NPArm = 2, 
        SAVe;
>SAVE PARm = 'data.PAR', 
      SCOre = 'data.SCO', 
      TSTat = 'data.TST';
>LENGTH NITems = (67);
>INPUT NTOtal = 67, 
       NIDchar = 5, 
       NGRoup = 3, 
       KFName = 'data.DAT', 
       NFName = 'data.DAT';
>ITEMS INAmes = (M01(1)M67);
>TEST1 TNAme = 'SCIT', 
       INUmber = (1(1)67);
>GROUP1 GNAme = 'GRADE 4', 
        LENgth = 27, 
        INUmbers = (1(1)27);
>GROUP2 GNAme = 'GRADE 6', 
        LENgth = 27, 
        INUmbers = (21(1)47);
>GROUP3 GNAme = 'GRADE 8', 
        LENgth = 27, 
        INUmbers = (41(1)67);
(5A1,1X,I1,1X,67A1)
>CALIB NQPt = 51, CYCles = 30, REFerence = 2, TPRior;
>SCORE IDIst = 3, RSCtype = 3, NOPrint;
```

三、输出文件  
data.PAR-->试题参数文件。  
data.SCO-->学生成绩文件。  
data.PH1-->经典测量理论参数，如原始分，正答率，相关系数等。  
data.PH2-->模型和试题参数。  
data.PH3-->rescaled 试题参数。  


案例2   

混合数据  
即有三卷共有题目，也有两卷共有题目，当然也包括一卷独有题目。  
```
40001 1 1110111111011011111111011111011                                        
40002 1 0110110111111001111111101111101                                        
60001 2 0111                    111111100110011001111110111                    
60002 2 1101                    110011101000000010100110111                    
80001 3 1001                                        110110010000001000000000000
80002 3 0101                                        111000000100001000000000110
```

BLM文件  
```
EXAMPL05.BLM - VERTICAL EQUATING OF TEST FORMS OVER THREE GRADE LEVELS

>COMMENT
Science test equating
>GLOBAL DFName = 'data.DAT', 
        NPArm = 2, 
        SAVe;
>SAVE PARm = 'data.PAR', 
      SCOre = 'data.SCO', 
      TSTat = 'data.TST';
>LENGTH NITems = (71);
>INPUT NTOtal = 71, 
       NIDchar = 5, 
       NGRoup = 3, 
       KFName = 'data.DAT', 
       NFName = 'data.DAT';
>ITEMS INAmes = (M01(1)M71);
>TEST1 TNAme = 'SCIT', 
       INUmber = (1(1)71);
>GROUP1 GNAme = 'GRADE 4', 
        LENgth = 31, 
        INUmbers = (1(1)31);
>GROUP2 GNAme = 'GRADE 6', 
        LENgth = 31, 
        INUmbers = (1(1)4,25(1)51);
>GROUP3 GNAme = 'GRADE 8', 
        LENgth = 31, 
        INUmbers = (1(1)4,45(1)71);
(5A1,1X,I1,1X,71A1)
>CALIB NQPt = 71, 
       CYCles = 30, 
       REFerence = 2, 
       TPRior;
>SCORE IDIst = 3, 
       RSCtype = 3, 
       NOPrint;
```

解释说明：  
Group2中INUmbers = (1(1)4,25(1)51);#表示一部分共有题目是1(1)4，另外一部分共有题目是25(1)51，中间用“,”间隔。  
操作技巧：  
1、BILOG输出文件可以使用双空格置换为单空格，最后将所有空格置换为分隔符，然后粘贴到EXCEL中即可。  

2、构建数据文件时，首先需要在EXCEL中构建数据结构，原始数据不要有空值，如有有空值提前用0或者9填充空值。填充空值时，先选择编辑-查找-定位，选择空值，即可选择所有空值。然后在输入值区域输入要填充的值比如0，按CTRL+Enter即可全部填充。数据按照试题关系粘贴好之后，会产生很多空白区域，可以用半角空格替换空白区域。然后将所有数据拷贝到文本编辑器中，用空值替换所有分隔符。然后把所有数据作为文本粘贴到EXCEL中添加学生编号和组别即可，再略微编辑即可。  
