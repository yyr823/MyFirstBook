### git push origin与git push -u origin master的区别

* #### [原文链接](https://www.cnblogs.com/zhouj850/p/7260558.html)
* **`$ git push origin`** 上面命令表示，将当前分支推送到origin主机的对应分支。

  如果当前分支只有一个追踪分支，那么主机名都可以省略。

* **`$ git push -u origin master `**如果当前分支与多个主机存在追踪关系，那么这个时候-u选项会指定一个默认主机,将本地的master分支推送到origin主机，同时指定origin为默认主机，后面就可以不加任何参数使用git push了。

*  不带任何参数的git push，默认只推送当前分支，这叫做simple方式。此外，还有一种matching方式，会推送所有有对应的远程分支的本地分支。Git 2.0版本之前，默认采用matching方法，现在改为默认采用simple方式。



