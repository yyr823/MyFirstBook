### js正则验证特殊字符

* #### [**参考链接**](https://blog.csdn.net/rentian1/article/details/79784662)

* #### 方案一

```js
var regEn = /[`~!@#$%^&*()_+<>?:"{},.\/;'[\]]/im,
    regCn = /[·！#￥（——）：；“”‘、，|《。》？、【】[\]]/im;
 
if(regEn.test(newName) || regCn.test(newName)) {
    alert("名称不能包含特殊字符.");
    return false;
}
```

* #### 方案二

```js
function checkName(val){ 
    var reg = new RegExp("[`~!@#$^&*()=|{}':;',\\[\\].<>/?~！@#￥……&*（）——|{}【】‘；：”“'。，、？]"); 
    var rs = ""; 
    for (var i = 0, l = val.length; i < val.length; i++) { 
        rs = rs + val.substr(i, 1).replace(reg, ''); 
    } 
    return rs; 
}
```



