## git-commands

skillful at git

### 概念

- 工作区：（增删文件和内容）
- 暂存区：`git add 改动的文件名` 此次改动就放到了暂存区
- 本地仓库（本地）：`git commit 此次改动的描述` 此次改动就放到了本地仓库，每一个 commit 就是一个版本
- 远程仓库（远程）：`git push 远程仓库` 此次改动就放到了远程仓库
- commit-id：`git log` 输出提交的信息

### 展示帮助信息

    git help -g
    git help -a

### 回到远程仓库的状态

    git reset --hard origin/master

### 重设第一个 commit

也就是把所有的改动重新放回工作区，并清空所有的 commit 这样就可以重新开始第一个 commit 了

    git update-ref -d HEAD

### 强制提交

    git push -f <remote-name> <remote-branch>

### 展示工作区和暂存区的不同

输出工作区和暂存区的不同（哪些 add 了，哪些没有 add）

    git diff

展示本地仓库中任意两个 commit 中的文件变动

    git diff <commit-id> <commit-id></commit-id>

### 展示工作区、暂存区和本地仓库的不同（这个看着有点乱）

    git diff HEAD

### 快速切换到上一个分支（感觉还挺好用的）

    git checkout -

### 删除已经合并到 master 的分支

    git branch --merged master | grep -v '^\*\|  master' | xargs -n 1 git branch -d

### 展示本地分支关联远程仓库的情况

    git branch -vv

### 关联远程分支

关联之后，git branch -vv 就可以展示关联的远程分支名了，同时推送到远程仓库直接：git push，不需要指定远程仓库了。

    git push -u origin master

### 列出所有的远程分支（remote）

    git branch -r

### 列出本地和远程分支（all）

    git branch -a

### 查看远程分支和本地分支的对应关系（-a 信息已经够了）

    git remote show origin

### 远程删除了分支，本地也想删除

    git remote prune origin

### 创建并切换到本地分支

    git checkout -b <branch-name> origin/<branch-name>

### 删除本地分支

    git branch -d <branch-name>

### 删除远程分支

    git push origin --delete <branch-name>

### 重命名本地分支

    git branch -m <new-branch-name>

### 本地创建标签

    git tag <version-number>

默认 tag 是打在最近一次 commit 记录上，如果需要指定 commit 打 tag

    git tag -a <version-number> -m '描述' <commit-id>

### 推送标签到远程仓库

    git push origin <local-version-number>

一次性推送所有

    git push origin --tags

### 删除本地分支

    git tag -d <tag-name>

### 删除远程标签

需要先删除本地标签，再删除远程标签

    git push orgin :refs/tags/<tag-name>

### 切回到某个标签（只能 -b）

    git checkout -b <branch-name> <tag-name>

### 查看标签

    git tag

展示当前分支最近的 tag

    git describe --tags --abbrev=0

查看标签的详细信息

    git tag -ln

---

### 放弃工作区的修改（这个是神器）

    git checkout <file-name>

放弃所有更改

    git checkout .

### 以新增一个 commit 的方式还原某一个 commit 的修改

    git revert <commit-id></commit-id>

### 回到某个 commit 的状态，并删除后面的 commit

    git reset <commit-id>  #默认就是-mixed参数。

    git reset --mixed HEAD^  #回退至上个版本，它将重置HEAD到另外一个commit,并且重置暂存区以便和HEAD相匹配，但是也到此为止。工作区不会被更改。

    git reset --soft HEAD~3  #回退至三个版本之前，只回退了commit的信息，暂存区和工作区与回退之前保持一致。如果还要提交，直接commit即可

    git reset --hard <commit-id>  #彻底回退到指定commit-id的状态，暂存区和工作区也会变为指定commit-id版本的内容

### 修改上一个 commit 的描述

    git commit --amend

### 查看某段代码是谁写的

    git blame <file-name>

### 显示本地更新过 HEAD 的 git 命令记录

每次更新了 HEAD 的 git 命令比如 commit、amend、cherry-pick、reset、revert 等都会被记录下来（不限分支），就像 shell 的 history 一样，这样你就可以 reset 到任何一次更新了 HEAD 的操作之后，而不仅仅是回到当前分支下的某个 commit 之后的状态

    git reflog

### 修改作者名

    git commit --amend --author="GerritV<shiguangwei5@gmail.com>"

### 修改远程仓库的 url

    git remote set-url origin <URL>

### 增加远程仓库

    git remote add origin <remote-url>

### 列出所有的远程仓库

    git remote

### 查看两个星期内的改动

    git whatchanged --since="2 weeks ago"

### 把 A 分支的某一个 commit 放到 B 分支上

    git checkout <branch-name> && git cherry-pick <commit-id>

### 存储当前状态，但不用提交 commit

    git stash

### 存储当前状态，包括 untracked 的文件
    
    git stash -u

### 展示所有的 stashes

    git stash list

### 回到某个 stash 的状态

    git stash apply <stahs@{version}> // 这个 list 是栈

### 回到最后一个 stash，并删除这个 stash

    git stash pop