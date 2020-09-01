# git-workbook
Git 指令练习仓库

### 目录
- [专用名词](#专用名词)
- [Git配置](#Git配置)
- [SSH配置](#SSH配置)
- [创建仓库](#创建仓库)
- [工作区](#工作区)
- [暂存区](#暂存区)
- [本地仓库](#本地仓库)
- [版本分支](#版本分支)
- [标签](#标签)
- [查看信息](#查看信息)
- [远程同步](#远程同步)
- [撤销操作](#撤销操作)
- [其他操作](#其他操作)

### 专用名词
- Ignored       忽略区
- Untracked     未跟踪区
- WorkSpace     工作区
- Index/Stage   暂存区
- Repository    本地仓库
- Remote        远程仓库

### Git配置

#### 1. 查看当前Git配置
```
$ git config --list
```

#### 2. 编辑Git配置文件
```
$ git config -e <--global>
```

#### 3. 设置提交代码的用户信息
```
$ git config <--global> user.name 'user'

$ git config <--global> user.email 'email address'
```

### SSH配置

#### 1. 打开终端，查看是否已配置SSH
```
$ cd ~/.ssh
```

#### 2. 若已配置可看到目录下包含如下文件，其中`id_rsa`是私钥，`id_rsa.pub`是公钥
```
id_rsa
id_rsa.pub
known_hosts
```

#### 3. 若未生成，则执行公钥和私钥的生成命令，并连按3下回车键
```
$ ssh-keygen -t rsa
```

#### 4. 执行查看公钥指令，复制此公钥到对应的仓库中生成密钥即可
```
$ cat ~/.ssh/id_rsa.pub
```

### 创建仓库

#### 1. 使用 Https 克隆远程仓库

指令：`git clone https://domain.com/user/repo.git`

例子：`git clone https://github.com/TimeAway/git-workbook.git`

#### 2. 使用 SSH 克隆远程仓库

指令：`git clone git@domain.com:user/repo.git`

例子：`git clone git@github.com:TimeAway/git-workbook.git`

#### 3. 当前目录下创建本地仓库（新建目录）
```
$ git init <project name>
``` 

#### 4. 本地仓库与远程仓库关联，并推送到远程仓库

指令：
```
$ git remote add origin git@domain.com:user/repo.git

$ git push -u origin master
```

例子：
```
$ git remote add origin git@github.com:TimeAway/git-workbook.git
```

### 工作区

#### 1. 查看本地工作区变化文件状态
```
$ git status
```

#### 2. 对比文件前后变化
```
$ git diff
```

### 暂存区

#### 1. 添加指定文件到暂存区
```
$ git add <file1> <file2> ...
```

#### 2. 添加指定目录到暂存区，包括子目录
```
$ git add <dir1> <dir2>
```

#### 3. 添加当前目录的所有文件到暂存区（包括修改及未跟踪文件，但不包括删除）
`-u` 表示将**已跟踪**的修改和删除的文件添加到暂存区，不包括新增的未跟踪文件

`-A` 表示将所有**已跟踪**的修改和删除及新增的**未跟踪**文件添加到暂存区
```
$ git add <-u> <-A> .
```

#### 4. 分次提交一个文件的多处变化
```
$ git add -p
```

#### 5. 删除工作区文件，并将此删除放入暂存区
```
$ git rm <file1> <file2> ...
```

#### 6. 强制删除文件，如果是新增文件会被从暂存区与工作区清除。如果是已存在文件，会被删除并放入暂存区
```
$ git rm -f <file>
```

#### 7. 停止追踪指定文件，但会留在工作区
```
$ git rm --cached <file>
```

#### 8. 改名文件，并且将这个改名放入暂存区
```
$ git mv <file-original> <file-renamed>
```

### 本地仓库
#### 1. 提交暂存区到本地仓库
```
$ git commit -m <message>
```

#### 2. 提交暂存区指定文件到本地仓库
```
$ git commit <file1> <file2> -m <message>
```

#### 3. 提交自上次commit之后的变化，直接到仓库区
```
$ git commit -a
```

#### 4. 提交时显示所有的diff信息
```
$ git commit -v
```

#### 5. 使用新的commit替代上一次提交，如果代码无变化则改写上一次commit的提交信息（可忽略）
```
$ git commit --amend -m <message>
```

#### 6. 重做上一次commit，包括指定文件的新变化
```
$ git commit --amend <file1> <file2>
```

### 版本分支
#### 1. 列出所有的本地分支
`-r` 表示列出所有远程分支

`-a` 表示列出所有本地分支与远程分支
```
$ git branch <-r> <-a>
```

#### 2. 新建本地分支，但依然停留在当前分支
```
$ git branch <branch-name>
```

#### 3. 新建本地分支，并切换到分支
```
$ git branch -b <branch-name>
```

#### 4. 新建本地分支，并指向指定的commit
```
$ git branch <branch-name> <commit>
```

#### 5. 新建本地分支，并与指定的远程分支建立追踪关系
```
$ git branch --track <branch-name> <remote-branch-name>
```

#### 6. 切换本地分支，并更新工作区
```
$ git checkout <branch-name>
```

#### 7. 切换到上一个分支
```
$ git checkout -
```

#### 8. 让本地分支与指定远程分支之间建立追踪关系
```
$ git branch --set-upstream <branch-name> <remote-branch-name>
```

#### 9. 切换到远程分支并创建本地分支
```
$ git branch -b <branch-name> origin/<remote-branch-name>
```

#### 10. 合并指定分支到当前分支
```
$ git merge <branch-name>
```

#### 11. 选择一个commit，合并到当前分支（也可直接指定分支，默认为该分支的最后一次commit）
```
$ git cherry-pick <commit>

$ git cherry-pick <branch-name>
```

#### 12. 解决cherry-pick冲突并继续
```
$ git cherry-pick --continue
```

#### 13. 取消当前的cherry-pick
```
$ git cherry-pick --abort
```

#### 14. 删除本地分支（该分支需要已被合并）
```
$ git branch -d <branch-name>
```

#### 15. 强制删除本地分支
```
$ git branch -D <branch-name>
```

#### 16. 删除远程分支
```
$ git push origin --delete <branch-name>

$ git branch -dr <remote/branch>
```

### 标签
#### 1. 列出所有标签
```
$ git tag
```

#### 2. 新建tag, 在当前commit
```
$ git tag <tag-name>
```

#### 3. 新建tag，在指定commit
```
$ git tag <tag-name> <commit>
```

#### 4. 删除本地tag
```
$ git tag -d <tag-name>
```

#### 5. 删除远程tag
```
$ git push origin :refs/tags/<tag-name>
```

#### 6. 查看tag信息
```
$ git show <tag-name>
```

#### 7. 提交指定tag
```
$ git push <remote> <tag-name>
```

#### 8. 提交所有tag
```
$ git push <remote> --tags
```

#### 9. 新建一个分支，指向某个tag
```
$ git checkout -b <branch-name> <tag-name>
```

### 查看信息
#### 1. 显示有变更的文件
```
git status
```

#### 2. 显示当前分支的版本历史
```
git log
```

#### 3. 显示当前分支的版本历史，及修改的文件
```
git log --stat
```

#### 4. 根据关键词，搜索提交历史
```
git log -S <keyword>
```

#### 5. 显示某个commit之后的所有commit提交信息，每个message占据一行
```
$ git log <tag-name> HEAD --pretty=format:%s
```

#### 6. 显示某个commit之后的所有变动，其"提交说明"必须符合搜索条件
```
$ git log <tag-name> HEAD --grep feature
```

#### 7. 显示某个文件的版本历史，包括文件改名
```
$ git log --follow <file>
$ git whatchanged <file>
```

#### 8. 显示指定文件相关的每一次diff
```
$ git log -p <file>
```

#### 9. 显示过去5次提交
```
$ git log -5 --pretty --oneline
```

#### 10. 显示所有提交过的用户，并按提交次数排序
```
$ git shortlog -sn
```

#### 11. 显示指定文件什么人在何时修改过
```
$ git blame <file>
```

#### 12. 显示暂存区与工作区的差异
```
$ git diff
```

#### 13. 显示暂存区与上一个commit的差异
```
$ git diff --cached <file>
```

#### 14. 显示工作区与当前分支最新commit之间的差异
```
$ git diff HEAD
```

#### 15. 显示两次提交之间的差异
```
$ git diff <first-commit> <second-commit>
```

#### 16. 显示今天写了多少代码
```
$ git diff --shortstat '@{0 day ago}'
```

#### 17. 显示某次提交的元数据和内容变化
```
$ git show <commit>
```

#### 18. 显示某次提交发生变化的文件
```
$ git show --name-only <commit>
```

#### 19. 显示某次提交，某个文件的内容
```
$ git show <commit>:<filename>
```

#### 20. 显示当前分支的最近几次提交
```
$ git reflog
```

### 远程同步
#### 1. 拉取远程仓库最新内容到本地，需手动合并
```
$ git fetch <remote>
```

#### 2. 拉取远程仓库最新内容到本地，并与本地分支合并
```
$ git pull <remote> <branch-name>
```

#### 3. 拉取远程仓库最新内容到本地，并与本地分支合并，但是不会生成merge commit
```
$ git pull <remote> <branch-name> --rebase
```
简写
```
$ git pull --rebase
```
#### 4. 显示所有的远程仓库
```
$ git remote -v
```

#### 5. 增加一个新的远程仓库，并命名
```
$ git remote add <shortname> <url>
```

#### 6. 上传本地分支到远程仓库
```
$ git push <remote> <branch-name>
```

#### 7. 强行推送当前分支到远程仓库，即使有冲突
```
$ git push <remote> --force
```
简写
```
$ git push
```

#### 8. 强行推送当前分支到远程仓库，即使有冲突
```
$ git push <remote> --force
```

#### 9. 推送所有分支到远程仓库
```
$ git push <remote> --all
```

### 撤销操作

#### 1. 将工作区文件（非暂存区）撤销修改，包括删除
```
$ git restore <file>
```

#### 2. 将暂存区文件恢复到工作区，包括删除，不会更改文件
```
$ git restore --staged LICENSE
```

#### 3. 重置工作区/暂存区的某个文件，与某次commit保持一致
```
$ git checkout <commit> <file>
```

#### 4. 将暂存区文件恢复到工作区，包括删除，不会更改文件
```
$ git reset <file>
```

#### 5. 重置暂存区与工作区，与上一次的commit保持一致（所有修改的文件都会被重置，暂存区与工作区会被清空）
```
$ git reset --hard
```

#### 6. 将所有暂存区文件恢复到工作区中
```
$ git reset --soft
```

#### 7. 重置当前分支的指针为指定commit，同时重置暂存区，但工作区不变
```
$ git reset <commit>
```

#### 8. 置当前分支的HEAD为指定commit，同时重置暂存区和工作区，与指定commit一致
```
$ git reset --hard <commit>
```

#### 9. 重置当前HEAD为指定commit，但保持暂存区和工作区不变
```
$ git reset --soft <commit>
```

#### 10. 新建一个commit，用来撤销指定commit，后者的所有变化都将被前者抵消，并且应用到当前分支
```
$ git revert <commit>
```

#### 11. 将本地修改保存起来，并且将当前代码切换到HEAD上
```
$ git stash
```

#### 12. 恢复上次保存的文件到工作区
```
$ git stash pop
```

### 其他操作
#### 1. 生成一个可供发布的压缩包
```
$ git archive
```