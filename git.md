#### Git 版本控制器

__配置__

```
git config --list  #查看配置的信息

git config --global user.name Nick #设置用户名

git config --global user.email nick_php@163.com #设置邮箱

git help config #获取帮助信息
```

__普通操作__

```
git status #查看已添加到暂存区文件状态

git diff #查看未添加暂存区文件状态

git add file #添加文件

git add . #添加当前目录下所有文件到版本库

git add -A #添加所有文件到版本库

git commit -m '注释' #提交

git push #推送到仓库

git pull #拉取当前分支仓库最新代码

git pull dev #拉取指定分支的代码与本地分支合并

git reset --hard #回滚到上版本

git reset --hard af442cb672b02cdfca1fcb #回滚到指定的版本

git checkout . #恢复暂存区的所有文件到工作区

git checkout file #恢复暂存区的指定文件到工作区

git checkout af442cb672b02cdfca1fcb index.php 恢复某个 commit 的指定文件到暂存区和工作区

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

git checkout -b test dev #基于 dev 新建 test 分支，并切换

git merge test #将test分支合并到当前分支

git branch -m old new #重命名分支

git push origin branch #推送分支到远程

git branch -D branch #删除本地分支

git push origin :branch #删除远程分支

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