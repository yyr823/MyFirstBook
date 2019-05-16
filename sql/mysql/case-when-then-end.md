* 已知商品评论表如下图展示：

> #### ![](/assets/c1.png)**统计每种商品下的好坏留言的人数：**

* 思路：先进行商品分类--》case when then 进行评分的判定--》count统计数量。

* 代码如下：

```
 SELECT pro.pid,pro.pname, 
             COUNT(CASE WHEN p.prscore=5 THEN 1 END)best, 
             COUNT(CASE WHEN p.prscore=4 THEN 1 END)good,
             COUNT(CASE WHEN p.prscore=3 THEN 1 END)common, 
             COUNT(CASE WHEN p.prscore<=2 THEN 1 END)bad 
 FROM product_review p JOIN products pro ON p.pid =pro.pid   GROUP BY p.pid
```

* 效果显示：

![](/assets/c2.png)

