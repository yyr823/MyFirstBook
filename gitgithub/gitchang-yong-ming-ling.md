| 语法 | 描述 |
| :--- | :--- |
| git init | 初始化一个Git仓库 |
| git status | 掌握仓库当前的状态 |
| git diff  fileName | 查看文件内容不同之处\(比较工作区和暂存区\[最后一次add\]的区别\) |
| git diff --cached | 比较暂存区和版本库\(仓库分支里\[上次git commit 后的内容\]\)的区别 |
| git diff HEAD -- fileName | 比较工作区和版本库（最后一次commit）的区别 |
| git add fileName | 把文件添加到仓库 |
| git commit -m '备注信息' | 告诉git把文件提交到仓库 |
| git log | 显示从最近到最远的提交日志 |
| git log --pretty=oneline | 简化日志信息输出 |
| git reset --head HEAD^ | 把当前最新的提交回退上一个版本 |
| git reset --hard  1094a\(commit id前几位\) | 指定回到所填写 的版本处 |
| cat fileName | 查看文件内容 |
| git reflog | 查看记录日志（命令历史） |
| git checkout  --  fileName | 把文件在工作区的修改/删除全部撤销\(未添加到暂存区:_,_撤销后回到与版本库一模一样的状态     已添加到暂存区:回到最近一次commit/add时的状态 \) |
| git reset HEAD fileName | 把暂存区的修改撤销掉,重新放回工作区 |
| rm fileName | 删除工作区文件 |
| git rm fileName | 从版本库删除该文件\(记得删除后进行提交\) |
| git remote add origin  url | 本地关联远程仓库 |
| git checkout -b branchName origin/branchName | 创建远程origin下的分支到本地 |
| git branch --set-upstream-to= origin/branchName   branchName | 创建本地分支和远程分支的链接关系 |
| git pull | 拉取远程分支 |
| git push -u origin master | 会把本地的master分支内容推送的远程新的master分支,还会把本地的master分支和远程的master分支关联起来 |
| git clone url | 从github上克隆一个本地库 |
| git checkout -b  branchName | 创建分支并切换到该分支 |
| git branch branchName | 创建分支 |
| git checkout branchName | 切换到该分支下 |
| git branch | 查看当前分支 |
| git merge branchName | 合并指定分支到当前分支 |
| git merge --no-ff   branchName | 合并分支时禁用Fast forward |
| git branch -d branchName | 删除分支 |
| git rebase | 把本地未push的分叉提交整理成直线 |
| git log --graph --pretty=oneline --abbrev-commit | 查看分支合并图 |
| git stash | 把当前工作现场'储藏起来' |
| git stash apply | 恢复工作现场 |
| git stash drop | 删除stash 内容 |
| git stash pop | 恢复工作现场并删除stash内容 |
| git stash list | 查看stash 内容 |
| git stash apply stash@{0} | 指定恢复的stash |
| git branch -D branchName | 丢弃一个没有被合并过的分支 |
| git remote -v | 查看远程库的详细信息 |
| git tag  -a  tagName  -m '备注信息'  commit id | 给该提交id打一个带有说明的标签 -a 指定标签名 -m指定说明文字 |
| git tag | 查看所有标签 |
| git show tagName | 查看标签信息 |
|  |  |

文件名称+后缀：fileName

github/git上项目的路径\(git@server-name:path/repo-name.git\):url

分支名称:branchName

标签名称:tagName

#### 



