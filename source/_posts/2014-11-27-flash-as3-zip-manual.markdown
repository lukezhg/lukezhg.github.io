---
layout: post
title: "Flash AS3 zip Manual"
date: 2014-11-27 14:48
comments: true
categories: [flash]
tags: [flash,manual]
---
Action Script 3.0 简明手册  
在上机前确保你的flash是cs3或者以上版本，如果是flash8或者以前的版本，下面有些代码会报错。  
变量与常量  
变量有不同的类型，一个变量由变量名和值构成。  
<code/>
var value2:Number = 17;  
const SALES_TAX_RATE:Number = 0.07;  
</code>  
属性  
简单地视为包含在对象中的“子”变量。  
  
<code/>
square.x = 100;  
square.y = 150;  
square.rotation = triangle.rotation;  
square.scaleX = 1.5;  
square.scaleY = 1.5;  
square.currentFrame  
square.alpha = 30;  
square.height =20;  
square.width =40;  
square.visible =false;  
</code>
  
调用方法：变量名-点-属性名  
方法  
方法是指可以由对象执行的操作。  
  
    shortFilm.play();  
    shortFilm.stop();  
    shortFilm.gotoAndStop(1);  
  
某些方法可以执行计算并返回可以像变量一样使用的结果。  
  
    var numericData:Number = 9;  
    var textData:String = numericData.toString();  
    calculatorDisplay.text = numericData.toString();  
  
事件  
本质上，事件就是所发生的、ActionScript 能够识别并可响应的事情。  
在编写执行事件处理时三个重要元素：  
  
    事件源：事件实际发生的位置。  
    事件：发生的事情。  
    响应：事件发生时的执行动作。  
  
    this.stop();  
    function playMovie(event:MouseEvent):void{  
    this.play();}  
  
    playButton.addEventListener(MouseEvent.CLICK, playMovie);  
  
算数运算符  
+-*/^  

逻辑运算符  
==  
&&  
||  

  
if (dayOfWeek == "Wednesday"){  
takeOutTrash();}  
  
//单行注释  
/*多行  
注释  
*/  
  
流控制  
函数  
调用函数调用函数  
  
    trace("Use trace to help debug your script");  
    var randomNum:Number = Math.random();  
   
    var someDate:Date = new Date();  
    var dayNum:uint = someDate.getDay();  
  
定义函数  
  
    function traceParameter(aParam:String){  
        trace(aParam);}  
   
    traceParameter("hello"); // hello  
  
从函数返回值  
  
    function doubleNum(baseNum:int):int{  
        return (baseNum * 2);}  
   
<code/>
function passPrimitives(xParam:int, yParam:int):void{  
    xParam++;  
    yParam++;  
    trace(xParam, yParam);  
}  
</code>  
函数参数  
  
    var xValue:int = 10;  
    var yValue:int = 15;  
    trace(xValue, yValue);// 10 15  
    passPrimitives(xValue, yValue); // 11 16  
    trace(xValue, yValue);// 10 15  
  
循环  
  
for循环  
  
    var i:int;  
    for (i = 0; i < 5; i++){  
    trace(i);}  
  
    for..in  
  
    var myObj:Object = {x:20, y:30};  
    for (var i:String in myObj){  
    trace(i + ": " + myObj[i]);  
    }  
    //output:  
    //x: 20  
    // y: 30  
  
条件语句  
  
    if (x > 0){  
    trace("x is positive");}  
    else if (x < 0){  
    trace("x is negative");}  
    else{  
    trace("x is 0");}  
  
switch语句  
  
<code/>
switch(dayNum){  
case 0:trace("Sunday");  
break;  
case 1:trace("Monday");  
break;  
case 2:trace("Tuesday");  
break;  
case 3:trace("Wednesday");  
break;  
case 4:trace("Thursday");  
break;  
case 5:trace("Friday");  
break;  
case 6:trace("Saturday");  
break;  
default:trace("Out of range");  
break;  
}  
</code>  

类  
点语法  
  
点运算符 (.) 提供对对象的属性和方法的访问。使用点语法，可以使用后跟点运算符和属性名或方法名的实例名来引用类的属性或方法。以下面的类定义为例：  
  
<code/>
class DotExample  
{  
public var prop1:String;  
public function method1():void {}  
}  
</code>  
借助于点语法，可以使用在如下代码中创建的实例名来访问 prop1 属性和 method1() 方法：  
<code/>  
var myDotEx:DotExample = new DotExample();  
myDotEx.prop1 = "hello";  
myDotEx.method1();  
</code>  
定义包时，可以使用点语法。可以使用点运算符来引用嵌套包。例如，EventDispatcher 类位于一个名为 events 的包中，该包嵌套在名为 flash 的包中。可以使用下面的表达式来引用 events 包：  
  
flash.events  
  
还可以使用此表达式来引用 EventDispatcher 类：  
  
flash.events.EventDispatcher  
  
数组  
  
<code/>
var names:Array = new Array("John", "Jane", "David");  
trace(names.length); //output: 3  
trace(names[0]);// output: John  
trace(names[1]); //output: Jane  
trace(names[2]);// output: David  
</code>  
  
  
实例教程  
对象的初始化  
1 在主场景中新建一个矩形，全选然后F8转换为元件，命名为box。在第一帧里面尝试加入：  
代码1  
  
<code/>
box.x = 10;  
box.y = 150;  
</code>  
代码2  
<code/>  
box.rotation = triangle.rotation;  
box.scaleX = 1.5;  
box.scaleY = 1.5;  
</code>  
2 把box变成一个骰子，尝试  
代码3  
<code/>  
box.currentFrame  
box.alpha = 30;  
box.height =20;  
box.width =40;  
box.visible =false;  
</code>  
3 尝试使用随机函数  
代码4  
<code/>  
box.x = this.stage.width*Math.random();  
box.y = this.stage.height*Math.random();  
</code>  
  
影片剪辑的控制  
  
<code/>
box.stop();  
box.play();  
box.gotoAndStop(1);  
box.gotoAndPlay(3);  
box.gotoAndStop(Math.round(6*Math.random()));  
</code>  

影片剪辑的控制  
  
<pre><code/>
import flash.display.*;
import flash.events.*;
mcFace.addEventListener(MouseEvent.MOUSE_DOWN,startDragFace);//添加监听

//startDragFace函数
function startDragFace(e:MouseEvent):void {
mcFace.startDrag();
}

mcFace.addEventListener(MouseEvent.MOUSE_UP,stopDragFace);

function stopDragFace(e:MouseEvent):void {
mcFace.stopDrag();

}
</code></pre> 

播放和定制按钮  
1、制作按钮  
2、给按钮命名为btn  
3、在第一帧添加代码（该实例来自：AS3基础教程实例1 给按钮添加动作 | 且行电子学档: http://www.eportfolios.cn/node/2146）  
  
    btn.addEventListener(MouseEvent.CLICK,btnClick);//给btn注册事件帧听器  
    btn.addEventListener(MouseEvent.ROLL_OVER,btnRollOver);//注册鼠标放上事件帧听器  
    btn.addEventListener(MouseEvent.ROLL_OUT,btnRollOut);//注册鼠标离开事件帧听器  
   
//点击事件处理函数  
    function btnClick(e:MouseEvent):void{  
    trace(e.currentTarget.name);//trace就是在输出面板里输出内容，这里输出"btn"，只有在flash测试的时候才有效  
    }  
   
//鼠标放在btn上的事件处理函数  
    function btnRollOver(e:MouseEvent):void{  
    txt.text="鼠标放在了按钮上";//给文本框txt的text属性赋值为"鼠标放在了按钮上"  
    }  
   
//鼠标从btn上离开的事件处理函数  
    function btnRollOut(e:MouseEvent):void{  
    txt.text="鼠标从按钮上离开了";  
    }  
  
4、添加一个动态文本框，命名为txt  
ctrl+enter测试影片  
修改代码如下：  
  
    btn.addEventListener(MouseEvent.CLICK,btnClick);//给btn注册事件帧听器  
   
//点击事件处理函数  
    function btnClick(e:MouseEvent):void{  
    box.gotoAndStop(Math.round(6*Math.random()));  
    }  

测试影片，如果成功则再建一个按钮元件，命名为btnPlay,修改代码为：  
  
    btn.addEventListener(MouseEvent.CLICK,btnClick);//给btn注册事件帧听器  
   
//点击事件处理函数  
    function btnClick(e:MouseEvent):void{  
    box.stop();  
    }  
    btnPlay.addEventListener(MouseEvent.CLICK,btnPlayClick);//给btnPlay注册事件帧听器  
   
//点击事件处理函数  
    function btnPlayClick(e:MouseEvent):void{  
    box.play();  
    }  
  
如何使用文本框（Text）  

使用前可以导入以下声明  
	import flash.text.TextField;
	import flash.text.TextFormat;
	import flash.text.TextFormatAlign;

Number()将字符型转化为数值型变量  
toString()将数值转化为字符  

  
5、尝试仿照实例让代码与fla源文件分离：  
实例：（AS3基础教程实例1 给按钮添加动作 | 且行电子学档: http://www.eportfolios.cn/node/2146）  

本文参考了:  
adobe AS3帮助手册：http://tinyurl.com/7ujc2yp  
  
Flash实例  
简单实例  
  
    Flash教程：送给初学者的一点使用技巧_Flash实例教程_IT部落: http://edu.itbulo.com/200711/120855.htm  
    立体板-Flash源文件-闪吧Flash8: http://www.flash8.net/fla/10364.shtml  
    放大镜-Flash源文件 - 闪吧Flash8: http://www.flash8.net/fla/10144.shtml  
    卷轴和毛笔写字- Flash源文件 - 闪吧Flash8: http://www.flash8.net/fla/10342.shtml  
    地球旋转-上传：明月老师 Flash源文件 - 闪吧Flash8: http://www.flash8.net/fla/10237.shtml  
    瀑布-上传：CC851246330 Flash源文件 - 闪吧Flash8: http://www.flash8.net/fla/9515.shtml  
  
  
复杂实例  
ActionScript 3.0的流程控制语法_知行网: http://www.zhixing123.cn/Flash/2111.html  
flash actionScript3 处理xml 教程_知行网: http://www.zhixing123.cn/Flash/20080.html    