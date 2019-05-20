###  获取子节点所有父节点的name的拼接

* #### [原文链接](https://www.cnblogs.com/liyang19910805/p/5806155.html)

```js
//获取子节点，所有父节点的name的拼接字符串
function getFilePath(treeObj){
if(treeObj==null)return "";
var filename = treeObj.name;
var pNode = treeObj.getParentNode();
if(pNode!=null){
filename = getFilePath(pNode) +">"+ filename;
}
return filename;
}
```





