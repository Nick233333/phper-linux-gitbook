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
第三行：CPU占用率 %id	空闲百分比
第四行：内存使用： 总共 使用 空闲 缓存
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
```

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

route -n  #查看网关
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

