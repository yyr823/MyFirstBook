### onclick事件传变量时注意的问题

* #### [**原文链接**](https://blog.csdn.net/tuohuang0303/article/details/55841119)

* [x] **onclick事件传变量时**

```js
var setname="start";
return '<img src="images/control_start_blue.png" style="cursor:hand" width="15px" height="15px" onclick="sendMsg(\''+setname+'\');" >';
```

**上面这个注意\''这个是一个\和两个'单引号，而不是一个"双引号，刚开始老看不明白，是因为两个'放一起看起来像"双引号了。**

* #### [**原文链接**](https://blog.csdn.net/legend11/article/details/53408459)

* [x] ** onclick事件中传递对象参数**

```js
var user = {id:1, name:'zs', age:20};

var ele = '<a onclick="edit(' + JSON.stringify(user).replace(/"/g, '&quot;') + ');">修改</a>';

或者 

var ele = '<a onclick="edit(\'' + JSON.stringify(user).replace(/"/g, '&quot;') + '\');">修改</a>';
```

**前者取到的是json对象，后者取到的是json字符串。**

