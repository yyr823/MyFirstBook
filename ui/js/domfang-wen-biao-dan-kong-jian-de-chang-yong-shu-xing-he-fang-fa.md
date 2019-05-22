> #### DOM访问列表框、下拉菜单的常用属性

| form | 返回列表框/下拉框所在的表单对象 |
| :--- | :--- |
| length | 返回列表框/下拉框的选项个数 |
| options | 返回列表框/下拉菜单里所有选项组成的数组 |
| selectedIndex | 返回下拉列表中选中选项的索引 |
| type | 返回下拉列表的类型, 多选的话返回select-multiple,单选select-one |

> #### 使用options\[index\]返回具体选项所对应的常用属性

| defaultSelected | 返回该选项默认是否被选中 |
| :--- | :--- |
| index | 返回该选项在列框/下拉菜单中的索引 |
| selected | 返回该选项是否被选中 |
| text | 返回该选项呈现的文本 |
| value | 返回该选项的value属性值 |

> #### 在elements返回的数组中访问具体的表单控件语法如下

| .elements\[index\] | 返回该表单中的第index个表单控件 |
| :--- | :--- |
| .elements\[elementName\] | 返回表单内id或name为elementName的表单控件 |
| .elementName | 返回表单中id或name为elementName的表单控件 |

* **案例:表单控件**

```js
<!DOCTYPE html>
<html>
    <head>
        <meta charset="UTF-8">
        <title>表单控件</title>
        <script>
            function operateForm() {
                var myForm = document.forms[0];
                console.log(myForm.action);
                console.log(myForm.method);
                console.log(myForm.target);
                myForm.submit(); //表单提交
                //myForm.reset(); //表单重置
            }
        </script>
    </head>
    <body>
        <form id="myform" action="https://www.baidu.com" method="get" target="_self">
            <input name="username" type="text" value="liming" /><br/>
            <input name="password" type="password" value="123456" /><br/>
            <select name="city">
                <option value="shanghai">上海</option>
                <option value="beijing">北京</option>
            </select><br/>
            <input type="button" value="获取表单内的第一个控件" onclick="alert(document.getElementById('myform').elements[0].value)" />
            <input type="button" value="获取表单内的第二个控件" onclick="alert(document.getElementById('myform').elements['password'].value)" />
            <input type="button" value="获取表单内的第三个控件" onclick="alert(document.getElementById('myform').city.value)" />
            <input type="button" value="操作表单" onclick="operateForm()" />
        </form>
    </body>
</html>
```

* **案例:查找列表框,下拉菜单控件**

```js
<!DOCTYPE html>
<html>
    <head>
        <meta charset="UTF-8">
        <title>查找列表框,下拉菜单控件</title>
    </head>
    <body>
        <select name="city" id="city" size="5">
            <option value="shanghai">上海</option>
            <option value="beijing" selected="selected">北京</option>
            <option value="shanghai">天津</option>
            <option value="beijing">南京</option>
            <option value="shanghai">武汉</option>
            <option value="shanghai">深圳</option>
        </select><br/>
        <input type="button" value="第一个城市" onclick="change(s_city.options[0])" />
        <input type="button" value="上一个城市" onclick="change(s_city.options[s_city.selectedIndex-1])" />
        <input type="button" value="下一个城市" onclick="change(s_city.options[s_city.selectedIndex+1])" />
        <input type="button" value="最后一个城市" onclick="change(s_city.options[s_city.length-1])" />
        <script>
            var s_city = document.getElementById("city");
            var change = function(city) {
                alert(city.text);
            }
        </script>
    </body>
</html>
```

> #### DOM访问表格子元素的常用属性和方法如下

| caption | 返回表格的标题对象 |
| :--- | :--- |
| rows | 返回该表格里所有行 |
| tbodies | 返回该表格里所有&lt;tbody../&gt;元素组成的数组 |
| tfoot | 返回该表格里所有的&lt;tfoot../&gt;元素 |
| thead | 返回该表格里所有的&lt;thead../&gt;元素 |

> #### 通过rows\[index\]返回表格指定的行所对应的属性

| cells | 返回该表格内所有的单元格组成的数组 |
| :--- | :--- |
| rowIndex | 返回该表格行在表格内的索引值 |
| sectionRowIndex | 返回该表格行在其所在元素\(tbody,thead等元素\)的索引值 |

> #### **通过cells\[index\]返回表格指定的列所对应的属性:**

| cellIndex | 返回该单元格在表格行内的索引值 |
| :--- | :--- |


![](/assets/kk.jpg)

```js
function updateCell(){
var row=document.getElementById("row").value;
var cell=document.getElementById("cell").value;
var t=document.getElementById("mytable");
t.rows[row-1].cells[cell-1].innerHTML=document.getElementById("course").value;
//t.rows.item(row-1).cells.item(cell-1).innerHTML=document.getElementById("course").value;
}
```



