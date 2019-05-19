![](/assets/s1.png)![](/assets/s2.png)

![](/assets/s9.png)结果:  p  div body p div ....











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



