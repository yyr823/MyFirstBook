### jquery禁用、启用button以及button的样式操作

* #### [**原文链接**](https://blog.csdn.net/qq_38455201/article/details/80591530)

> #### 一：**禁止使用button**

**1.直接写在&lt;button&gt;标签里面**

```html
<button id="btn" disabled="disabled">设置按钮不可以点击</button>
```

**2.js禁用button**

```js
document.getElementById("btn").disabled=true;
```

**3.使用jquery禁用button**

```js
$("#btn").attr('disabled',true);
$("#btn").attr('disabled','disabled');
$("#btn").prop('disabled','disabled');
```

> #### 二：设置禁用之后启用button

**1.使用js启用button**

```js
document.getElementById("btn").disabled = true;
```

**2.jquery启用button**

```js
$("#btn").attr('disabled',false);

$("#btn").removeAttr("disabled");

$("#btn").attr('disabled','');
```

> #### 三：button的显示与隐藏

```js
//jq:
$("#btn").show();

$("#btn").hide();
```

> #### 四：给button设置css样式

```css
background-color: #1AAD19;//设置背景颜色

color: #FFFFFF;//设置按钮上面的字体颜色

border: 1px solid #1AAD19;//设置边框的颜色

cursor: pointer;//设置鼠标移动到button的样式

border-radius: 3px;//设置倒角的大小，这个属性可以使得四个角有一定的角度更美观一点

width: 100px;//设置按钮的宽度

height: 36px;//设置按钮的高度

border:none;//去掉边框

background:url("static/images/reponse_add.png") no-repeat;//设置背景图片
```

> #### 五：设置button的click事件

```js
$("#btn").click(function(){
   //do something
```

> #### 六：jquery改变button的样式

**1.直接css\(\)方法进行修改样式**

```js
$("#btn").css("color","red");//改一种

$("#btn").css({

"color":"white",

"background-color":"#98bf21",

"font-family":"Arial",

"font-size":"20px",

"padding":"5px"

});//改多种，注意里面加大括号
```

**2.首先定义一个class的样式，然后动态的添加样式**

```css
.btnStyle{
    border: 1px solid #E4E8EB;
    border-radius: 100%;
    width: 36px;
    height: 36px;
    background-color: #FFFFFF;
    cursor: pointer;
}
```

**点击改成上面这个样式、点击移除上面这个样式。**

```js
$("#btn").click(function(){  
       $(this).addClass("btnStyle");  
 }) 
$("#btn").click(function(){  
       $(this).removeClass("btnStyle");  
 })
```



