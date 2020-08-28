# git-workbook
Git 指令练习仓库

#### SSH 配置

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

#### 创建仓库

1. Clone Remote Repository With Https

指令：`git clone https://domain.com/user/repo.git`

例子：`git clone https://github.com/TimeAway/git-workbook.git`

2. Clone Remote Repository With SSH

指令：`git clone git@domanin.com:user/repo.git`

例子：`git clone git@github.com:TimeAway/git-workbook.git`

3. Create A New Local Repository
```
$ git init
``` 