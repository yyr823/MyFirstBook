### _git push_报错error: failed to push some refs to 'git@github.com

* [x] 原因： GitHub远程仓库中的README.md文件不在本地仓库中。

* [x] 解决办法：

```
$ git pull --rebase origin master //先拉下来，会自动合并的(pull=fetch+merge)
$ git push -u origin master //进行推送
```



