### layui 给数据表格加序号

* #### [原文链接](https://blog.csdn.net/qq_40319394/article/details/80657832)
* **第一种需求,只给当前页加序号**

```js
,cols: [[
    {field:'tourPlayerId', width:80, title: 'ID1', sort: true,fixed: 'left',}
    ,{field:'zizeng', width:80, title: '排名',fixed: 'left',templet: function (d) 
    {return d.LAY_TABLE_INDEX+1;}}
    ]]
```

**需注意:点击下一页时,只会重新从1开始排序**

* **第二种需求,包括分页的数据也加上序号\(连续性排序\)**

```js
,cols: [[
    {field:'tourPlayerId', width:80, title: 'ID1', sort: true,fixed: 'left',}
    ,{field:'zizeng', width:80, title: '排名',fixed: 'left',    type:'numbers'}
    ]]
```

**设定列类型。可选值有：normal\(常规列,无需设定\)、checkbox\(复选框列\)、space\(空列\)、numbers\(序号列\)**

**注意:该参数为 layui 2.2.0 新增。而如果是之前的版本,复选框列采用 checkbox:true、空列采用 space: true**

