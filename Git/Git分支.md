分支中常用命令:

```bash
# 列出所有本地分支 
git branch

# 列出所有远程分支 
git branch -r

# 新建一个分支，但依然停留在当前分支
git branch [branch-name]

# 新建一个分支，并切换到该分支
git checkout -b [branch]

# 合并指定分支到当前分支
$ git merge [branch]

# 删除分支
$ git branch -d [branch-name]

# 删除远程分支
$ git push origin --delete [branch-name]
$ git branch -dr [remote/branch]

```

如果同一个文件在合并分支时都被修改了则会引起冲突:解决的办法是我们可以修改冲突文件后重新提交!选择要保留他的代码还是你的代码!

master主分支应该非常稳定,用来发布新版本, - -般情况下不允许在上面工作,工作一般情况下在新建的dev分支上工作,工作完后，比如上要发布,或者说dev分支代码稳定后可以合并到主分支master.上来。
