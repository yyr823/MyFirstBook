| 语法\(在git bash中操作\) | 描述 |
| :--- | :--- |
| \*_**git init**_ |  |
| git init | 初始化一个Git仓库 |
| git init \[program-name\] | 新建一个目录,将其初始化为git代码库 |
| \*_**git status**_ | 掌握仓库当前的状态\(还可以在分支合并冲突的时候提示哪个文件冲突\) |
| \*_**git diff**_ |  |
| git diff  fileName | 查看文件内容不同之处\(比较工作区和暂存区\[最后一次add\]的区别\) |
| git diff --cached \[fileName\] | 比较暂存区和版本库\(仓库分支里\[上次git commit 后的内容\]\)的区别 |
| git diff HEAD -- \[fileName\] | 比较工作区和版本库（最后一次commit）的区别 |
| \*_**git add**_ |  |
| git add \[ fileName\] | 把文件添加到暂存区\(表示添加新文件和编辑过的文件,不包括删除的文件\) |
| git add \[dir\] | 添加指定目录到暂存区,包括子目录 |
| git add . | 添加当前目录的所有文件到暂存区\(表示添加新文件和编辑过的文件,不包括删除的文件\) |
| git add -u | 表示添加编辑或者删除的文件,不包括新添加的文件 |
| \*_**git commit**_ |  |
| git commit -m '备注信息' | 告诉git把文件提交到仓库区 |
| git commit \[fileName1\] \[fileName2\] ... -m  '备注信息' | 暂存区的指定文件提交到仓库区 |
| git commit -a -m '备注信息' | 相当于git add . 与git commit –m '备注信息' 两句操作合并为一句进行使用 |
| \*_**git log**_ |  |
| git log -n | 查看最近n次的提交信息\(n=1 即最近一次的提交\) |
| git log | 显示从最近到最远的提交日志 |
| git log --pretty=oneline | 简化日志信息输出\(单行模式\) |
| git log --stat | 查看commit历史，以及每次commit发生变更的文件 |
| git log --graph --pretty=oneline  --abbrev-commit | 查看分支合并图 |
| \*_**git reset**_ |  |
| git reset  \[fileName\] | 重置暂存区的指定文件，与上一次commit保持一致，工作区不变 |
| git rest --hard | 重置暂存区与工作区，与上一次commit保持一致 |
| git reset --head HEAD^/HEAD~2 | 把当前最新的提交回退上一个版本/从当前版本回退两个版本 |
| git reset --hard  1094a\(commit id前几位\) | 指定回到所填写 的版本号处 |
| git reset HEAD \[fileName\] | 把暂存区的修改撤销（unstage），重新放回工作区 |
| \*_**cat \[fileName\]**_ | 查看文件内容 |
| \*_**git reflog**_ | 查看记录日志（命令历史） |
| \*_**git checkout**_ |  |
| git checkout  --  \[fileName\] | 把文件在工作区的修改/删除全部撤销 |
| git checkout . | 撤销工作区的全部修改\(未添加到暂存区:,撤销后回到与版本库一模一样的状态 已添加到暂存区并做了修改:回到最近一次commit/add时的状态 \) |
| git checkout -b \[branchName\] \[remote\]/\[branchName\] | 创建远程remote 下的分支到本地 |
| \*_** rm **_ |  |
| rm \[fileName\] | 删除工作区文件\(不会放进暂存区\) |
| git rm \[fileName\] | 从版本库删除该文件\(记得删除后进行提交\)会放进暂存区 |
| \*_**git remote**_ |  |
| git remote add origin\(可更改名字\)  url | 本地关联远程仓库 |
| git remote -v | 查看远程库的信息 |
| git remote add \[remote\] \[url\] | 增加一个新的远程仓库，并命名 \(一般是origin\) |
| git remote rm \[remote\] | 删除远程库 |
| \*_**git branch --set-upstream-to= \[remote\]/\[branchName\]  \[ branchName\]**_ | 创建本地分支和远程分支的链接关系 |
| \*_**git pull \[remote\] \[branchName\]**_ | 拉取远程分支 |
| \*_**git push**_ |  |
| git push -u \[remote\] master | 会把本地的master分支内容推送的远程新的master分支,还会把本地的master分支和远程的master分支关联起来\(git给远程库起的默认名称是origin\) |
| git push \[remote\] master | 将主分支推送到远程库 |
| git push \[remote\] \[branchName\] | 将\(\[branch\]\)分支推送到远程库 |
| git push \[remote\] --delete \[branchName\] | 删除远程分支 |
| git push \[remote\] \[tagName\] | 推送某个标签到远程 |
| git push \[remote\] --tags | 一次性推送全部尚未推送到远程的本地标签 |
| \*_**git clone url**_ | 从github上克隆一个本地库 |
| \*_**branch**_ |  |
| git checkout -b  branchName \[tagname\] | 创建分支并切换到该分支,同时指向某个tag |
| git branch \[branchName\] | 创建分支 |
| git checkout \[branchName\] | 切换到该分支下 |
| git branch | 查看当前所包含的分支 |
| git merge \[branchName\] | 合并指定分支到当前分支 |
| git_** merge **_--no-ff   \[branchName\] | 合并分支时禁用Fast forward |
| git branch -d \[branchName\] | 删除分支 |
| git branch -D \[branchName\] | 强制删除一个还没有合并（已经commit）的分支 |
| git branch -a | 列出所有本地分支和远程分支 |
| git branch -r | 列出所有远程分支 |
| \*_**git rebase**_ | 把本地未push的分叉提交整理成直线 |
| \*_**git stash**_ |  |
| git stash | 把当前工作现场'储藏起来',只能'储藏' git add过的文件 |
| git stash apply | 恢复工作现场\(stash内容并不删除\) |
| git stash drop | 删除stash 内容 |
| git stash pop | 恢复工作现场并删除stash内容 |
| git stash list | 查看stash 内容 |
| git stash apply stash@{0} | 指定恢复的stash |
| \*_** tag**_ |  |
| git tag  \[tagName\] | 新建一个标签,默认为HEAD |
| git tag  -a \[ tagName\]  -m '备注信息'  commit id | 给该提交id打一个带有说明的标签 -a 指定标签名 -m指定说明文字 |
| git tag | 查看所有标签 |
| git show \[tagName\] | 查看标签信息 |
| git tag -d \[tagName\] | 删除指定标签 |
| git push \[remote\] --delete \[tagName\] | 删除远程指定标签\(先删除本地标签\) |
| \*_**git config**_ |  |
| git config --list | 显示当前的Git配置 |
| git config user.name/user.email | 查看用户名/邮箱 |
| git config --global user.name \[username\]/user.email \[email\] | 设置全局用户名/邮箱 |
| git config --global color.ui true | git命令显示颜色 |
| git config --global alias.st/rh  status/'reset HEAD' | 配置别名 \(git st/rh fileName\) |
| \*_**git CHECK-IGNORE -v  \[fileName \]**_ | 检查为什么文件不能ADD,是否是因为定义的忽略规则 |
| \*_**git blame  \[fileName\]**_ | 查看文件是什么人在什么时间修改过 |
| \*_**git shortlog -sn**_ | 查看所有提交过的用户，按提交次数排序 |

文件名称：fileName

github/git上项目的路径\(git@server-name:path/repo-name.git\):url

分支名称:branchName

标签名称:tagName

git lg

```
git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"
```

git fetch \(取回远程仓库的变化，但并不会主动与本地分支合并\)

```
 //方法一 例子
  git fetch origin master //从远程的origin仓库的master分支下载代码到本地的origin master

  git log -p master.. origin/master//比较本地的仓库和远程参考的区别

  git merge origin/master//把远程下载下来的代码合并到本地仓库，远程的和本地的合并

  //方法二
  git fetch origin master:temp //从远程的origin仓库的master分支下载到本地并新建一个分支temp

  git diff temp//比较master分支和temp分支的不同

  git merge temp//合并temp分支到master分支

  git branch -d temp//删除temp
```



