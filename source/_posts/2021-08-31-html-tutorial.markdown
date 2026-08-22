---
title: Web开发简明教程
date: 2021-08-31 13:12:58
tags: [html, css, js]
---

## [](#写在前面的话 "写在前面的话")写在前面的话

有一种语言几乎每个没学过编程的人也都会天天接触，这种语言就是html语言。几乎所以的网页都需要它来写，所以的网站都离不开他，所有的电脑都支持它，所以学一点html不一定是要从事web开发，而是让你对互联网世界有更深层的了解，并在必要的时候读懂和改写代码，让创造性得到施展，让工作和生活更顺畅。
本教程将带你快速浏览网页背后的代码，涉及的内容包括html、CSS、JavaScript、Python、Bootstrap、Jquery、SQL。这些语言和工具足够你开发一个自己的网站和实现想要的功能了。下面，就开始你的探索之旅吧！！

## [](#出发前的准备 "出发前的准备")出发前的准备

- 建议安装一个好用的文本编辑器，用于写代码，比如sublime、Visual Studio Code等，如果不按照用系统自动的文本编辑器也可以，只不过用户体验不会很好。
- 建议选择一个可多端同步笔记软件，比如印象笔记、Onenote、有道云笔记等，实在不行也可以用纸质笔记本记录自己的学习过程，特别是重要的语句和技术思想，这是你能否学以致用的关键。
- 安装谷歌或者火狐浏览器，便于对网页进行调试和预览。
- 测试以下代码的方法，拷贝代码，用编辑器新建文件，粘贴代码，另存为test.html,双击用浏览器打开预览效果，如果对效果不满意，可以对文件重新编辑。
- 在线测试的方法，点击这个[链接](https://www.w3schools.com/js/tryit.asp?filename=tryjs_intro_inner_html)，然后把代码粘贴进去，运行即可。

## [](#html基本 "html基本")html基本

html是网页注释语言，你可以用它来创建自己的网页。

### [](#html文档 "html文档")html文档

```
<!DOCTYPE html>
<html>
<head>
<title>Hello World</title>
</head>
<body>
<h1>这是我的标题</h1>
<p>这是我的段落</p>
</body>
</html>
```

### [](#标题h "标题h")标题h

```
<!DOCTYPE html>
<html>
<body>
<h1>This is heading 1</h1>
<h2>This is heading 2</h2>
<h3>This is heading 3</h3>
</body>
</html>
```

### [](#段落p "段落p")段落p

```
<!DOCTYPE html>
<html>
<body>
<p>This is a paragraph.</p>
<p>This is another paragraph.</p>
</body>
</html>
```

### [](#超级连接a "超级连接a")超级连接a

```
<!DOCTYPE html>
<html>
<body>
<h2>HTML Links</h2>
<p>网页链接用a标记</p>
<a href="zhangchunlei.com">连接</a>
</body>
</html>
```

### [](#图片img "图片img")图片img

```
<!DOCTYPE html>
<html>
<body>
<h2>HTML Images</h2>
<p>HTML images are defined with the img tag:</p>
<img src="https://www.w3schools.com/html/w3schools.jpg" alt="W3Schools.com" width="104" height="142">
</body>
</html>
```

### [](#按钮和JS特效 "按钮和JS特效")按钮和JS特效

```
<!DOCTYPE html>
<html>
<body>
<h2>按钮</h2>
<p>HTML按钮使用关键字button标记:</p>
<p id="demo" style="display:none">这是JS特性!</p>
<button type="button" onclick="document.getElementById('demo').style.display='block'">点我!</button>
</body>
</html>
```

### [](#列表ul和ol "列表ul和ol")列表ul和ol

```
<!DOCTYPE html>
<html>
<body>
<h2>无序列表</h2>
<ul>
  <li>无丝分裂</li>
  <li>有丝分裂</li>
  <li>减数分裂</li>
</ul>
<h2>有序列表</h2>
<ol>
  <li>前期</li>
  <li>中期</li>
  <li>后期</li>
</ol>
</body>
</html>
```

### [](#样式style "样式style")样式style

```
<!DOCTYPE html>
<html>
<body>
<p>I am normal</p>
<p style="color:red;">I am red</p>
<p style="color:blue;">I am blue</p>
<p style="font-size:50px;">I am big</p>
</body>
</html>
```

### [](#文本格式 "文本格式")文本格式

```
<!DOCTYPE html>
<html>
<body>
<p><b>This text is bold</b></p>
<p><i>This text is italic</i></p>
<p>This is<sub> subscript</sub> and <sup>superscript</sup></p>
</body>
</html>
```

### [](#注释 "注释")注释

注释虽然并不显示，但是可以帮助阅读和理解代码。

```
<!DOCTYPE html>
<html>
<body>
<!-- This is a comment -->
<p>This is a paragraph.</p>
<!-- Comments are not displayed in the browser -->
</body>
</html>
```

### [](#颜色color "颜色color")颜色color

```
<!DOCTYPE html>
<html>
<body>
<h1 style="background-color:Tomato;">Tomato</h1>
<h1 style="background-color:Orange;">Orange</h1>
<h1 style="background-color:DodgerBlue;">DodgerBlue</h1>
<h1 style="background-color:MediumSeaGreen;">MediumSeaGreen</h1>
<h1 style="background-color:Gray;">Gray</h1>
<h1 style="background-color:SlateBlue;">SlateBlue</h1>
<h1 style="background-color:Violet;">Violet</h1>
<h1 style="background-color:LightGray;">LightGray</h1>
</body>
</html>
```

### [](#CSS样式 "CSS样式")CSS样式

可以使得代码更简洁

```
<!DOCTYPE html>
<html>
<head>
<style>
body {background-color: powderblue;}
h1   {color: blue;}
p    {color: red;}
</style>
</head>
<body>
<h1>This is a heading</h1>
<p>This is a paragraph.</p>
</body>
</html>
```

### [](#在新窗口打开连接 "在新窗口打开连接")在新窗口打开连接

```
<!DOCTYPE html>
<html>
<body>
<h2>The target Attribute</h2>
<a href="https://www.w3schools.com/" target="_blank">Visit W3Schools!</a>
<p>如果target="_blank"，网页会在新窗口或便签页打开。</p>
</body>
</html>
```

### [](#图片大小尺寸width-amp-height "图片大小尺寸width&height")图片大小尺寸width&height

```
<!DOCTYPE html>
<html>
<body>
<h2>图谱尺寸</h2>
<p>自定义图片长宽</p>
<img src="https://www.w3schools.com/html/img_girl.jpg" alt="Girl in a jacket" width="500" height="600">
</body>
</html>
```

### [](#图片picture "图片picture")图片picture

```
<!DOCTYPE html>
<html>
<head>
<meta name="viewport" content="width=device-width, initial-scale=1.0">
</head>
<body>
<h2>The picture Element</h2>
<picture>
  <source media="(min-width: 650px)" srcset="img_food.jpg">
  <source media="(min-width: 465px)" srcset="img_car.jpg">
  <img src="img_girl.jpg" style="width:auto;">
</picture>
<p>改变浏览器宽度可以自动更换图,部分浏览器版本可能不支持</p>
</body>
</html>
```

### [](#span "span")span

```
<!DOCTYPE html>
<html>
<body>
<p>This is an inline span <span style="border: 1px solid; color:black">Hello World</span> element inside a paragraph.</p>
<p>The SPAN element is an inline element, and will not start on a new line and only takes up as much width as necessary.</p>
</body>
</html>
```

### [](#class "class")class

```
<!DOCTYPE html>
<html>
<head>
<style>
.note {
  font-size: 120%;
  color: red;
}
</style>
</head>
<body>
<h1>My <span class="note">Important</span> Heading</h1>
<p>This is some <span class="note">important</span> text.</p>
</body>
</html>
```

### [](#ID-JS "ID +JS")ID +JS

```
<!DOCTYPE html>
<html>
<body>
<h2>用JavaScript调用ID</h2>
<p>JavaScript可以使用getElementById()方法来改变元素内容</p>
<h1 id="myHeader">Hello World!</h1>
<button onclick="displayResult()">Change text</button>
<script>
function displayResult() {
  document.getElementById("myHeader").innerHTML = "Have a nice day!";
}
</script>
</body>
</html>
```

还可以使用JS和getElementById方法改变特定元素的属性。

```
document.getElementById("demo").style.fontSize = "25px";
document.getElementById("demo").style.color = "red";
document.getElementById("demo").style.backgroundColor = "yellow";
document.getElementById("image").src = "picture.gif";
```

### [](#iframe行内框架 "iframe行内框架")iframe行内框架

```
<!DOCTYPE html>
<html>
<body>
<h2>制定特定网页在特定位置打开</h2>
<iframe src="" name="iframe_a" height="300px" width="100%" title="Iframe Example"></iframe>
<p><a href="https://www.w3schools.com" target="iframe_a">W3Schools.com</a></p>
<p>当点击链接时，该页面会在制定框架打开</p>
</body>
</html>
```

### [](#file-path "file path")file path

```
<img src="picture.jpg"> 文件在网页相同目录（当前目录）#相对路径
<img src="images/picture.jpg">  文件在当前目录下的images文件夹中
<img src="/images/picture.jpg"> 文件中根目录下的images文件夹中
<img src="../picture.jpg">  文件中当前目录上一层文件夹中
<img src="https://www.w3schools.com/images/picture.jpg"> #绝对路径
```

### [](#head "head")head

head是一个包含下列元素title, style, meta, link, script，base的容器。 它位于html和body标记之间。例如：

```
<!DOCTYPE html>
<html>
<head>
  <title>Page Title</title>
  <meta charset="UTF-8">
  <meta name="description" content="Free Web tutorials">
  <meta name="keywords" content="HTML, CSS, JavaScript">
  <meta name="author" content="John Doe">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <link rel="stylesheet" href="mystyle.css">
  <base href="https://www.w3schools.com/" target="_blank">
  <script>
  function myFunction() {
    document.getElementById("demo").innerHTML = "Hello JavaScript!";
  }
  </script>
</head>
<body>
<p>All meta information goes inside the head section.</p>
</body>
</html>
```

### [](#canvas "canvas")canvas

```
<!DOCTYPE html>
<html>
<body>
<canvas id="myCanvas" width="200" height="100" style="border:1px solid #d3d3d3;">
Your browser does not support the HTML canvas tag.</canvas>
//line
<script>
var c = document.getElementById("myCanvas");
var ctx = c.getContext("2d");
ctx.moveTo(0,0);
ctx.lineTo(200,100);
ctx.stroke();
</script>
//circle
<script>
var c = document.getElementById("myCanvas");
var ctx = c.getContext("2d");
ctx.beginPath();
ctx.arc(95, 50, 40, 0, 2 * Math.PI);
ctx.stroke();
</script>
//hello world 1
<script>
var c = document.getElementById("myCanvas");
var ctx = c.getContext("2d");
ctx.font = "30px Arial";
ctx.fillText("Hello World", 10, 50);
</script>
//hello world 2
<script>
var c = document.getElementById("myCanvas");
var ctx = c.getContext("2d");
ctx.font = "30px Arial";
ctx.strokeText("Hello World", 10, 50);
</script>
// gradient
<script>
var c = document.getElementById("myCanvas");
var ctx = c.getContext("2d");
// Create gradient
var grd = ctx.createLinearGradient(0, 0, 200, 0);
grd.addColorStop(0, "red");
grd.addColorStop(1, "white");
// Fill with gradient
ctx.fillStyle = grd;
ctx.fillRect(10, 10, 150, 80);
</script>
</body>
</html>
```

绘制图片

```
<!DOCTYPE html>
<html>
<body>
<p>Image to use:</p>
<img id="scream" src="img_the_scream.jpg" alt="The Scream" width="220" height="277">
<p>Canvas to fill:</p>
<canvas id="myCanvas" width="250" height="300"
style="border:1px solid #d3d3d3;">
Your browser does not support the HTML canvas tag.</canvas>
<p><button onclick="myCanvas()">Try it</button></p>
<script>
function myCanvas() {
  var c = document.getElementById("myCanvas");
  var ctx = c.getContext("2d");
  var img = document.getElementById("scream");
  ctx.drawImage(img,10,10);
}
</script>
</body>
</html>
```

## [](#CSS "CSS")CSS

CSS是定义网页显示风格的语言。

### [](#什么是CSS "什么是CSS?")什么是CSS?

CSS是Cascading Style Sheets的缩写
CSS描述了HTML元素如何在屏幕或者其他媒体中现实的样式。
CSS能节省大量的工作。它能够轻松定制多个网页。
外部风格定义表单存储在CSS文件中。我们只需要一个CSS文件，就可以管控所以网页。

### [](#CSS插入的3种方式 "CSS插入的3种方式")CSS插入的3种方式

- 外部CSS文件
- 在网页head容器内插入CSS
- 在元素内插入CSS

### [](#外部CSS文件 "外部CSS文件")外部CSS文件

```
<link rel="stylesheet" href="mystyle.css">
```

### [](#网页内嵌风格 "网页内嵌风格")网页内嵌风格

```
<!DOCTYPE html>
<html>
<head>
<style>
body {
  background-color: lightblue;
}
h1 {
  color: white;
  text-align: center;
}
p {
  font-family: verdana;
  font-size: 20px;
  color: red;
  text-align: center;
}
p.center {
  text-align: center;
  color: red;
}
.center {
  text-align: center;
  color: red;
}
</style>
</head>
<body>
<h1>My First CSS Example</h1>
<p>This is a paragraph.</p>
<h1 class="center">Red and center-aligned heading</h1>
<p class="center">Red and center-aligned paragraph.</p>
</body>
</html>
```

### [](#行内插入CSS "行内插入CSS")行内插入CSS

```
<!DOCTYPE html>
<html>
<body>
<h1 style="color:blue;text-align:center;">This is a heading</h1>
<p style="color:red;">This is a paragraph.</p>
</body>
</html>
```

## [](#JavaScript "JavaScript")JavaScript

### [](#改变元素内容 "改变元素内容")改变元素内容

```
<!DOCTYPE html>
<html>
<body>

<h2>What Can JavaScript Do?</h2>

<p id="demo">JavaScript can change HTML content.</p>

<button type="button" onclick='document.getElementById("demo").innerHTML = "Hello JavaScript!"'>Click Me!</button>

</body>
</html>
```

### [](#改变元素属性值 "改变元素属性值")改变元素属性值

```
<!DOCTYPE html>
<html>
<body>
<h2>What Can JavaScript Do?</h2>
<p>JavaScript can change HTML attribute values.</p>
<p>In this case JavaScript changes the value of the src (source) attribute of an image.</p>
<button onclick="document.getElementById('myImage').src='https://www.w3schools.com/js/pic_bulbon.gif'">Turn on the light</button>
<img id="myImage" src="pic_bulboff.gif" style="width:100px">
<button onclick="document.getElementById('myImage').src='https://www.w3schools.com/js/pic_bulboff.gif'">Turn off the light</button>
</body>
</html>
```

### [](#对象object "对象object")对象object

```
<!DOCTYPE html>
<html>
<body>
<h2>JavaScript Objects</h2>
<p>There are two different ways to access an object property.</p>
<p>You can use person.property or person["property"].</p>
<p id="demo"></p>
<script>
// Create an object:
const person = {
  firstName: "John",
  lastName : "Doe",
  id     :  5566
};
// Display some data from the object:
document.getElementById("demo").innerHTML =
person.firstName + " " + person.lastName;
</script>
</body>
</html>
```

### [](#事件events "事件events")事件events

```
<!DOCTYPE html>
<html>
<body>
<button onclick="document.getElementById('demo').innerHTML=Date()">The time is?</button>
<p id="demo"></p>
</body>
</html>
```

### [](#函数调用 "函数调用")函数调用

```
<!DOCTYPE html>
<html>
<body>
<h2>JavaScript Math.random()</h2>
<p>Math.random() returns a random number between 0 and 1:</p>
<button type="button" onclick='myFunction()'>Click Me!</button>
<p id="demo"></p>
<script>
  function myFunction() {
    document.getElementById("demo").innerHTML = Math.random();
  }
</script>
</body>
</html>
```

### [](#数据类型 "数据类型")数据类型

```
let length = 16;                               // Number
let lastName = "Johnson";                      // String
let x = {firstName:"John", lastName:"Doe"};    // Object
```

### [](#应遵循的良好习惯 "应遵循的良好习惯")应遵循的良好习惯

[best practice you should follow](https://www.w3schools.com/js/js_best_practices.asp)

## [](#代码示例 "代码示例")代码示例

### [](#博客网站layout样例 "博客网站layout样例")博客网站layout样例

```
<!DOCTYPE html>
<html>
<head>
<style>
* {
  box-sizing: border-box;
}

body {
  font-family: Arial;
  padding: 10px;
  background: #f1f1f1;
}

/* Header/Blog Title */
.header {
  padding: 30px;
  text-align: center;
  background: white;
}

.header h1 {
  font-size: 50px;
}

/* Style the top navigation bar */
.topnav {
  overflow: hidden;
  background-color: #333;
}

/* Style the topnav links */
.topnav a {
  float: left;
  display: block;
  color: #f2f2f2;
  text-align: center;
  padding: 14px 16px;
  text-decoration: none;
}

/* Change color on hover */
.topnav a:hover {
  background-color: #ddd;
  color: black;
}

/* Create two unequal columns that floats next to each other */
/* Left column */
.leftcolumn {
  float: left;
  width: 75%;
}

/* Right column */
.rightcolumn {
  float: left;
  width: 25%;
  background-color: #f1f1f1;
  padding-left: 20px;
}

/* Fake image */
.fakeimg {
  background-color: #aaa;
  width: 100%;
  padding: 20px;
}

/* Add a card effect for articles */
.card {
  background-color: white;
  padding: 20px;
  margin-top: 20px;
}

/* Clear floats after the columns */
.row:after {
  content: "";
  display: table;
  clear: both;
}

/* Footer */
.footer {
  padding: 20px;
  text-align: center;
  background: #ddd;
  margin-top: 20px;
}

/* Responsive layout - when the screen is less than 800px wide, make the two columns stack on top of each other instead of next to each other */
@media screen and (max-width: 800px) {
  .leftcolumn, .rightcolumn {
    width: 100%;
    padding: 0;
  }
}

/* Responsive layout - when the screen is less than 400px wide, make the navigation links stack on top of each other instead of next to each other */
@media screen and (max-width: 400px) {
  .topnav a {
    float: none;
    width: 100%;
  }
}
</style>
</head>
<body>

<div class="header">
  <h1>My Website</h1>
  <p>Resize the browser window to see the effect.</p>
</div>

<div class="topnav">
  <a href="#">Link</a>
  <a href="#">Link</a>
  <a href="#">Link</a>
  <a href="#" style="float:right">Link</a>
</div>

<div class="row">
  <div class="leftcolumn">
    <div class="card">
      <h2>TITLE HEADING</h2>
      <h5>Title description, Dec 7, 2017</h5>
      <div class="fakeimg" style="height:200px;">Image</div>
      <p>Some text..</p>
      <p>Sunt in culpa qui officia deserunt mollit anim id est laborum consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco.</p>
    </div>
    <div class="card">
      <h2>TITLE HEADING</h2>
      <h5>Title description, Sep 2, 2017</h5>
      <div class="fakeimg" style="height:200px;">Image</div>
      <p>Some text..</p>
      <p>Sunt in culpa qui officia deserunt mollit anim id est laborum consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco.</p>
    </div>
  </div>
  <div class="rightcolumn">
    <div class="card">
      <h2>About Me</h2>
      <div class="fakeimg" style="height:100px;">Image</div>
      <p>Some text about me in culpa qui officia deserunt mollit anim..</p>
    </div>
    <div class="card">
      <h3>Popular Post</h3>
      <div class="fakeimg"><p>Image</p></div>
      <div class="fakeimg"><p>Image</p></div>
      <div class="fakeimg"><p>Image</p></div>
    </div>
    <div class="card">
      <h3>Follow Me</h3>
      <p>Some text..</p>
    </div>
  </div>
</div>

<div class="footer">
  <h2>Footer</h2>
</div>

</body>
</html>
```

### [](#钟表代码 "钟表代码")钟表代码

```
<!DOCTYPE html>
<html>
<body>
<canvas id="canvas" width="400" height="400"
style="background-color:#333">
</canvas>
<script>
var canvas = document.getElementById("canvas");
var ctx = canvas.getContext("2d");
var radius = canvas.height / 2;
ctx.translate(radius, radius);
radius = radius * 0.90
setInterval(drawClock, 1000);
//define functions
function drawClock() {
  drawFace(ctx, radius);
  drawNumbers(ctx, radius);
  drawTime(ctx, radius);
}
function drawFace(ctx, radius) {
  var grad;
  ctx.beginPath();
  ctx.arc(0, 0, radius, 0, 2*Math.PI);
  ctx.fillStyle = 'white';
  ctx.fill();
  grad = ctx.createRadialGradient(0,0,radius*0.95, 0,0,radius*1.05);
  grad.addColorStop(0, '#333');
  grad.addColorStop(0.5, 'white');
  grad.addColorStop(1, '#333');
  ctx.strokeStyle = grad;
  ctx.lineWidth = radius*0.1;
  ctx.stroke();
  ctx.beginPath();
  ctx.arc(0, 0, radius*0.1, 0, 2*Math.PI);
  ctx.fillStyle = '#333';
  ctx.fill();
}
function drawNumbers(ctx, radius) {
  var ang;
  var num;
  ctx.font = radius*0.15 + "px arial";
  ctx.textBaseline="middle";
  ctx.textAlign="center";
  for(num = 1; num < 13; num++){
    ang = num * Math.PI / 6;
    ctx.rotate(ang);
    ctx.translate(0, -radius*0.85);
    ctx.rotate(-ang);
    ctx.fillText(num.toString(), 0, 0);
    ctx.rotate(ang);
    ctx.translate(0, radius*0.85);
    ctx.rotate(-ang);
  }
}
function drawTime(ctx, radius){
    var now = new Date();
    var hour = now.getHours();
    var minute = now.getMinutes();
    var second = now.getSeconds();
    //hour
    hour=hour%12;
    hour=(hour*Math.PI/6)+
    (minute*Math.PI/(6*60))+
    (second*Math.PI/(360*60));
    drawHand(ctx, hour, radius*0.5, radius*0.07);
    //minute
    minute=(minute*Math.PI/30)+(second*Math.PI/(30*60));
    drawHand(ctx, minute, radius*0.8, radius*0.07);
    // second
    second=(second*Math.PI/30);
    drawHand(ctx, second, radius*0.9, radius*0.02);
}
function drawHand(ctx, pos, length, width) {
    ctx.beginPath();
    ctx.lineWidth = width;
    ctx.lineCap = "round";
    ctx.moveTo(0,0);
    ctx.rotate(pos);
    ctx.lineTo(0, -length);
    ctx.stroke();
    ctx.rotate(-pos);
}
</script>
</body>
</html>
```

### [](#web-game实例 "web game实例")web game实例

```
<!DOCTYPE html>
<html>
<head>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<style>
canvas {
    border:1px solid #d3d3d3;
    background-color: #f1f1f1;
}
</style>
</head>
<body onload="startGame()">
<script>
var myGamePiece;
var myObstacles = [];
var myScore;

function startGame() {
    myGamePiece = new component(20, 20, "red", 10, 120);
    myGamePiece.gravity = 0.5;
    myScore = new component("30px", "Consolas", "black", 280, 40, "text");
    myGameArea.start();
}

function myrefresh(){
    window.location.reload();
}

var myGameArea = {
    canvas : document.createElement("canvas"),
    start : function() {
        this.canvas.width = 480;
        this.canvas.height = 270;
        this.context = this.canvas.getContext("2d");
        document.body.insertBefore(this.canvas, document.body.childNodes[0]);
        this.frameNo = 0;
        this.interval = setInterval(updateGameArea, 20);
        },
    clear : function() {
        this.context.clearRect(0, 0, this.canvas.width, this.canvas.height);
    }
}

function component(width, height, color, x, y, type) {
    this.type = type;
    this.score = 0;
    this.width = width;
    this.height = height;
    this.speedX = 0;
    this.speedY = 0;
    this.x = x;
    this.y = y;
    this.gravity = 0;
    this.gravitySpeed = 0;
    this.update = function() {
        ctx = myGameArea.context;
        if (this.type == "text") {
            ctx.font = this.width + " " + this.height;
            ctx.fillStyle = color;
            ctx.fillText(this.text, this.x, this.y);
        } else {
            ctx.fillStyle = color;
            ctx.fillRect(this.x, this.y, this.width, this.height);
        }
    }
    this.newPos = function() {
        this.gravitySpeed = this.gravity;
        this.x += this.speedX;
        this.y += this.speedY + this.gravitySpeed;
        this.hitBottom();
    }
    this.hitBottom = function() {
        var rockbottom = myGameArea.canvas.height - this.height;
        if (this.y > rockbottom) {
            this.y = rockbottom;
            this.gravitySpeed = 0;
        }
    }
    this.crashWith = function(otherobj) {
        var myleft = this.x;
        var myright = this.x + (this.width);
        var mytop = this.y;
        var mybottom = this.y + (this.height);
        var otherleft = otherobj.x;
        var otherright = otherobj.x + (otherobj.width);
        var othertop = otherobj.y;
        var otherbottom = otherobj.y + (otherobj.height);
        var crash = true;
        if ((mybottom < othertop) || (mytop > otherbottom) || (myright < otherleft) || (myleft > otherright)) {
            crash = false;
        }
        return crash;
    }
    //event listener
    document.addEventListener("keydown",keyDownHandler, false);
    document.addEventListener("keyup",keyUpHandler, false);
}

function updateGameArea() {
    var x, height, gap, minHeight, maxHeight, minGap, maxGap;
    for (i = 0; i < myObstacles.length; i += 1) {
        if (myGamePiece.crashWith(myObstacles[i])) {
            return;
        }
    }
    myGameArea.clear();
    myGameArea.frameNo += 1;
    if (myGameArea.frameNo == 1 || everyinterval(150)) {
        x = myGameArea.canvas.width;
        minHeight = 20;
        maxHeight = 200;
        height = Math.floor(Math.random()*(maxHeight-minHeight+1)+minHeight);
        minGap = 50;
        maxGap = 200;
        gap = Math.floor(Math.random()*(maxGap-minGap+1)+minGap);
        myObstacles.push(new component(10, height, "green", x, 0));
        myObstacles.push(new component(10, x - height - gap, "green", x, height + gap));
    }
    for (i = 0; i < myObstacles.length; i += 1) {
        myObstacles[i].x += -1;
        myObstacles[i].update();
    }
    myScore.text="SCORE: " + myGameArea.frameNo;
    myScore.update();
    myGamePiece.newPos();
    myGamePiece.update();
}

function everyinterval(n) {
    if ((myGameArea.frameNo / n) % 1 == 0) {return true;}
    return false;
}

function accelerate(n) {
    myGamePiece.gravity = n;
}

//------------
//Key Handlers
//------------
function keyDownHandler(event)
{
    var keyPressed = String.fromCharCode(event.keyCode);
    if ((keyPressed == "W") || (keyPressed == "&"))
    {
        accelerate(-1.5);
    }
}
function keyUpHandler(event)
{
    var keyPressed = String.fromCharCode(event.keyCode);
    if ((keyPressed == "W") || (keyPressed == "&") )
    {
        accelerate(1);
    }
}
</script>

<br>
<button onmousedown="accelerate(-0.2)" onmouseup="accelerate(0.05)">ACCELERATE</button>
<button onclick="myrefresh()">Restart</button>
<p>使用上下方向键控制</p>
<p>看你能坚持多久?</p>
</body>
</html>
```
