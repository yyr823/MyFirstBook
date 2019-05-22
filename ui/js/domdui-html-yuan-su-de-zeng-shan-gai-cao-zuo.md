#### ![](/assets/bo8.png)![](/assets/bo9.jpg)**为了动态地修改HTML元素,须先访问HTML元素。 DOM主要提供了两种方式来访问 HTML元素:**

* 根据 l D访问HTML元素一通过document对象调用getE l ementById\(\)方法来查找具有唯一id属性值的元素。

* 利用节点关系访问HTML元素。常用的属性和方法如下:

| parentNode | 返回当前节点的父节点 |
| :---: | :--- |
| previousSibling | 返回当前节点的前一个兄弟节点 |
| nextSibling | 返回当前节点的后一个兄弟节点 |
| childNodes | 返回当前节点的所有子节点 |
| firstChild | 返回当前节点的第一个子节点 |
| lastChild | 返回当前节点的最后一个子节点 |
| getElementsByTagName\(tagName\) | 返回当前节点的具有指定标签名的所有子节点 |
|  |  |

![](/assets/bo11.jpg)

* > #### DOM创建节点的方法:
* [x] **document.createElement\(Tag\),Tag必须是合法的HTML元素**

* > #### DOM复制节点的方法:
* [x] **节点cloneNode\(boolean deep\),当deep为true时,表示复制当前节点以及当前节点的全部后代节点\(深复制\)。为false时,只复制当前节点浅复制\)**

* > #### DOM添加、 删除节点的方法:

| appendChild\(newNode\) | 将newNode添加成当前节点的最后一个子节点 |
| :--- | :--- |
| insertBefore\(newNode,refNode\) | 在 refNode节点之前插入newNode节点 |
| replaceChild\(newNode,oldNode\) | 将ol dNode节点替换成newNode节点 |
| removeChild\(oldNode\) | 将oldNode子节点删除 |
|  |  |

* [x] **代码示例:**

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

> #### DOM为列表框、下拉菜单添加选项的方式

* [x] **创建选项除了使用前面所示一createElement方法之外, 还可以使用专门的构造器来构造一个选项出来 。 **

* [x] **语法如下:**

```
new Option(text,value,defaultSelected,selected)
```

* [x] **该构造器有4个参数**

| text | 该选项的文本、即该选项所呈现的”内容” |
| :--- | :--- |
| value | 选中该选项的值 |
| defaultSelected  | 设置默认是否显示该选项 |
| selected  | 设置该选项当前是否被选中 |

**提示:并不是每次构造函数都需指明4个参数,可以指明一个或者两个都可以\(浏览器都兼容\).**

* ** 添加创建好的选项至列表框或下拉菜单的方式**

* [x] 直接为&lt;select.../&gt;的指定选项赋值

**`列表框或下拉菜单对象. options[i] =创建好的opt i on对象`**

* **删除列表框或下拉菜单的选项的方法**

列表框或下拉菜单对象.remove\(index\)方法/对象.options\[index\]=null 删除指定项

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

> #### DOM动态添加删除表格内容所使用到的常用方法

| insertRow\(index\)  | 在指定索引位置插入一行 |
| :--- | :--- |
| createCaption\(\) | 为该表格创建标题 |
| createTFoot\(\) | 为该表格创建&lt;tfoot. .. /&gt;元素,假如已存在就返回现有的 |
| createTHead\(\) | 为该表格创建&lt;thead. .. /&gt;元素,假如已存在就返回现有的 |
| deleteRow\(index\)  | 删除表格中 i ndex索引处的行 |
| deleteCaption\(\) | 删除表格标题 |
| deleteTFoot\(\) | 从表格删除 tFoot元素及其内容 |
| deleteTHead\(\) | 从表格删除 tHead元素及其内容 |

* **给表格行创建,删除单元格的方法:**

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



