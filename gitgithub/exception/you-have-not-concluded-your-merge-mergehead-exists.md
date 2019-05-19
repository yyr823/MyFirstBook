### fatal: You have not concluded your merge \(MERGE\_HEAD exists\)

* #### [参考链接](https://blog.csdn.net/feng2qing/article/details/56496441)
* #### **报错原因：**

* [x] **pull下来的代码自动合并失败。**

* > #### 从远程获取最新版本到本地有两种方式：
* #### `Git fetch`:只是从远程获取最新版本到本地,不会`merge`\(合并\)

```git
git fetch origin master           //从远程的origin的master主分支上获取最新版本到origin/master分支上
git log -p master..origin/master  //比较本地的master分支和origin/master分支的区别
git merge origin/master           //合并
```

* #### `Git pull`:从远程获取最新版本并`merge`\(合并\)到本地

```
 git pull origin master  //相当于进行了 git fetch 和 git merge两部操作
```

##### 实际工作中,可能`git fetch`更好一些, 因为在`merge`前,可以根据实际情况决定是否`merge`

* #### 解决方法：
* [x] ** 方法一:保留本地的更改,中止合并-&gt;重新合并-&gt;重新拉取**

```git
git merge --abort
git reset --merge
git pull
```

* [x] **方法二:舍弃本地代码,远端版本覆盖本地版本\(慎重\)**

```git
git fetch --all
git reset --hard origin/master
git fetch
```



