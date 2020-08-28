# git-workbook
Git 指令练习仓库

> 1.SSH 配置

打开`git bash`

---

使用`cd ~/.ssh` 查看是否已经配置SSH，已配置可看到目录下包含如下文件，
```
id_rsa
id_rsa.pub
known_hosts
```
其中`id_rsa`是私钥，`id_rsa.pub`是公钥。

---

如果未生成，则执行公钥和私钥的命令，并连按3下回车键
```
ssh-keygen -t rsa
```

---

执行查看公钥指令，复制此公钥到对应的仓库中生成密钥即可
```
cat ~/.ssh/id_rsa.pub
```

> 2.创建仓库

- Clone Remote Repository With Https

指令：`git clone https://domain.com/user/repo.git`

例子：`git clone https://github.com/TimeAway/git-workbook.git`

- Clone Remote Repository With SSH

指令：`git clone git@domanin.com:user/repo.git`

例子：`git clone git@github.com:TimeAway/git-workbook.git`

- Create A New Local Repository
```git
git init
``` 