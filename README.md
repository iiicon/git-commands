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

    git update-ref -d HEAD

