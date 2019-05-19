![](/assets/J2.png)![](/assets/J3.png)**案例:**

![](/assets/微信图片_20190519123002.jpg)![](/assets/J5.png)案例:

![](/assets/微信图片_20190519132005.jpg)![](/assets/微信图片编辑_20190519132517.jpg)通过cells\[index\]返回表格指定的列所对应的属性:

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



