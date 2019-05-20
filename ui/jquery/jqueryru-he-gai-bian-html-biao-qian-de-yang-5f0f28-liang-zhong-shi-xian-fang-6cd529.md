### 如何改变html标签的样式\(两种实现方法\)

* #### [原文链接](https://blog.csdn.net/liutianjie/article/details/84070816)

> #### **通过修改标签属性来改变它的样式**

1. [x] js设置和获取标签的属性

```js
<script type="text/javascript"> 
window.onload = function () { 
var attr = document.getElementById("attr"); 
attr.setAttribute("style", "font-weight:bold;") 
 alert(attr.getAttribute("style")); 
} 
</script> 
```

* [x] jquery设置和获取标签的属性

```js
<script src="jquery/jquery-1.4.2.min.js" type="text/javascript"></script> 
<script type="text/javascript"> 
$(function () { 
$("#attr").attr("style", "color:#ff0000");//单个属性的设置 
$("#Avatar").attr({ "class": "banner", "alt": "头像", 
"src": "http://pic.cnblogs.com/avatar/a118538.jpg?id=11133319" });//多个属性的设置 
alert($("#Avatar").attr("src")); //得到指定标签的属性 
}); 
</script> 
```

**值得注意的是JS的window.onload方法块的内容是在JQ的$\(function\(\){}\)方法块执行完成后，再执行的。**

> #### **通过修改标签的css样式来改变它的样式**

* [x] 看看基本的语法：

```js
$("#attr").addClass("banner");//添加样式 
$("#attr").removeClass("banner");//移除样式 
//ＪＱ支持连带写法，因为removeClass的返回结果也是一个Jq对象，所以Jq对象的所有方法和事件它都可以使用 
$("#attr").removeClass("banner").addClass("bannerOver"); 
```

* [x] 下面是一个例子，当在dd标签上单击时，将当前dd块进行高亮显示 

```js
<style> 
.banner { background: #0094ff; } 
.bannerOver { background: #808080; } 
.cur { background: #ff6a00; } 
</style> 
<script> 
$(function () { 
$('#menu_title').find('dd').click(function () { 
$('#menu_title').find('dd').removeClass('cur'); 
$(this).addClass('cur'); 
});
}); 
</script> 
<body>
<dl id="menu_title"> 
<dt>人</dt> 
<dd>一种高级动物</dd> 
<dt>狗</dt> 
<dd>人类的朋友</dd> 
<dt>猫</dt> 
<dd>猫科动物的祖先</dd> 
</dl> 
</body>
```

* [x] **下面是为表格的隔行变色效果**

```js
.odd { background: #808080; } 
.even { background: #ffd800; } 
.selected { background: #0094ff; color: #fff; }　　　　 
.hover { background: #808080; } 
 //选择所有行 
var $trs = $("#menu_title>dd"); 
//给奇数行添加odd样式 
$trs.filter(":odd").addClass("odd");
//给偶数行添加odd样式 
$trs.filter(":even").addClass("even"); 
```

* [x] 单击行后，让当前行高亮显示

```js
//点击行,添加变色样式 
$trs.click(function(e) { 
$(this).addClass("selected").siblings().removeClass("selected"); 
}) 
```

* [x] 添加鼠标移入与移出事件 

```js
// 鼠标移入 与移出 
$("#menu_title>dd").hover( 
function () { 
$(this).addClass("hover"); 
}, 
function () { 
$(this).removeClass("hover"); 
} 
); 
```





