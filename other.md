#### wc 命令，用于统计

```
wc index.php #依次输出 行数 字数 字节数 文件名

wc -l index.php #统计文件行数

wc -w index.php #统计文件字数

wc -c index.php #统计字节数
```

#### last 命令

```
last #显示最近登录的用户列表

last -6 #显示最近登录的 6 条登录信息

last -u nick #显示指定用户 nick 的登录信息
```

#### lastlog 命令

```
lastlog #显示最后登录的用户信息，内容为 用户名 终端 ip地址 登录时间，如果没有登录信息登录时间为 **Never logged in**

内容如下

tss                                        **Never logged in**
postfix                                    **Never logged in**
sshd                                       **Never logged in**
ntp                                        **Never logged in**
tcpdump                                    **Never logged in**
nscd                                       **Never logged in**
nick             pts/0    x.x.x.x   Sun May  6 16:06:39 +0800 2018


lastlog -t 2 #指定 2 天内的登录信息

lastlog -u nick #指定 nick 用户的登录信息
```

#### lastb 命令

```
sudo lastb #显示最近登录失败的用户，需要 root 权限

lastb -2 #显示 2 天内登录失败的用户
```

#### date 命令

```
date #输出系统时间与日期，世界标准时间（UTC）格式 Sun May  6 16:19:05 CST 2018

date +"%Y-%m-%d" #输出年月日

date +"%Y-%m-%d %H:%M.%S" #输出年月日时分秒
```

#### history 命令

```
history #显示执行过的命令，以列表显示

history 5 #只显示最近执行过的 5 条命令

history -c #清除执行过的命令
```

#### fc 命令

```
fc -l #显示执行过的命令

fc -l 2 #显示最近执行的 2 条命令

fc -ln #显示执行过的命令，不显示编号

fc 588 #默认使用 vim 打开，编辑编号为 588 的命令，如果有修改，保存退出之后自动执行
``` 