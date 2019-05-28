> #### Css3设置边框属性

* [x] box-shadow属性

* 作用: 可以设置一个或多个下拉阴影的框。 

* 语法: box-shadow:h-shadow  v-shadow   blur  spread  color 

* 语法描述: 

| 值 | 描述 |
| :--- | :--- |
| h-shadow | 必需的。水平阴影的位置。允许负值 |
| v-shadow | 必需的。垂直阴影的位置。 先许负值 |
| blur   | 可选。模糊距离 |
| spread   | 可选。阴影的大小 |
| color  | 可选。阴影的颜色 |

* [x]  border-radius属性

*  作用: 这个属性允许你为元素添加圆角边框。 

* 语法: border-radius:none\|&lt;length&gt;{1,4}\[/&lt;length&gt;{1,4}\]

*  语法描述:

| length  | 定义弯道的形状, 由浮点数和单位标识符组成的长度值, 不可为负值 |
| :--- | :--- |


* ** 注意：每个半径的四个值的顺序是：左上角，右上角，右下角，左下角**

* [x] border-image属性

* 作用: 这个属性允许你为元素添力c,边框背景。 

* 语法: border-image:source slice width outset  repeat

* 语法插述: 

| 值 | 描述 |
| :--- | :--- |
| source  | 定义边框的背景图片源, 即图像URL |
| slice  | 定义如何裁切背景图像 |
| width  | 定义边框背景图像的显示大小 \(即边框显示大小\) |
| outset  | 定义边框背景图像的偏移位置\(不支持\) |
| repeat  | 定义边框背景團像的重复性,重复\(repeated\)、拉伸\(stretched\)或平铺\(rounded\)  |

> #### Css3设置背景属性

* [x] background-size属性

* 作用:用来定义背景图像的大小
* 语法: background-size:length\|percentage\|cover\|contain
* 语法描述: 

| 值 | 描述 |
| :--- | :--- |
| length  | 设五背景图片高度和宽度。第一个值设置宽度, 第二个值设置的高度 |
| percentage  | 将计算相对于背景定位区城的百分比。 第一个值设置宽度, 第二个值设置的高度 |
| cover  | 此时会保持图像的纵横比并将图像缩放成将完全覆盖背景定位区域的最小大小 |
| contain  | 此时会保持图像的纵横比并将图像缩放成将适合背景定位区域的最大大小 |

* [x] background-origin属性

* 作用:用来定义背景图像的定位区域
* 语法: background-origin:padding-box\|border-box\|content-box 

* 语法描述: 

| padding-box | 背景图像填充框的相对位置 |
| :--- | :--- |
| border-box | 背景图像边界框的相对位置 |
| content-box | 背景图像的相对位置的内容框 |

![](/assets/cq1.png)

* [x] background-clip属性

* 作用:用来定义背景图像的裁剪区域
* 语法: backgroud-clip:padding-box\|border-box\|content-box 
* 语法描述:

| border-box | 默认值,从边框区域向外裁剪背景 |
| :--- | :--- |
| padding-box | 从补白区域向外裁剪背景 |
| content-box | 从内容区域向外裁剪背景 |

 













