# git-workbook
Git 指令练习仓库

### 专用名词
- Ignored       忽略区
- Untracked     未跟踪区
- WorkSpace     工作区
- Index/Stage   暂存区
- Repository    本地仓库
- Remote        远程仓库

### Git 配置

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

### SSH 配置

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

#### 9. 将工作区文件（非暂存区）撤销修改，包括删除
```
$ git restore <file>
```

#### 10. 将暂存区文件恢复到工作区，包括删除，不会更改文件
```
$ git restore --staged LICENSE
```
