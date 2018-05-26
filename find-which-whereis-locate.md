#### find 命令

```
sudo find /usr/local/nginx -name nginx.conf #在 /usr/local/nginx 下查找 nginx.conf 文件

sudo find /usr/local/nginx -iname nginx.conf #在 /usr/local/nginx 下查找 nginx.conf 文件,忽略文件名称大小写

sudo find /home/ ! -name "*.gz" #查找不是 .gz 后缀的文件

sudo find /home/  -iname "demo.*" #查找名称为 demo 开头的文件，不区分文件名称大小写

sudo find . -type f #查找文件类型为文件

sudo find . -maxdepth 1 -type f #查找文件类型为文件,向下最大深度限制为1

sudo find . -type d #查找文件类型为目录

sudo find . -type f -atime -7 #查找7天之内访问过的文件

sudo find . -type f -atime +7 #查找超过7天的访问文件

sudo find . -type f -atime 7 #查找7天前的访问文件

sudo find . -type f -amin -10 #查找10分钟之内的访问文件

sudo find . -type f -amin 10  #查找超过10分钟的访问文件

sudo find . -type f -amin +10 #查找超过10分钟的访问文件
```

补充：`+` 意思为大于，`-` 意思为小于，没有符合是等于。
- 访问时间（-atime/天，-amin/分钟）：用户最近一次访问时间。
- 修改时间（-mtime/天，-mmin/分钟）：文件最后一次修改时间。
- 变化时间（-ctime/天，-cmin/分钟）：文件数据（包括权限等）最后一次修改时间。

#### which 命令

```
which php #查找 php 命令的绝对路径，可用于判断某个系统命令是否存在
```

#### whereis 命令

```
whereis php #查找 php 命令的位置
```

#### locate 命令

```
locate /etc/*.conf #查找 /etc 命令下所有 .conf 后缀的文件，此命令比 find 快
```