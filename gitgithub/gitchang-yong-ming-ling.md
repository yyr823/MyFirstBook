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
|  |  |

文件名称+后缀：fileName

#### 



