![](/assets/bo8.png)![](/assets/bo9.jpg)![](/assets/bo10.png)![](/assets/bo11.png)![](/assets/bo11.jpg)

![](/assets/kk1.jpg)**代码示例:**

```html
<!DOCTYPE html>
<html>

    <head>
        <meta charset="UTF-8">
        <title></title>
        <script type="text/javascript">
            var city = document.getElementById("city");

            function create() {
                var element = document.createElement("li");//ie不支持
                element.innerHTML = "南京";
                city.appendChild(element);
                //city.firstChild.nextSibling --><li>北京</li>
                //city.insertBefore(element,city.firstChild.nextSibling);
                //city.replaceChild(element,city.firstChild.nextSibling)

            }

            function copy() {
                var element = city.firstChild.nextSibling.cloneNode(true);
                //true深复制(后代元素也会复制) false浅复制 只复制当前元素
                city.appendChild(element);
            }

            function del() {
                var element = city.firstChild.nextSibling;
                city.removeChild(element);
            }
        </script>
    </head>

    <body>
        <ul id="city">
            <li>北京</li>
            <li>上海</li>
        </ul>
        <input type="button" value="创建复制替换节点" onclick="create()" />
        <input type="button" value="复制节点" onclick="copy()" />
        <input type="button" value="删除节点" onclick="del()" />

    </body>

</html>
```

![](/assets/K5.png)提示:并不是每次构造函数都需指明4个参数,可以指明一个或者两个都可以\(浏览器都兼容\).

![](/assets/K6.png)

* 删除列表框或下拉菜单的选项的方法

  ```
   列表框或下拉菜单对象.remove\(index\)方法/对象.options\[index\]=null 删除指定项
  ```

```js
<!DOCTYPE html>
<html>

    <head>
        <meta charset="UTF-8">
        <title></title>
        <script type="text/javascript">
            function createSelect() {
                var element = document.createElement("select");
                for(var i = 0; i < 10; i++) {
                    var op = new Option("新增的选项" + i, i);
                    element.options[i] = op;
                }
                element.size = 5; //一次性显示5个
                element.id = "city"; //设置id属性
                document.getElementById("test").appendChild(element);
            }

            function delOne() {
                var city = document.getElementById("city");
                var len = city.options.length;
                if(len > 0) {
                    city.remove(len - 1);
                    //city.options[len-1]=null;
                }

            }

            function delAll() {
                var city = document.getElementById("city");
                var len = city.options.length;
                if(len > 0) {
                    city.options.length = 0;
                }
            }
        </script>
    </head>
    <body id="test">

        <input type="button" value="创建一个城市列表" onclick="createSelect()" />
        <input type="button" value="一条条删除列表框内容" onclick="delOne()" />
        <input type="button" value="一次性清空列表框内容" onclick="delAll()" />
    </body>
</html>
```

![](/assets/k7.png)

* 给表格行创建,删除单元格的方法:

| insertCell\(index\) | 在index处创建一个单元格,返回新创建的单元格 |
| :--- | :--- |
| deleteCell\(index\) | 删除某行在index索引处的单元格 |

```js
<!DOCTYPE html>
<html>

    <head>
        <meta charset="UTF-8">
        <title></title>
        <script type="text/javascript">
            function createTable() {
                var b = document.getElementById("test");
                var t = document.createElement("table");
                t.border = "1";
                t.id = "mytable";
                var caption = t.createCaption();
                caption.innerHTML = "我的表格";
                for(var i = 0; i < 5; i++) {
                    var tr = t.insertRow(i);
                    for(var j = 0; j < 4; j++) {
                        var td = tr.insertCell(j);
                        td.innerHTML = "单元格" + i + j;
                    }
                }
                b.appendChild(t);
            }

            function delLastRow() {
                var t = document.getElementById("mytable");
                var rows = t.rows;
                if(rows.length > 0) {
                    t.deleteRow(rows.length - 1);
                }

            }

            function delLastCell() {
                var t = document.getElementById("mytable");
                var rows = t.rows;
                if(rows.length > 0) {
                    var lastRow = t.rows[t.rows.length - 1];
                    var len = lastRow.cells.length;
                    if(len > 0) {
                        lastRow.deleteCell(len - 1);
                    }
                }

            }
        </script>
    </head>

    <body id="test">

        <input type="button" value="创建一个5行4列的表格" onclick="createTable()" />
        <input type="button" value="删除最后一行" onclick="delLastRow()" />
        <input type="button" value="删除最后一个单元格" onclick="delLastCell()" />

    </body>

</html>
```



