# git-workbook
Git 指令练习仓库

### 专用名词
- WorkSpace     工作区
- Index/Stage   暂存区
- Repository    本地仓库
- Remote        远程仓库

### Git 配置

1. 查看当前Git配置
```
$ git config --list
```

2. 编辑Git配置文件
```
$ git config -e <--global>
```

3. 设置提交代码的用户信息
```
$ git config <--global> user.name 'user'

$ git config <--global> user.email 'email address'
```

### SSH 配置

1. 打开终端，查看是否已配置SSH
```
$ cd ~/.ssh
```

2. 若已配置可看到目录下包含如下文件，其中`id_rsa`是私钥，`id_rsa.pub`是公钥
```
id_rsa
id_rsa.pub
known_hosts
```

3. 若未生成，则执行公钥和私钥的生成命令，并连按3下回车键
```
$ ssh-keygen -t rsa
```

4. 执行查看公钥指令，复制此公钥到对应的仓库中生成密钥即可
```
$ cat ~/.ssh/id_rsa.pub
```

### 创建仓库

1. 使用 Https 克隆远程仓库

指令：`git clone https://domain.com/user/repo.git`

例子：`git clone https://github.com/TimeAway/git-workbook.git`

2. 使用 SSH 克隆远程仓库

指令：`git clone git@domain.com:user/repo.git`

例子：`git clone git@github.com:TimeAway/git-workbook.git`

3. 当前目录下创建本地仓库（新建目录）
```
$ git init <project name>
``` 

4. 本地仓库与远程仓库关联，并推送到远程仓库

指令：
```
$ git remote add origin git@domain.com:user/repo.git

$ git push -u origin master
```

例子：
```
$ git remote add origin git@github.com:TimeAway/git-workbook.git
```