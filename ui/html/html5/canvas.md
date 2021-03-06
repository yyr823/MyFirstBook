> #### 认识Canvas元素

* canvas是HTML5新增的专门用来绘制图形的元素, 通过Canvas技术, 用户可以在Web中绘制各种图形. canvas元素它是一块无色透明的区域, 它只是一个容器, 开发者通过JavaScript脚本可以轻松的在区域上实现任意绘图 。 
* 在页面中添加canvas元素

```HTML
<html >
<body>
<canvas id="myCanvas" width="578" height="200">
您的浏览器不支持oanvas元素, 请更新或更换您的浏览器.
</canvas>
</body>
</html >
```

> #### Canvas绘制步骤

* 在html5页面中添加canvas元素, 定义 id属性值以便接下来调用

```HTML
<canvas  id="myCanvas" width="578" height="200"></canvas>
```

* 使用 id寻找页面中的canvas元素

```js
var c=document.getElementById("myCanvas");
```

* 通过canvas元素的getContext方法来获取其上下文\(Context\) ,即创建Context对象, 以获取允许进行绘制的2D环境。 

```js
var context=c.getContext("2d");
```

* 使用 JavaScript脚本来进行绘制

```js
context.fillStyle='#ff0000';
context.fillRect(50,25,100,50);
```

> #### 绘制直线相关的方法

| beginPath\(\) | 定义了一个新的路径绘制动作的开始 |
| :---: | :--- |
| moveTo\(\) | 为指定点创建了一个新的子路径, 这个点就变成了新的上下文点,我们可以把moveTo\(\) 方法看成用来定位我们的绘图鼠标用的 |
| lineTo\(\) | 以上下文点为起点, 到方法参数中指定的点之间函一条直线 |
| stroke\(\) | 为所画的线赋予颜色, 并使其可见.如果没有特别的指定颜色的,则默认使用黑色画直线 |

> #### 绘制直线的相关属性

| lineWidth | 直线的宽度 |
| :---: | :--- |
| strokeStyle | 直线的颜色 |
| 直线端点样式 | HTML5canvas支持3种i线的端点样式, 包括:butt,round,round 和 square.设定端点样式是用lineGap属性设定.缺省情况下,将使用butt样式 |

* 绘制矩形

绘制矩形使用**rect**\(\)方法。每个短形需要由左上角坐标\(x, y\) 和矩形的宽与高 \(width,height\)来确定。

* 绘制圆

画圆只需要在调用**arc**\(\)方法时,将起始角度设为0,终止角度设为2 \* Pl即可。

* 图形的颜色填充

要填充图形,需要用**filIStyIe**属性设五填充图形用的颜色,然后使用**fill**\(\)方法完成对图形的填充。默认情况下,fillStyle的颜色是黑色。

```js
<script>
    window.onload=function (){
     let canvas=document.getElementById("myCanvas");
     let context=canvas.getContext("2d");
//绘制矩形
     context.beginPath();
     context.rect(10,50,200,100);
      context.lineWidth=5;//线的粗细
      context.strokeStyle="blue";//线的颜色
      context.stroke();
      context.fillStyle="blue";//填充的颜色
      context.fill();//填充
//绘制圆
      context.beginPath();
      //圆心的坐标
      let centerX=canvas.width/1.5;
      let centerY=canvas.height/2;
      let radius=80;//半径
      context.arc(centerX,centerY,radius,0,1.5*Math.PI,false); //true逆时针 false顺时针
      context.lineWidth=5;//线的粗细
      context.strokeStyle="black";//线的颜色
      context.stroke();
    }
</script>
```

> #### 绘制文本

* [x] **绘制文本的方法**

`context.fillText(Text,x1, y1)`

其中text是要绘制的文本, x1 , y1是绘制文本的位置。

* [x] **设置文本的字体、大小和样式**

要设置字体、大小和样式,需要用到上下文对象的 **font**属性。样式可以是**normal,itaIic或bold.**默认情况是 normal 。

* [x] **设置文本颜色**

文本的颜色用**fillStyle**属性设置

* [x] **描绘文本边缘**

要描绘字体边缘的效果,要使用 **strokeText**\(\)方法替代**filIText**\(\), 同时要用**strokeStyle**属性替代 **filIStyIe**属性。

```js
  <script>
    window.onload = function () {
      let canvas = document.getElementById("myCanvas");
      let context = canvas.getContext("2d");
      let x = canvas.width / 2;
      let y = canvas.height / 2;
      context.font = "italic 40px Arial";
      context.fillStyle = "#ff0000";
      context.fillText("Hello World", x, y);
      context.lineWidth = 2;
      context.strokeText("Hello World", x, y + 50);
    }
  </script>
```

![](/assets/K4.png)

* [x] **绘制文本对齐**

文本的对齐功能设定使用 **textAlign**属性。其可用的选项包括**start, end,  left, center和 right。**

* [x] **文本度量**

要获取有关文本的尺度信息,可以使用 **measureText**\(\)方法。此方法需要一个文本字符串组为参数, 并返回一个尺度对象.尺度对象中的数据是基于所提供的字符串参数和当前的文本字体信息而来的.

* [x] **文本换行**

要实现文本换行功能, 我们需要创建一个用户自定义函数, 此函数需要**canvas**上下文对象,一个文本字符串、一个位置、一个最大宽度和行高度信息.函数将使用 **measureText**\(\)计算何时换行。

```js
  <script>
    window.onload = function () {
      let canvas = document.getElementById("myCanvas");
      let context = canvas.getContext("2d");
      let text = "They say a person needs just three things to be truly happy in this world: someone to love, something to do, and something to hope for.";
      let maxWidth = 300;//每一行绘制的长度,超过就换行
      let lineHeight = 25;//设置行之间的间隔
      let x = (canvas.width - maxWidth) / 2;//绘制起始坐标
      let y = 30;
      context.font = "16px Arial";
      context.fillStyle = "#000fff";
      wrapText(context, text, x, y, maxWidth, lineHeight);
    };
    function wrapText(context, text, x, y, maxWidth, lineHeight) {
      let words = text.split(" ");//以空格把字符串分割并存到数组里
      let line = "";
      for (let n = 0; n < words.length; n++) {
        let testLine = line + words[n] + " ";
        let metrics = context.measureText(testLine);
        let testWidth = metrics.width;//得到测量字符的宽度
        if (testWidth > maxWidth) {
          context.fillText(line, x, y);
          line = words[n] + " "; //重新给line赋值,绘制下一行
          y += lineHeight;//y坐标要加上行高,在上一行的下方绘制,避免绘制的内哦平重叠
        } else {
          line = testLine;
        }
      }
      context.fillText(line, x, y);//绘制文本
    }
  </script>
```

![](/assets/K5.png)

> #### **据说一个人在这个世上获得真正的幸福需要三件事情：有人爱，有事做，有所期待。**

![](/assets/K2.png)

```js
<script>
    window.onload=function (){
     let canvas=document.getElementById("myCanvas");
     let context=canvas.getContext("2d");
     //绘制弧线
     context.beginPath();
     context.moveTo(20,20);
     context.lineTo(100,20);
     context.arcTo(150,20,150,70,50);
     context.lineTo(150,120);
     context.stroke();     

     context.beginPath();
     context.moveTo(100,20);
     //第一条直线
      context.lineTo(200,160);
      //二次曲线
      context.quadraticCurveTo(230,200,250,120);
      //贝塞尔曲线
      context.bezierCurveTo(290,-40,300,200,400,150);
      //第二条直线
      context.lineTo(500,90);
      context.lineWidth=5;
      context.strokeStyle="blue";
      context.stroke();
    }
  </script>
```

#### ![](/assets/K1.png)

> #### 绘制径向渐变

首先使用 **createRadiaIGradient**\(\)方法创建canvasGradient对象, **语法如下**:

`var grad=context.createRadialGradient(X1,Y1,R1,X2,Y2, R2);`

其中X1,Y1,R1定义一个以\(X1, Y1\)为原点、半径为R1的国。 X2,Y2,R2定义一个以\(X2, Y2\)为原点、半径为R2的圆。然后使用 addColorStop方法定义色标的位置并上色 。grad. **addColorStop**\(position, color\) ;其中参数position为渐变中色标的相对位置 \(偏移量\)

> #### 绘制线性渐变

首先使用 **createLinearGradient**\(\)方法创建canvasGradient对象, **语法如下:**

`var grad=context.createLinearGradient(X1, Y1, X2, Y2);`

其中X1、 Y1为渐变的起点, X2、 Y2为渐变的终点。然后使用 **addColorStop**方法定义色标的位置并上色

grad. **addColorStop**\(position, color\) ;其中参数position为渐变中色标的相对位置 \(偏移量\)

```js
  <script>
    window.onload=function(){
      let c=document.getElementById("myCanvas");
      let context=c.getContext("2d");
      //线性渐变
      let clg=context.createLinearGradient(0,0,100,200);
      clg.addColorStop(0,"#ff0000");
      clg.addColorStop(0.5,"#00ff00");
      clg.addColorStop(1,"#0000ff");
      context.fillStyle=clg;
      context.strokeStyle=clg;
      context.fillRect(10,10,200,200);
      //径向渐变
      let crg=context.createRadialGradient(325,100,20,325,100,80);
      crg.addColorStop(0,"#ffffff");
      crg.addColorStop(0.75,"#ff0000");
      crg.addColorStop(1,"#000000");
      context.fillStyle=crg;
      context.fillRect(230,10,200,200);
    }
  </script>
```

![](/assets/K3.png)

> #### 绘制图像的方法

* **context.drawlmage\(imageObj, x,y\);**

此方法需要一个图像对象和一个起始点坐标作为参数, 其中起始点坐标是相对于canvas的左上角的位置

* **context. drawlmage\(imageObj, x, y, width,  height\);**

drawlmage方法还可以接受 width和 height两个参数用来以任意指定的尺寸显示图像。

* **context. drawlmage\(imageObj,sx,sy,sw, sh, dx, dy, dw, dh\);**

drawlmage方法还可以增加另六个参数来实现对图像的裁剪 。 这六个参数是

sourceX,sourceY, sourGeWidth, sourceHeight,destWidth和destHeight。

```js
  <script>
    window.onload=function(){
      let c=document.getElementById("myCanvas");
      let context=c.getContext("2d");
     let image=new Image();
     image.src="icon.png";
     image.onload=function(){
       context.drawImage(image,10,10);//原始图片的大小
      context.drawImage(image,10,10,200,200);//绘制图片的大小
      context.drawImage(image,50,40,300,450,50,50,350,450);//裁剪后的图像
     }
    }
  </script>
```

> #### 绘制阴影

**要为图形添加明影需要用到:**

`shadowColor:阴影颜色`

`shadowB1ur:阴影模糊度`

`shadowOffsetX:设置或返回阴影与形状的水平距高`

`shadowOffsetY:设置或返回阴影与形状的垂直距高`

> #### 绘制透明度

`globalAlpha属性`设置或还回绘图的当前透明值.属性值必须是介于**0.0\(完全透明\)与1.0\(不透明\)**之间的数字。

```js
  <script>
  window.onload=function (){
  let canvas=document.getElementById("myCanvas");
  let context=canvas.getContext("2d");
  //绘制圆
    context.beginPath();
//圆心的坐标
    let centerX=canvas.width/1.5;
    let centerY=canvas.height/2;
    let radius=80;//半径
    context.arc(centerX,centerY,radius,0,2*Math.PI,false); //true逆时针 false顺时针
    context.lineWidth=5;//线的粗细
    context.strokeStyle="black";//线的颜色
    context.stroke();
    context.fillStyle="#8ED6FF";//设置填充色
    //设置阴影
    context.shadowColor="green";
    context.shadowBlur=20;
    context.shadowOffsetX=10;
    context.shadowOffsetY=10;
    //设置透明度
    context.globalAlpha=0.2;
    context.fill();
  }
  </script>
```

> #### 绘制图案填充

用上下文对象的 **createPattern**\(\)方法创建一个图案填充对象, **语法如下:**

`context.createPattern(image, type);`

其中type必须为下面字符串之一: `repeat、 repeat-x、 repeat-y、 no-repeat`

```js
<script>
    function draw(type){
      let c=document.getElementById("myCanvas");
      let canvas=c.getContext("2d");
      canvas.clearRect(0,0,500,400);
      let img=document.getElementById("butterfly");
      let pat=canvas.createPattern(img,type);
      canvas.rect(0,0,500,400);
      canvas.fillStyle=pat;
      canvas.fill();
    }
  </script>
<body>
<p>图像的使用:</p>
<img src="icon.png" id="butterfly"/><br>
<button onclick="draw('repeat')">Repeat</button>
<button onclick="draw('repeat-x')">Repeat-x</button>
<button onclick="draw('repeat-y')">Repeat-y</button>
<button onclick="draw('no-repeat')">no-repeat</button>
<canvas id="myCanvas" width="500" height="400"></canvas>
</body>
```

> #### 图形的变换

* 移动坐标空间

使用 translate\(\) 方法可以将绘图原点横向和纵向的移动到指定的距离\(x, y\),结果表现为整张图像的移动。

* 旋转坐标空间

旋转canvas用的方法是 rotate\(\)。此方法接受一个以弧度为单位的旋转参教,整个canvas将以坐标原点,也就是由 transIate\(\)所确定的原点为圆心进行旋转。

* 缩放图形

缩放操作使用 scale\(\)方法,参数x、 y分别代表横向与纵向的缩放比例, 两个参数都是浮点数, 1. 0表示不缩放, 小于1. 0表示缩小,大于1. 0表示放大。

```js
  <script>
    window.onload = function () {
      let canvas = document.getElementById("myCanvas");
      let context = canvas.getContext("2d");
      let rectWidth=150;
      let  rectHeight=75;
      context.fillStyle="#ff0000";
      //把坐标原点移动到canvas中心点
      context.translate(canvas.width/2,canvas.height/2);
      //顺时针旋转45度
      context.rotate(0.25*Math.PI);
      //坐标在纵向上缩小一半
      context.scale(1,0.5);
      context.fillRect(-rectWidth/2,-rectHeight/2,rectWidth,rectHeight);
    }
  </script>
```

* 保存与恢复canvas状态

使用save\(\)和 restore\(\)方法可以实现对坐标变换状态的保存与恢复。

```js
  <script>
    window.onload = function () {
      let canvas = document.getElementById("myCanvas");
      let context = canvas.getContext("2d");
      //所绘制矩形的宽度和高度
      let rectWidth = 150;
      let rectHeight = 75;
      context.save();//保存状态1(坐标0,0)
      context.translate(canvas.width / 2, canvas.height / 2);
      context.save();//保存状态2(坐标移动到画布中间)
      context.rotate(Math.PI / 4);
      context.save();//保存状态3 (按中心点旋转45)
      context.scale(2, 2);//矩形宽度和高度增加2倍
      context.fillStyle = "blue";
      context.fillRect(-rectWidth / 2, -rectHeight / 2, rectWidth, rectHeight);
      context.restore();//回复状态3
      context.fillStyle = "red";
      context.fillRect(-rectWidth / 2, -rectHeight / 2, rectWidth, rectHeight);
      context.restore();//回复状态2
      context.fillStyle = "yellow";
      context.fillRect(-rectWidth / 2, -rectHeight / 2, rectWidth, rectHeight);
      context.restore();//回复状态1
      context.fillStyle = "green";
      context.fillRect(-rectWidth / 2, -rectHeight / 2, rectWidth, rectHeight);
    }
  </script>
```

> #### 图形的组合

globalCompositeOperation 属性设置或返回如何将一个源 \(新的\) 图像绘制到日标\(已有的\)的图像上。

属性值如下:

| source-over | 默认。在目标图像上显示源图像 |
| :--- | :--- |
| source-atop | 在目标图像顶部显示源图像。源图像位于目标图像之外的部分是不可见的 |
| source-in | 在目标图像中显示源图像。只有目标图像之内的源图像部分会显示, 目标图像是透明的 |
| source-out | 在 目标图像之外显示源图像.只有目标图像之外的源图像部分会显示,目标图像是透明的 |
| destination-over | 在源图像上显示目标图像 |
| destination-atop | 在源图像顶部显示目标图像。目标图像位于源图像之外的部分是不可见的 |
| destination-in | 在源图像中显示目标图像。只有源图像之内的目标图像部分会被显示, 源图像是透明的 |
| destination-out | 在源图像之外显示目标图像。只有源图像之外的目标图像部分会被显示, 源图像是透明的 |
| lighter | 显示源图像+ 目标图像,交叉处高亮显示 |
| darker | 显示源图像+目标图像 |
| copy | 显示源图像。忽略目标图像 |
| xor  | 使用异或操作对源图像与目标图像进行组合。 |

* #### **红色源图像    蓝色目标图像**

```js
  <script>
    window.onload = function () {
      let canvas = document.getElementById("myCanvas");
      let context = canvas.getContext("2d");
      //绘制矩形
      context.beginPath();
      context.rect(200, 20, 100, 100);
      context.fillStyle = "blue";
      context.fill();
      context.globalCompositeOperation = "source-over";
      context.globalCompositeOperation = "source-atop";
      context.globalCompositeOperation = "source-in";
      context.globalCompositeOperation = "destination-in";
      context.globalCompositeOperation = "destination-out";
      context.globalCompositeOperation = "lighter";
      context.globalCompositeOperation = "darker";
      context.globalCompositeOperation = "xor";
      context.globalCompositeOperation = "copy";
      //绘制圆
      context.beginPath();
      context.arc(320, 120, 60, 0, 2 * Math.PI, false);
      context.fillStyle = "red";
      context.fill();

    }
  </script>
```

![](/assets/kt.png)

> #### 图形的裁切

clip\(\)方法从原始画布中剪切任意的形状和尺寸 。

**提示:** 一旦剪切了某个区域, 则所有之后的绘图都会被限制在被剪切的区域内 \(不能访问画布上的其他区域\) 。 您也可以在使用

clip\(\)方法前通过使用 save\(\)方法对当前画布区域进行保存, 并在以后的任意时间对其进行恢复\(通过 restore\(\)方法\) 。

```js
 <script>
    window.onload = function () {
      let canvas = document.getElementById("myCanvas");
      let context = canvas.getContext("2d");
      context.rect(50, 20, 200, 120);
      context.stroke();
      context.fillStyle = "red";
      context.fillRect(0, 0, 150, 100);
      let canvas1 = document.getElementById("myCanvas2");
      let context1 = canvas1.getContext("2d");
      context1.rect(50, 20, 200, 120);
      context1.stroke();
      context1.clip();//裁切
      context1.fillStyle = "red";
      context1.fillRect(0, 0, 150, 100);
    }
  </script>
</head>
<body>
<span>没有裁切之前:</span><br>
<canvas id="myCanvas" width="300" height="150">
  您的浏览器不支持HTML5 canvas标签
</canvas>
<span>裁切之后:</span>
<canvas id="myCanvas2" width="300" height="150">
  您的浏览器不支持HTML5 canvas标签
</canvas>
</body>
```

![](/assets/kt2.png)

