#### uptime 命令

```
uptime #显示信息依次为：当前时间、系统运行时间、目前登录用户、系统在 1 分钟、5 分钟和 15 分钟内的负载。
```

#### free 命令

```
free -m #以 mb 统计系统内存

free -k #以 kb 统计系统内存
```

补充：`total` 总内存，`used` 已使用内存，`free` 空闲的内存，`shared` 当前已经废弃不用，`buff/cache` 缓存内存，`available` 可用内存

#### du 命令

```
du /usr #统计指定目录或文件的大小

du -h /usr #统计指定目录或分区大小并以K，M，G 为单位，提高信息的可读性

du -s /usr #统计目录的总大小

du -sh /usr #统计并 K，M，G 为单位显示
```

#### df 命令

```
df / #统计指定分区的大小，默认以千字节显示

df -h /usr #统计指定文件大小并以 K，M，G 为单位，提高信息的可读性
```

补充：`df` 和 `du` 的区别，`df` 是统计文件系统，包括文件、目录、程序、命令占用的空间；`du` 是统计文件和目录的占用空间。统计系统占用硬盘占用大小以 `df` 为准，一般建议一段时间重启服务器释放被进程和已经删除文件目录占用的空间。

#### lsb_release 命令

```
lsb_release -a #查看系统版本信息
```

#### top 命令

```
top #查看资源占用比

第一行：系统当前时间 系统持续时间 登录用户1,5,15分钟之前的平均负载
第二行：进程总数
第三行：CPU占用率 %id 空闲百分比
第四行：内存使用： 总共 空闲 使用 缓存
第五行：swap使用

top -p 6297 #查看指定 pid 信息

top -u root #查看指定用户的进程
```

#### netstat 命令

```
netstat  -tuln  #查看本机所有监听端口

netstat  -an #查看所有网络连接
```

补充：`t` 代表 `tcp` ， `u` 代表 `udp` ，`l` 代表监听，`n` 代表以 IP 和端口号显示。

#### ps 命令

```
ps -aux #查看系统所有进程，以 BSD 系统格式显示

```

补充：`a` 代表显示前台所有进程，`u` 显示用户名，`x`	显示后台进程。

#### pstree 命令

```
pstree #查看系统进程以树状显示

pstree -p #显示 PID 的进程树
```

#### lsof 命令

```
lsof -i:22 #查看 22 端口打开的进程文件

lsof -i 4 #查看 IPv4 的进程文件

lsof -i 6 #查看 IPv6 的进程文件

lsof -i TCP #查看 TCP 进程文件

lsof -i UDP #查看 UDP 进程文件

lsof -i -sTCP:LISTEN #查看监听 TCP 的进程

lsof -i:80 -sTCP:LISTEN #查看监听 80 端口的 TCP 的进程
 
lsof -t #查看进程 id 列表

lsof -p 470 #查看知道进程 id 的文件

lsof -u nick #查看指定用户进程文件

lsof -u ^nick #查看排除指定用户的进程文件

```

补充：`lsof` 命令显示内容分别为：进程的名称、进程 id 、用户名称、文件描述符、类型、设备、大小、节点（节点磁盘上的标识）、文件名称

#### kill 命令

```
kill -9 2845 #强制杀死 pid 为 2845 的进程
```


#### killall 命令

```
killall -9 nginx #强制杀死 nginx 进程
```

#### pkill 命令

```
pkill -9 5679 #强制杀死 pid 为 5679 的进程

pkill -9 -t pts/1 #强制踢远程终端用户下线
```

补充：超级管理员可以踢任何人，普通用户只能踢自己。

#### ip 命令

```
以后补充
```

#### ifconfig 命令

```
ifconfig  #查看网卡信息
```

#### route 命令

```
route #查看路由

route -n #查看网关
```

#### env 命令

```
env #查看当前用户的系统环境变量信息
```

#### systemctl 命令

```
systemctl start nginx #开启 nginx 服务

systemctl stop nginx #关闭 nginx 服务

systemctl restart nginx #重启 nginx 服务

systemctl reload nginx #重新加载 nginx 服务

systemctl status nginx #查看 nginx 服务

systemctl enable nginx #设置开启自启动

systemctl disable nginx #关闭开机自启动

systemctl list-units --type=service #查看已启动的服务
```

#### service 命令

```
service mysqld start #开启 mysql 服务

service mysqld stop #关闭 mysql 服务

service mysqld restart #重启 mysql 服务

service mysqld reload #重新加载 mysql 服务

service mysqld force-reload #强制加载 mysql 服务

service mysqld status #查看 mysql 服务
```

#### chkconfig 命令

```
chkconfig --list #查看所有的系统服务

chkconfig --list xxx #查看某个服务的设置信息

chkconfig --add xxx #添加系统服务

chkconfig --del xxx #删除系统服务

chkconfig xxx on #设置开机自启动
```

#### uname 命令

```
uname #打印内核名称

uname -n #打印主机名称

uname -r #打印系统版本号

uname -m #查看系统位数

unmae -a #打印全部内核信息
```

#### reboot 命令

```
reboot #重启系统
```

#### halt 命令

```
halt #关机
```

#### shutdown 命令

```
shutdown -h now #立刻关机

shutdown -r now #立刻重启

shutdown -r 11:26 #指定时间重启，时间按 24 小时制

shutdown -r 20180517 11:30 #指定日期时间重启

shutdown -c #取消指定时间的关机或重启
```

#### dd 命令

```
以后补充
```

#### ssh 命令

```
ssh username@ip #远程登录服务器

ssh username@ip 'pwd' #连接服务器并执行命令将结果返回给本地

ssh -p 2222 username@ip #指定端口登录远程服务器

```

#### ping 命令

```
ping ip or domain name #使用 ICMP 协议测试服务器是否正常运行

ping -c 2 ip #测试并设置返回的数据次数
```

#### dig 命令

```
dig baidu.com #查看域名 dns 信息
```

#### host 命令

```
host baidu.com #查看域名的ip
```

#### whois 命令

```
whois baidu.com #查看域名信息
```

#### hostname 命令

```
hostname #查看主机名称

hostname -i #查看主机 IP

hostname –d #查看主机域名
```

#### runlevel 命令

```
runlevel #查看系统运行级别
```

#### telnet 命令

```
telnet ip 端口 #测试指定 ip 的端口是否开放
```

#### jobs 命令

```
jobs -l #查看任务列表

jobs -r #查看正在运行的任务列表

jobs -s #查看停止运行的任务列表

jobs -p #查看任务的进程号
```

补充：输出信息的第一列为任务编号，第二列为任务的进程号，第三列任务的运行状态，第四列为启动任务的命令

#### bg 命令

```
bg 1 #将任务编号为 1 调到后台运行
```

#### fg 命令

```
fg 1 #将任务编号为 1 调到前台运行
```

#### pgrep 命令

```
pgrep nginx #查看 nginx 进程

pgrep -l nginx #查看 nginx 进程名称
```

#### vmstat 命令

```
vmstat 2  #每 2 秒打印一次系统内存使用情况

vmstat 2 6 #每 2 秒打印一次系统内存使用情况，打印 6 次退出

vmstat -t 1 5 #1 秒打印一次，打印 5次 ，添加时间戳


Procs（进程）:
    r: 运行队列中进程数量
    b: 等待IO的进程数量
Memory（内存）:
    swpd: 使用虚拟内存大小
    free: 可用内存大小
    buff: 用作缓冲的内存大小
    cache: 用作缓存的内存大小
Swap:
    si: 每秒从交换区写到内存的大小
    so: 每秒写入交换区的内存大小
    IO：（现在的Linux版本块的大小为1024bytes）
    bi: 每秒读取的块数
    bo: 每秒写入的块数
system：
    in: 每秒中断数，包括时钟中断
    cs: 每秒上下文切换数
CPU（以百分比表示）
    us: 用户进程执行时间(user time)
    sy: 系统进程执行时间(system time)
    id: 空闲时间(包括IO等待时间)
    wa: 等待IO时间
```

#### vnstat 命令

```

```

#### iostat 命令

```

```

#### iftop 命令

```

```

#### iotop 命令

```

```

#### tcpdump 命令

```

```

#### lscpu 命令

```
lscpu # 查看 cpu 信息 
```

补充： 与 `cat /proc/cpuinfo` 类似

#### visudo 命令

```
visudo # 快速编辑 /etc/sudoers 文件
```

补充：默认编辑器为 `nano` ，修改为 `vim` 执行 `sudo update-alternatives --config editor` 弹出选项，选择 `vim.tiny` 按回车键即可

