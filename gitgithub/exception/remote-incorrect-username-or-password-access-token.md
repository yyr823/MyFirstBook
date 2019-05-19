### remote: Incorrect username or password \( access token \)

* #### [**原文链接**](https://blog.csdn.net/mmyhs/article/details/81589419)
* #### 异常

```git
git push origin ionic-001
remote: Incorrect username or password ( access token )
fatal: Authentication failed for 'https://gitee.com/yyr/demo.git/'
```

* #### 原因:

* [x] 由于之前重置了Git账户的密码，忘记修改计算机的凭据导致这个问题的出现。

* #### 解决方案:
* [x] **打开电脑的控制面板–&gt;用户账户–&gt;管理Windows凭据**

![](https://img-blog.csdn.net/20180811181230594?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L21teWhz/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70 "这里写图片描述")  
![](https://img-blog.csdn.net/20180811181239257?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L21teWhz/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70 "这里写图片描述")  
![](https://img-blog.csdn.net/20180811181250203?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L21teWhz/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70 "这里写图片描述")

* [x] **找到普通凭据中自己的账号信息，选择编辑，填入正确的用户名和密码，最后点击保存即可。**

![](https://img-blog.csdn.net/20180811181259749?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L21teWhz/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70 "这里写图片描述")

* [x] **最后重新使用git的push指令，成功将代码提交。**

![](https://img-blog.csdn.net/20180811181310777?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L21teWhz/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70 "这里写图片描述")

