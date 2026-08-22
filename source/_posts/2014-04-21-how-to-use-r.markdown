---
layout: post
title: "R语言学习笔记"
date: 2014-04-21 23:35
comments: true
categories: "统计"
tags: [R,code]
---
<pre><code>
##week1
getwd() #获取当前工作目录
setwd(dir) #设定当前工作目录 也可以直接通过菜单界面设定
source("myfunction.R") #加入源之后才可以使用这个函数

##week2
#list
> a <- 1:10
> b <- c(1,3,4,5,8,9,11,14,15,18)
> b <- b[-2] #去除第二个元素
> c(1,2)*c(2,3)
[1] 2 6

> m <- c(1,2,3)
> mynames <- c("1-2","2-3","4-5")
> mytable <- setNames(m,mynames)#之后可以通过name来调用元素值
1-2 2-3 4-5 
  1   2   3 

> union(x, y) #并集
> intersect(x, y) #交集
> setdiff(x, y) #前者有后者没有的
> setequal(x, y) #元素是否全部相同
> is.element(el, set)
> unlist() #将层级list变为单层
> unique(x) # 获取非重复元素

# logical operation
x <- FALSE
y <- TRUE
! x
x & y
x && y
x | y
x || y
xor(x, y)

isTRUE(x)
cbind(a,b) #
rbind(a,b) #
length(a) #
class(a)
as.character()
as.logical()
as.numeric()
m <- matrix(a,nrow=2,ncol=5)
dim(m) #[1] 2 5
attributes(m) $dim [1] 2 5
m <- 1:10
dim(m) < c(2,5) #
f <- factor("yes","no","yes","yes")
table(f) # yes 3 no 1
x <- c()
x <- c(x,1)
mean() #求平均值
cor(a,b) #求相关系数
is.na()
is.nan()

## file 文件
read.table() #读取txt表格
read.csv() #读取csv文件
# 写文件略过row name
write.csv(data, "data.csv", row.names=FALSE)
# 同样写文件，当用空白替换"NA"
write.csv(data, "data.csv", row.names=FALSE, na="")
# 使用tabs略过row col name
write.table(data, "data.csv", sep="\t", row.names=FALSE, col.names=FALSE) 
参考[Cookbook for R » Writing data to a file](http://www.cookbook-r.com/Data_input_and_output/Writing_data_to_a_file/)
write.table(sim, "pcksim.csv", row.names=na,col.names=c("",na),sep = ",") # 可以写列名称

names()
x[!is.na(x)] # 去除缺失的数据
data <- data.frame(id=1:10,height=170:180)
data["id"] #返回局部data.frame
data["id"][!is.na(data["height"])] #返回height无缺失的id
data[[id]] #返回vector
paste("00","1",".csv",sep="") # 001.csv
paste(a,collapse="") # 将一个list连成一个长字符

for (i in 1:length(id)){
    s <- as.character(id[i])
    spre <- paste(rep("0",3-nchar(s)),collapse="") # use collapse join vector
    fn <- paste(directory,"/",spre,s,".csv",sep="") # use sep to join string
    data <- read.csv(fn)
}

if(length(x)>0){print(x)}else{}

##Week3
x <- list(a=1:5,b=rnorm(10))
lapply(x,mean)#$a[1] 3  $b[1] 0.03937816
如果x不是一个list,那么它将被自动转换成list,相当于使用as.list()函数
x <- list(a=matrix(1:4,2,2),b=matrix(1:6,3,2))
lapply(x,function(elt)elt[,1]) #$a[1] 1 2  $b[1] 1 2 3
lapply(x,function(elt) strsplit(elt,"-")) #对每个元素使用“-”进行拆分
sapply(x,mean) #会自动简化结果，返回一个vector或者matrix，不能简化返回list
x <- matrix(rnorm(200),20,10)
apply(x,2,mean) #返回10列的均值
apply(x,1,sum) #返回每行的总和共20个
a <- array(rnorm(2*2*10),c(2,2,10)) #三维数组
apply(a,c(1,2),mean)
          [,1]      [,2]
[1,] 0.1888774 0.5517366
[2,] 0.2667046 0.2412767

str() #Compactly Display the Structure of an Arbitrary R Object
str(tapply)
> x <- c(rnorm(10),runif(10),rnorm(10,1))
> f <-gl(3,10) #生成标签 1 1 1 1 1 1 1 1 1 1 2 2 2 2 2 2 2 2 2 2 3 3 3 3 3 3 3 3 3 3
> tapply(x,f,mean) #具有相同标签的数值的平均值
with(mtcars, tapply(mpg, cyl, mean))# mtcars is a data.frame with cyl and mpg

> split(x,f) #利用标签将list进行拆分
> s <- split(airdata, airdata$Month)
> lapply(s,function(x) colMeans(x[,c("Ozone","Solar.R","Wind")]))
split(x,list(f1,f2),drop=TRUE) # empty levels can be dropped

## 字符串 string
> as.character()
> strsplit("1-2,3-4,5-6",",") #对字符串进行拆分
> strsplit("1-2,3-4,5-6",",")[[1]][1] #返回 "1-2"
> paste(rev(strsplit("abc", split = "")[[1]]), collapse = "") #反转字符串
> grep("bcd", "abcd") # return 1 # 
> regexpr("bcd","aabcd")
[1] 3
attr(,"match.length")
[1] 3
attr(,"useBytes")
[1] TRUE

> gregexpr("1","1-2,2-3,1-5") #返回所有匹配位置 也能利用length获取匹配数目
> length(gregexpr("1","1-2,2-3,1-5,1-9,1-8")[[1]]) #返回4


> mapply(rep,1:4,4:1)
[[1]]
[1] 1 1 1 1

[[2]]
[1] 2 2 2

[[3]]
[1] 3 3

[[4]]
[1] 4

## debug
traceback() # print out where error occurs,else do nothing
debug() # step through one line at a time
browser() #suspend the execution wherever called and put it in debug mode
trace() # insert debug code in specific place

#Play with the iris data
library(datasets)
data(iris)

#Play with $
> x <- makeCacheMatrix()
> x
$set
function (y) 
{
    x <<- y
    inv <<- NULL
}

$get
function () 
x

$setinverse
function (inverse) 
inv <<- inverse

$getinverse
function () 
inv

> x$set(matrix(rnorm(9),3,3))
> x$get()

> x$set(a)
> x$get()
            [,1]      [,2]       [,3]
[1,] -0.50184759 -0.751659 -2.1276852
[2,]  0.37466264 -1.448643  1.1807655
[3,] -0.06093845  0.740338 -0.8508723
> cacheSolve(x)
           [,1]       [,2]       [,3]
[1,] -0.4668678  2.8847043  5.1705844
[2,] -0.3214999 -0.3872940  0.2664879
[3,] -0.2462983 -0.5435808 -1.3137063

#week4
#统计
str(str)# see the structure of a object
m <- matrix(rnorm(100),10,10)
str(m)
str(lm)
str(ls)
x <- rnorm(100,2,4)
summary(x) #摘要
table(x) #返回频数表
str(x)

#作图
hist(rnorm(1000,2,4))
hist(BMI, breaks=20, main="Breaks=20")
hist(BMI, breaks=seq(17,32,by=3), main="Breaks is vector of breakpoints")
seq(0, 1, length.out = 10) #在一定范围产生制定数目的序列
plot(x,y)

#拟合
> set.seed(20)  #进而可以再次产生同样的随机数 方便别人重复模拟
> x <- rnorm(100)
> e <-rnorm(100,0,2)
> y <- 0.5+2*x+e
> sumary(y)

#评估运算时间 user time（cpu 时间消耗）elipsed time(流逝壁钟时间)
> system.time(readLines("http://www.jhsph.edu"))

#就
make.Negloglik <- function(data, fixed=c(FALSE,FALSE)){
    params<- fixed
    function(p){
        params[!fixed] <- p
        mu <- params[1]
        sigma <- params[2]
        a <- -0.5*length(data)*log(2*pi*sigma^2)
        b <- -0.5*sum((data-mu)^2)/(sigma^2)
        -(a+b)
    }
}
set.seed(1)
normals <- rnorm(100,1,2)
nLL <- make.Negloglik(normals)
optim(c(mu=0,sigma=1),nLL)$par

> # Fixing sigma=2
> nLL <- make.Negloglik(normals,c(FALSE,2))
> optimize(nLL,c(-1,3))$minimum
[1] 1.217775
> optimize(nLL,c(-1,2))$minimum
[1] 1.217775
> #Fixing u=1
> nLL <- make.Negloglik(normals,c(1,FALSE))
> optimize(nLL,c(1e-6,10))$minimum
[1] 1.800596
> nLL <- make.Negloglik(normals,c(1,FALSE))
> x <- seq(1.7,1.9,len=100)
> y <- sapply(x,nLL)
> plot (x,exp(-(y-min(y))),type="l")
> nLL <- make.Negloglik(normals,c(FALSE,2))
> x <- seq(0.5,1.5,len=100)
> y <-sapply(x,nLL)
> plot(x,exp(-(y-min(y))),type="l")


Assignment 3
#在R中有的时候表达方式是不一样的，比如
引用某个变量的子变量用
time$year #而不是time.year

##常犯错误
该使用[]的时候错误的使用了（），特别是在操作data.frame的时候
该使用[[]]错误的使用了[]，前者可以变为向量，后者还是data.frame
忘记了使用%%进行
判断是否包含 
"a" %in% c("a","b","c")
表示数组相乘用 
%*%

如何使用Order
> (ii <- order(x <- c(1,1,3:1,1:4,3), y <- c(9,9:1), z <- c(2,1:9)))
 [1]  6  5  2  1  7  4 10  8  3  9
 > rbind(x, y, z)[,ii] # shows the reordering (ties via 2nd & 3rd arg)
  [,1] [,2] [,3] [,4] [,5] [,6] [,7] [,8] [,9] [,10]
x    1    1    1    1    2    2    3    3    3     4
y    5    6    9    9    4    7    1    3    8     2
z    5    4    1    2    6    3    9    7    2     8


</code></pre>