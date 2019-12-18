#### Git 版本控制器

__配置__

```
git config --list  #查看全局配置的信息

git config --global -l #查看全局配置

git config --system -l #查看系统配置

git config --local -l  #查看本地仓库配置

git config --global user.name Nick #设置用户名

git config --global user.email nick_php@163.com #设置邮箱

git config --global log.date format:'%Y-%m-%d %H:%M:%S' #时间显示格式修改

git config --global core.ignorecase false #配置文件目录区分大小写

git config --global core.editor vim #配置 vim 为编辑器

git config --global color.ui true #配置高亮

git config --global merge.tool vimdiff #配置差异分析工具

git help config #获取帮助信息
```

__快捷别名__

```
alias gs='git status'
alias gm='git merge'
alias gtag='git tag'
alias gl="git log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit -- | less"
alias gb='git branch'
alias gpull='git pull'
alias gpush='git push'
alias ga='git add -A'
alias gc='git commit -m'
alias gam='git commit -am'
alias gcheckout='git checkout'
alias glt='git describe --tags' #最新的 tag 名称，提交次数
```

__普通操作__

```
git status #查看已添加到暂存区文件状态

git diff #查看未添加暂存区文件状态

git add file #添加文件

git add . #添加当前目录下所有文件到版本库

git add -A #添加所有文件到版本库

git commit -m '注释' #提交

git commit -am '提交信息' #添加并提交信息

git commit --amend #修改最近一次的 commit 信息

git blame filename #查看文件修改记录

git push #推送到仓库

git pull #拉取当前分支仓库最新代码

git pull dev #拉取指定分支的代码与本地分支合并

git reset --hard #回滚到上版本

git reset --hard af442cb672b02cdfca1fcb #回滚到指定的版本

git reset --hard origin/master #将本地代码重置和远程仓库代码一致，避免产生一个新个合并日志

git reset --hard origin/api #将本地代码重置与远程仓库指定分支一致，避免产生一个新个合并日志

git revert af442cb67 #回退到某个提交的代码，新增一个 commit

git checkout . #恢复暂存区的所有文件到工作区

git checkout file #恢复暂存区的指定文件到工作区

git checkout af442cb672b02cdfca1fcb index.php 恢复某个 commit 的指定文件到暂存区和工作区

git rebase -i af442cb672 将多个已提交未推送的 commit 合并成一个，把 pick 改成 s 保存之后修改提交信息即可

git rebase --abort 撤销合并

```

__新建仓库__

```
mkdir www && cd www

git init #初始化

git status #查看文件状态

git add file #.或*代表全部添加

git commit -m "message"#此处注意乱码

git remote add origin git@github.com:username/project.git #关联远程仓库

git push -u origin master #第一次推送文件到远程仓库
```

__克隆仓库__

```
git clone https://github.com/Nick233333/gitbook.git #克隆远程仓库

git clone https://github.com/Nick233333/gitbook.git linux #克隆并指定目录名称
```

__日志__

```
git log #查看提交日志

git reflog #查看提交日志 git reset 回滚版本依然有日志，可以撤销回滚

git log --pretty=oneline #单行显示提交日志

git log --author=nick #查看指定用户的日志

git log -p filename #查看文件每次提交的修改部分
```

__分支__

```
git branch #查看本地分支

git branch -r #查看远端分支

git branch -a #查看所有分支

git branch test #新建 test 分支

git checkout -b dev ##新建 dev 分支并切换

git checkout - #切换到上一个分支

git checkout -b test dev #基于 dev 新建 test 分支，并切换

git merge test #将test分支合并到当前分支

git branch -m old new #重命名分支

git branch -M old new #强制重命名分支

git push origin branch #推送分支到远程

git branch -d branch #删除本地分支

git branch -D branch #强制删除本地分支(当分支内容有修改并且已经 commit 时，分支没有合并，需要强制删除)

git push origin :branch #删除远程分支

git branch -r -d branch #删除远程分支，没有执行此命令 git branch-r 还是能看到远程分支

```

__标签__

```
git tag #列出现有标签

git tag v0.1#新建标签

git tag -a v0.1 -m 'my version 1.4'#新建带注释标签

git checkout tagname #切换到标签

git push origin v1.5 #推送分支到源上

git push origin --tags #一次性推送所有分支

git tag -d tag #删除本地 tag

git push origin :tag #删除远程 tag
```

__关联远程仓库__

```
git remote -v #查看全部远程仓库

git remote add origin https://github.com/Nick233333/gitbook.git #添加本地仓库与远程仓库关联

git remote rename origin github #重命名

git remote remove origin #取消与远程仓库关联

```

__暂存代码__

```
git stash #将本地修改代码暂存

git stash save 'message' #暂存代码并添加备注

git stash pop #把最近的暂存代码还原

git stash pop stash@{0} #还原指定 id 的暂存代码

git stash list #查看暂存代码列表

git stash drop #删除最近的暂存代码

git stash drop stash@{0} #删除指定 id 的暂存代码

git stash clear #清空所有暂存代码
```

__实用不常用命令__

```
git shortlog -sn #查看成员提交次数

git whatchanged --since='2 weeks ago' #查看指定时间的提交记录

git diff --name-only --diff-filter=U | uniq  | xargs $EDITOR #查看所有冲突文件

#删除最近一次提交中文件并修改提交信息
git rm —-cached file_name 
git commit —-amend
```