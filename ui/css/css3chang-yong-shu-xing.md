> #### Css3设置边框属性

* [x] **box-shadow属性**

* 作用: 可以设置一个或多个下拉阴影的框。

* 语法: `box-shadow:h-shadow  v-shadow   blur  spread  color`

* 语法描述:

| 值 | 描述 |
| :---: | :---: |
| h-shadow | 必需的。水平阴影的位置。允许负值 |
| v-shadow | 必需的。垂直阴影的位置。 先许负值 |
| blur | 可选。模糊距离 |
| spread | 可选。阴影的大小 |
| color | 可选。阴影的颜色 |

```css
 <style>
  div{
    width: 300px;
    height: 100px;
    background-color: yellow;
     box-shadow:20px 20px  5px #888888;
  }
    input{
      padding: 4px;
      border: solid 1px #E5E5E5;
      font-family:'sans-serif';
      width: 200px;
      background: #FFFFFF;
      box-shadow:10px 10px  5px rgba(0,0,0,0.5);
    }
  input:hover,input:focus{
      border-color: #c9c58a;
    }
label{
  margin-left: 10px;
  color: #999999;
}
    .submit input{
      width: auto;
      padding: 9px 15px;
      background: #617798;
      border: 0;
      font-size: 14px;
      color: #FFFFFF;
    }
  </style>
<body>
<h3>box-shadow</h3>
<div></div>
<h3>登录表单</h3>
<form>
  <p class="name">
    <label for="name"> 姓名 </label>
    <input type="text" name="name" id="name">
  </p>
  <p class="email">
    <label for="email"> 邮箱 </label>
    <input type="text" name="email" id="email">
  </p>
  <p class="submit">
    <input type="submit" value="提交"/>
  </p>
</form>
</body>
```

![](/assets/kt1.png)

* [x] **border-radius属性**

* 作用: 这个属性允许你为元素添加圆角边框。

* 语法: `border-radius:none|<length>{1,4}[/<length>{1,4}]`

* 语法描述:

| length | 定义弯道的形状, 由浮点数和单位标识符组成的长度值, 不可为负值 |
| :---: | :--- |


* **注意:每个半径的四个值的顺序是：左上角，右上角，右下角，左下角**

```css
  <style>
    div {
      width: 100px;
      height: 50px;
      background: #b3d4fc;
      text-align: center;
      line-height: 50px;
    }

    .bd1 {
      border-radius: 100px 0 100px 0;
    }

    .bd2 {
      border-radius: 5px;
    }

    .bd3 {
      border-radius: 10px 15px 10px 5px;
    }

    .bd4 {
      border-radius: 15px 5px;
    }

    .bd5 {
      border-radius: 15px 10px 5px;
    }
  </style>
<body>
<h3>border-radius</h3>
<span>左上100px  右下100px 右上 0px 左下0px</span>
<div class="bd1"></div>
<span>四角都为5px</span>
<div class="bd2"></div>
<span>左上10px  右下10px 右上 15px 左下5px</span>
<div class="bd3"></div>
<span>左上右下15px 右上左下5px</span>
<div class="bd4"></div>
<span>左上15px 右下5px 右上左下10px</span>
<div class="bd5"></div>
</body>
```

![](/assets/ke2.png)

* [x] **border-image属性**

* 作用: 这个属性允许你为元素添加边框背景。

* 语法: `border-image:source slice width outset  repeat`

* 语法插述:

| 值 | 描述 |
| :---: | :---: |
| source | 定义边框的背景图片源, 即图像URL |
| slice | 定义如何裁切背景图像 |
| width | 定义边框背景图像的显示大小 \(即边框显示大小\) |
| outset | 定义边框背景图像的偏移位置\(不支持\) |
| repeat | 定义边框背景图片的重复性,重复\(repeat\)、拉伸\(stretch\)或平铺\(round\) |

```css
  <style>
  div{
    width:250px;
    border: 15px solid transparent;
    padding: 10px 20px;
  }
  #round{
    border-image: url("kk.jpeg")  200 round;
  }
  #stretch{
    border-image: url("kk.jpeg") 200 stretch;
  }
  </style>
<body>
<h3>border-image</h3>
<div id="round">使用round来填充容器</div>
<br>
<div id="stretch">使用stretch来填充容器</div>
</body>
```

![](/assets/ke1.png)

> #### Css3设置背景属性

* [x] **background-size属性**

* 作用:用来定义背景图像的大小

* 语法: `background-size:length|percentage|cover|contain`

* 语法描述:

| 值 | 描述 |
| :--- | :--- |
| length | 设五背景图片高度和宽度。第一个值设置宽度, 第二个值设置的高度 |
| percentage | 将计算相对于背景定位区城的百分比。 第一个值设置宽度, 第二个值设置的高度 |
| cover | 此时会保持图像的纵横比并将图像缩放成将完全覆盖背景定位区域的最小大小\(以y轴为主\) |
| contain | 此时会保持图像的纵横比并将图像缩放成将适合背景定位区域的最大大小\(以x轴为主\) |

* [x] **background-origin属性**

* 作用:用来定义背景图像的定位区域

* 语法:`background-origin:padding-box|border-box|content-box`

* 语法描述:

| padding-box | 背景图像填充框的相对位置 |
| :--- | :--- |
| border-box | 背景图像边界框的相对位置 |
| content-box | 背景图像的相对位置的内容框 |

![](/assets/cq1.png)

* [x] **background-clip属性**

* 作用:用来定义背景图像的裁剪区域

* 语法: `backgroud-clip:padding-box|border-box|content-box`

* 语法描述:

| border-box | 默认值,从边框区域向外裁剪背景 |
| :--- | :--- |
| padding-box | 从补白区域向外裁剪背景 |
| content-box | 从内容区域向外裁剪背景 |

> #### CSS3文本相关

* [x] **CSS3 @font-face规则**

* 以前CSS的版本, 网页设计师不得不使用用户计算机上已经安装的字体。

* 使用CSS3, 网页设计师可以使用他/她喜欢的任何字体。

* 当你发现您要使用的字体文件时, 只需简单的将字体文件包含在网站中, 它会自动下载给需要的用户

* 我们要做的就是在@font-face规则中完成对字体的描述。

* [**可参考链接**](https://www.cnblogs.com/hellman/p/6773461.html)

```css
@font-face{
font-family: myFirstFont;
src:url(sansation_bold.ttf); 
font-weight:bold; 
}
```

| font-family | 必需。规定字体的名称 |
| :--- | :--- |
| src | 必需。定义字体文件的 URL |
| font-style | 可选。定义字体的样式。默认是"normal" |
| font-weight | 可选。定义字体的粗细。默认是"normal” |

**提示:**[**免费字体下载**](https://www.dafont.com/single-malta.font)

```css
<style>
    @font-face {
      font-family: 'Alex';
      src: url("KK.ttf") format('truetype');
      font-weight: bold;
      font-style: italic;
    }
    .font-face-display{
      font:66px Alex
    }
  </style>
<body>
<div class="font-face-display">Take me to your heart</div>
</body>
```

![](/assets/ke4.png)

* [x] **目前主要的几种网络字体**

* TrueType\(.ttf\)格式: 此字体是Windows和Mac的最常见的字体, 是一种RAW格式,  因此他不为网站优化, 支持这种手体的浏览器有\[lE9+,Firefox3.5+,Chrome4+, Safari3+,Opera10+,iOS MobileSafari4.2+\]

* OpenType\(.otf\)格式: .otf字体被认为是一种原始的字体格式, 其内置在TrueType的基础上, 所以也提供了更多的功能,支持这种手体的浏览器有\[Firefox3.5+,Chrome4.0+,Safari3.1+,Opera10.0+, iOS MobileSafari4. 2+\]

* Web Open Font Format\(.woff\)格式: woff字体是Web手体中最佳格式, 他是一个开放的TrueType/0penType的压缩版本。支持这种字体的浏览器有\[lE9+, Firefox3.5+, Chrome6+, Safari3. 6+,0pera11.1+\]

* Embedded Open Type\(.eot\)格式:.eot字体是lE专用字体, 可以从TrueType创建此格式字体,支持这种字体的浏览器有\[lE4+\]

* [x] **word-wrap属性**

* 作用: 用来定义文本超过指定容器的边界时是否断开转行

* 语法: `word-wrap:normal|break-word`

* 语法描述:

| normal | 只在先许的断字点换行 \(浏览器保持默认处理\) |
| :--- | :--- |
| break-word | 在长单词或 URL地址内部进行换行 |

* [x] **text-overflow属性**

* 作用: 用来定义省略文本的处理方式

* 语法: `text-overflow:clip|ellipisis|string`

* 语法描述:

| clip | 修剪文本 |
| :--- | :--- |
| ellipsis | 显示省略持号来代表被修剪的文本 |
| string | 使用给定的字符事来代表被修剪的文本\(当前浏览器不支持\) |

**注意**: 实际上,text-overflow属性仅是内容注解, 表明当文本溢出时是否显示省略标记, 并不具备样式定义的特性。要实现溢出时产生省略号的效果, 我们应该再定义两个样式:强制文本一行内显示\(white-space:nowrap\)和溢出内容为隐藏\(overflow:hidden\)

> #### 颜色相关

* [x] **RGBA颜色值**

* 作用:它在红、绿、蓝三原色通道的基础上增加了不透明度参数。

* 语法:`RGBA(R,G,B,A)`

* 语法插述:

| 取值 | 描述 |
| :---: | :---: |
| R | 红色值,0-255 |
| G | 绿色值,0-255 |
| B | 蓝色值,0-255 |
| A | 透明度,0-1之间 |

* [x] **HSL颜色值**

* 作用: 它通过对色调\(H\)、 他和度\(S\)和亮度\(L\) 3个颜色通道的变化以及它们相互之间的叠加来获得各种颜色 。

* 语法: `HSL(<Hue>,<Saturation>,<Lightness>)`

* 语法描述:

| Hue | 0\(或360\)表示红色, 120表示绿色, 240表示蓝色,也可取其他数值来指定颜色。取值为: 0-360 |
| :---: | :--- |
| Saturation | 取值为: 0.0% -100.0%, 0%表示灰色,100%颜色最艳。 |
| Lightness | 取值为: 0.0%-100.0%,0%最暗,  显示为黑色,100%最亮, 显示为白色 |

* [x] **HSLA颜色值**

* 作用: 它通过对色调\(H\)、 他和度\(S\)和亮度\(L\) 3个要素基础上增加了不透明度参数。

* 语法: `HSL(<Hue>,<Saturation>,<Lightness>,<alpha>)`

* 语法描述:

| Hue | 0\(或360\)表示红色, 120表示绿色, 240表示蓝色,也可取其他数值来指定颜色。取值为: 0-360 |
| :---: | :--- |
| Saturation | 取值为: 0.0% -100.0%, 0%表示灰色,100%颜色最艳。 |
| Lightness | 取值为: 0.0%-100.0%,0%最暗,  显示为黑色,100%最亮, 显示为白色 |
| alpha | 取值0~1之间 |

```css
<style>
    li {
      list-style-type: none;
    }

    li.rgba1 {
      background: rgba(255, 255, 0, 1);
    }

    li.rgba2 {
      background: rgba(255, 255, 0, 0.8);
    }

    li.rgba3 {
      background: rgba(255, 255, 0, 0.6);
    }

    li.rgba4 {
      background: rgba(255, 255, 0, 0.4);
    }

    li.rgba5 {
      background: rgba(255, 255, 0, 0.2);
    }

    li.rgba6 {
      background: rgba(255, 255, 0, 0);
    }

    /*HSL*/
    div.hsl1 {
      background: hsl(320, 100%, 50%);
      height: 20px;
    }

    div.hsl2 {
      background: hsl(320, 50%, 50%);
      height: 20px;
    }

    div.hsl3 {
      background: hsl(320, 100%, 75%);
      height: 20px;
    }

    div.hsl4 {
      background: hsl(202, 100%, 50%);
      height: 20px;
    }

    div.hsl5 {
      background: hsl(202, 50%, 50%);
      height: 20px;
    }

    div.hsl6 {
      background: hsl(202, 100%, 75%);
      height: 20px;
    }

    /*HSLA*/
    div.hsla1 {
      background: hsla(320, 100%, 50%, 0.2);
      height: 20px;
    }

    div.hsla2 {
      background: hsla(320, 50%, 50%, 0.4);
      height: 20px;
    }

    div.hsla3 {
      background: hsla(320, 100%, 75%, 0.6);
      height: 20px;
    }

    div.hsla4 {
      background: hsla(202, 100%, 50%, 0.8);
      height: 20px;
    }

    div.hsla5 {
      background: hsla(202, 50%, 50%, 1.0);
      height: 20px;
    }

    div.hsla6 {
      background: hsla(202, 100%, 75%, 0);
      height: 20px;
    }
  </style>
<body>
<h3>Css3的RGBA效果</h3>
<ul>
  <li class="rgba1">1</li>
  <li class="rgba2">0.8</li>
  <li class="rgba3">0.6</li>
  <li class="rgba4">0.4</li>
  <li class="rgba5">0.2</li>
  <li class="rgba6">0</li>
</ul>
<h3>Css3的HSL效果</h3>
<div class="hsl1"></div>
<div class="hsl2"></div>
<div class="hsl3"></div>
<div class="hsl4"></div>
<div class="hsl5"></div>
<div class="hsl6"></div>
<h3>Css3的HSLA效果</h3>
<div class="hsla1"></div>
<div class="hsla2"></div>
<div class="hsla3"></div>
<div class="hsla4"></div>
<div class="hsla5"></div>
<div class="hsla6"></div>
</body>
```

![](/assets/ke3.png)

* [x] **transparent**

* 作用:相当于使用了值为0的alpha通道,将背景、文字、边框等的颜色设定为完全透明。

```css
<style>
.test{
color:transparent;
border:1px solid transparent;
background:transparent;
}
</style>
```



