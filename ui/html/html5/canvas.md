> ####  认识Canvas元素

*  canvas是HTML5新增的专门用来绘制图形的元素, 通过Canvas技术, 用户可以在Web中绘制各种图形. canvas元素它是一块无色透明的区域, 它只是一个容器, 开发者通过JavaScript脚本可以轻松的在区域上实现任意绘图 。 
*  在页面中添加canvas元素

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

*  在html5页面中添加canvas元素, 定义 id属性值以便接下来调用

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

> ####  绘制直线相关的方法

| beginPath\(\) | 定义了一个新的路径绘制动作的开始 |
| :---: | :--- |
| moveTo\(\) | 为指定点创建了一个新的子路径, 这个点就变成了新的上下文点,我们可以把moveTo\(\) 方法看成用来定位我们的绘图鼠标用的  |
| lineTo\(\) | 以上下文点为起点, 到方法参数中指定的点之间函一条直线 |
| stroke\(\) | 为所画的线赋予颜色, 并使其可见.如果没有特别的指定颜色的,则默认使用黑色画直线 |

> ####  绘制直线的相关属性

| lineWidth      | 直线的宽度 |
| :---: | :--- |
| strokeStyle     | 直线的颜色 |
| 直线端点样式 | HTML5canvas支持3种i线的端点样式, 包括:butt,round,round 和 square.设定端点样式是用lineGap属性设定.缺省情况下,将使用butt样式 |

* 绘制矩形

绘制矩形使用 rect\(\)方法。每个短形需要由左上角坐标\(x, y\) 和矩形的宽与高 \(width,height\)来确定。 

* 绘制圆

画圆只需要在调用 arc\(\)方法时,将起始角度设为0,终止角度设为2 \* Pl即可。 

* 图形的颜色填充

要填充图形,需要用 filIStyIe属性设五填充图形用的颜色,然后使用 fill\(\)方法完成对图形的填充。默认情况下,   fillStyle的颜色是黑色。 

> #### 绘制文本

* [x] **绘制文本的方法**

`context.fillText(Text,x1, y1)`

其中text是要绘制的文本, x1 , y1是绘制文本的位置。 

* [x] **设置文本的字体、大小和样式**

要设置字体、大小和样式,需要用到上下文对象的 font属性。样式可以是 normal,  itaIic或bold.默认情况是 normal 。 

* [x] **设置文本颜色**

文本的颜色用fillStyle属性设置

* [x] **描绘文本边缘**

要描绘字体边缘的效果,要使用 strokeText\(\)方法替代filIText\(\), 同时要用strokeStyle属性替代 filIStyIe属性。 

* [x] **绘制文本对齐**

文本的对齐功能设定使用 textAl ign属性。其可用的选项包括start, end,  left, center和 right。 

* [x] **文本度量**

要获取有关文本的尺度信息,可以使用 measureText\(\)方法。此方法需要一个文本字符串组为参数, 并返回一个尺度对象.尺度对象中的数据是基于所提供的字符串参数和当前的文本字体信息而来的.

* [x] **文本换行**

要实现文本换行功能, 我们需要创建一个用户自定义函数, 此函数需要canvas上下文对象,一个文本字符串、一个位五、一个最大宽度和行高度信息.函数将使用 measureText\(\)计算何时换行。 

#### ![](/assets/K1.png)

> #### 绘制径向渐变

首先使用 createRadiaIGradient\(\)方法创建canvasGradient对象, **语法如下**:

**`var grad=context.createRadialGradient(X1,Y1,R1,X2,Y2, R2);`**

其中X1,Y1,R1定义一个以\(X1, Y1\)为原点、半径为R1的国。 X2,Y2,R2定义一个以\(X2, Y2\)为原点、半径为R2的圆。然后使用 addColorStop方法定义色标的位置并上色 。grad. addColor\(position, color\) ;其中参数position为渐变中色标的相对位置 \(偏移量\) .

> #### 绘制图案填充

用上下文对象的 createPattern\(\)方法创建一个图案填充对象, **语法如下:** 

**`context. createPattern(image, type);`**

其中type必须为下面字符串之一: **`repeat、 repeat-x、 repeat-y、 no-repeat`**







