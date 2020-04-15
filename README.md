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

    测试tag

## rebase

## test reverse