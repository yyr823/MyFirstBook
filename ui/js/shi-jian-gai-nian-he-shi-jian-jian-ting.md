![](/assets/s1.png)![](/assets/s2.png)

* **冒泡型事件:**

![](/assets/s9.png)**结果:  p  div body p div ....**

* 捕获型事件:

![](/assets/s10.png)**结果: body   div   p  body  div    p ....**

![](/assets/s4.png)![](/assets/s5.png)**一般不会使用:**

```js
//Ie特有:

       function show() {
                alert(1);
            }
            var test1 = document.getElementById("test1");
            var test2 = document.getElementById("test2");

    window.onload=function(){
            test1 .attachEvent("onclick",show);
                   test2.onclick=function(){
                   test1.detachEvent("onclick",show);    
                        };
        }

//标准DOM:
          window.onload = function() {

                test1.addEventListener("click", show, true);
                //true 冒泡型事件  false 捕获型事件
                test2.onclick = function() {
                test1.removeEventListener("click", show, true);
                };
            }
```

> #### 访问事件对象

**实践对象封装了事件发生的详细信息,尤其是鼠标,键盘事件.如鼠标事件发生的位置,键盘事件的键盘键等**

> * #### IE中的事件对象

**IE中的事件对象是一个隐式可用的全局对象:event,它是window对象的一个属性.**

```js
op.onclick=function(){
var oEvent=window.event;
}
```

> * #### 标准DOM中的事件对象

**在标准DOM浏览器检测到发生了某个事件时,将自动创建一个Event对象,并隐式地将该对象作为事件处理函数的第一个参数传入.**

```js
op.onclick=function(oEvent){
  //作为参数传进来
}
```

* [x] **经验之谈:为了兼容不同的浏览器,通常采用下面的方法得到事件对象.**

```js
op.onclick=function(oEvent){
    if(window.event){
        oEvent=window.event;
    }
}
```

![](/assets/sj3.png)

```js
<!DOCTYPE html>
<html>

    <head>
        <meta charset="UTF-8">
        <title>事件的目标</title>
        <script>
            function handle(oEvent) {
                if(window.event) {
                    oEvent = window.event;
                }
                var oTarget;
                if(oEvent.srcElement) {
                    oTarget = oEvent.srcElement;//IE

                } else {
                    oTarget = oEvent.target;//标准DOM
                }
                alert(oTarget.tagName); //弹出IMG
            }

            window.onload = function() {
                var oImg = document.getElementsByTagName("img")[0];
                oImg.onclick = handle;
            }
        </script>

    </head>

    <body>
        <img src="img/HBuilder.png" border="0" />
    </body>

</html>
```

> #### 常见的事件类型

![](/assets/sj1.png)

```js
<!DOCTYPE html>
<html>

	<head>
		<meta charset="UTF-8">
		<title>鼠标事件</title>
		<script>
			function handle(oEvent) {
				if(window.event) {
					oEvent = window.event; //处理兼容性，获得事件对象
				}
				var oDiv = document.getElementById("display"); 
				oDiv.innerHTML += oEvent.type + "<br/>";//输出事件名称
			}

			window.onload = function() {
				var oImg = document.getElementsByTagName("img")[0];
				oImg.onmousedown = handle;
				oImg.onmouseup = handle;
				oImg.onmouseover = handle;
				oImg.onmouseout = handle;
				oImg.onclick = handle;
				oImg.ondblclick = handle;
			}
		</script>

	</head>
	<body>
		<img src="img/HBuilder.png" border="0" />
		<div id="display"></div>
	</body>

</html>
```

```js
<!DOCTYPE html>
<html>

	<head>
		<meta charset="UTF-8">
		<title>键盘事件</title>
		<script>
			function handle(oEvent) {
				if(window.event) {
					oEvent = window.event; //处理兼容性，获得事件对象
				}
				var oDiv = document.getElementById("display");
				oDiv.innerHTML += oEvent.type + "<br/>"; //输出事件名称
			}

			window.onload = function() {
				var txt = document.getElementsByTagName("textarea")[0];
				txt.onkeydown = handle;
				txt.onkeyup = handle;
				txt.onkeypress = handle;
			}
		</script>

	</head>

	<body>
		<textarea rows="4" cols="50"></textarea>
		<div id="display"></div>
	</body>

</html>
```

![](/assets/sj2.png)

```HTML
<body onload="alert('hello')" onunload="alert('byebye')">
		<form action="https://www.baidu.com" onsubmit="return false">
			<input type="text" value="a" onfocus="alert('获取焦点')" onblur="alert('失去焦点')" />
			<input type="text" value="b" onchange="alert('内容改变了')" onselect="alert('内容选中了')" />
			<select name="city" onchange="alert('选项改变了')">
				<option>上海</option>
				<option>北京</option>
			</select>
			<br/>
			<input type="submit" value="提交" />

		</form>

</body>
```



