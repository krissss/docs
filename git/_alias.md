## alias

[doc](https://git-scm.com/book/en/v2/Git-Basics-Git-Aliases)

通过命令创建 alias

`git config --global alias.co checkout`

`git config --global alias.merge-to "!f() { git checkout $1 && git merge $2 && git checkout -; }; f"`

通过配置文件修改 alias （个人目录下的.gitconfig文件）

```txt
[alias]
	co = checkout
	merge-to = "!f() { git co $2 && git pull && git co $1 && git pull && git merge $2; }; f"
	m2 = "!f() { git merge-to $1 $2; }; f"
	m235 = "!f() { git merge-to test-env/35 feature/#$1; }; f"
	m217 = "!f() { git merge-to test-env/17 feature/#$1; }; f"
```

以上alias 可以快使用如：

`git m2 test-env/35 feature/#14432` 等于 `git m235 14432`
