#### uptime 命令

```
uptime #显示信息依次为：当前时间、系统运行时间、目前登录用户、系统在 1 分钟、5 分钟和 15 分钟内的负载。
```

#### free 命令

```
free -m #以 mb 统计系统内存

free -k #以 kb 统计系统内存
```

补充：total：总内存，used：已使用内存，free：空闲的内存，shared 当前已经废弃不用，buff/cache 缓存内存，available 可用内存


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

补充：df 和 du 的区别，df 是统计文件系统，包括文件、目录、程序、命令占用的空间；du 是统计文件和目录的占用空间。统计系统占用硬盘占用大小以 df 为准，一般建议一段时间重启服务器释放被进程和已经删除文件目录占用的空间。

#### top 命令

```

```


#### netstat 命令

```

```

#### ps 命令

```

```


#### lsof 命令

```

```


#### kill 命令

```

```


#### killall 命令

```

```

#### pkill 命令

```

```


#### ip 命令

```

```

#### ifconfig 命令

```

```


#### route 命令

```

```

#### env 命令

```

```

#### systemctl 命令

```

```

#### service 命令

```

```

#### chkconfig 命令

```

```

#### uname 命令

```
uname #打印内核名称

uname -n #打印主机名称

uname -r #打印系统版本号

unmae -a #打印全部内核信息
```

#### rboot 命令

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

#### dump 命令

```

```

#### dd 命令

```

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
```

