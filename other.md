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

#### echo 命令

```
echo hello linux #输出字符串

echo $my_name #输出变量值
```

#### time 命令

```
time ls #统计执行命令的时间

real	0m0.002s #命令执行开始到结束的时间
user	0m0.002s #进程花费在用户模式中的时间
sys	 0m0.000s #在内核模式中的时间

/usr/bin/time -o output.log ls #将执行时间写入文件日志

/usr/bin/time -ao outfile.txt ls #以追加的形式将执行时间写入日志文件
```

补充：`-a` 选项必须在 `-o` 前面，否则执行不成功

#### login 命令

```
login nick #当前用户切换到 nick 登录
```

#### logout 命令

```
logout #以当前用户退出登录
```

#### exit 命令

```
exit #退出登录或登录当前 shell 脚本
```

#### clear 命令

```
clear #清除屏幕内容
```

#### alias 命令

```
alias gs="git status" #给  git status 起别名为 gs，仅在当前环境生效，关闭终端或退出登录以后无效，一般配置在当前 shell 的配置文件中
```

#### unalias 命令

```
unadlias gs #取消命令别名
```

#### type 命令

```
type pwd #查看命令的类型
```


#### w 命令

```
w #查看当前登录系统的用户
```

#### mesg 命令

```
mesg y #允许终端接收信息

mesg n #禁止终端接收信息
```

#### write 命令

```
write root #向 `root` 用户发送消息，实时的，用户必须登录服务器状态并且 `mesg` 设置为 `y` 才可以接收到，输入信息之后按 `control +d`  
```

#### wall 命令

```
wall #向所有在线的用户发送消息，输入信息之后按 `control +d` 发送，`mesg` 设置为 `y` 才可以接收到
```

#### sort 命令

```
ls /usr | sort #排序
```

#### nohup 命令

```
nohup node app.js & #将执行的结果不显示并在后台运行，默认会在执行命令当前目录插件 nohup.out ，如果 nohup.out 文件没有写入权限，会在 ~ 目录下新建

nohup node app.js > demo.txt 2>&1 & #同上，指定写入文件名
```

#### tree 命令

```
tree /usr/local #以树状形式显示指定路径的目录和文件内容

tree -d /usr/local #以树状形式显示指定路径目录内容
```

#### ln 命令

```
ln -s 目标文件 软连接

ln -s /usr/local/php/bin/php /usr/local/bin/php #创建软连接，软连接被删除并不会影响源文件，源文件被删除软连接失效，只有文件才可以设置软连接，类似 Windows 系统的快捷方式
```

#### scp 命令

```
scp demo.php username@ip:path #将本地文件复制在远程服务器

scp -r dirname username@ip:path #将本地命令复制到远程服务器

scp [-P 端口号] xxx username@ip:path #指定端口号

scp username@ip:path/filename ./ #将远程服务器上的文件复制到本地

scp -r username@ip:path/dirname ./ #将远程服务器上的目录复制到本地

scp [-P 端口号] [-r] username@ip:path/ ./
```

补充：`-P` 指定端口，`-r` 递归

#### source 命令

```
source .zshrc #加载配置

source demo.sh #运行 shell 脚本
```

#### ab 命令

```
ab -c 100 -n 200 'url' #压力测试
```

补充：`c` 代表并发数量 `n` 代表请求数量

#### yes 命令

```
yes #不指定输出内容默认输出 y

yes xxx #不断输出指定内容
```

#### chsh 命令

```
chsh -l #查看系统 shell ，相当于 cat /etc/shells

chsh -s /bin/zsh #更改当前用户的 shell ，更改完之后要重新登录才生效
```

补充：`Ubuntu` 系统没 `-l` 选项

#### nmap 命令

```
nmap -sS -P0 -sV -O ip #查看主机系统信息
```

#### sqlmap 命令

```

```



