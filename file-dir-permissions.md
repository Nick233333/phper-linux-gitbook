#### Linux 的文件类型

1. 普通文件，符号为 `-`

2. 目录，符号为 `d`

3. 字符设备，符号为 `c`

4. 块设备，符号为 `b`

5. 套接字文件，符号为 `s`

6. 软链接文件，类似 `Windows` 系统的快捷方式，删除了并不会影响源文件，符号为 `l`

7. 管道文件，符号为 `p`

补充：常见的文件类型为 `-` `d` `l`

#### Linux 的 3 种权限

- `r` 代表 `read` 读权限，数字代表为 `4`

- `w` 代表 `wirte` 写权限，数字代表为 `2`

- `x` 代表 `execute` 执行权限，数字代表为 `1`

#### Linux 的 3 种用户

- 拥有者（owner）

- 用户组（group）

- 其它人（others）

#### 解读

```
-rw-rw-r-- 1 nick nick 0 May 12 16:05 demo.php

- 第 1 列代表文件类型
rw- 第 2-4 列代表所属用户的权限
rw- 第 5-7 列代表所属用户组的权限
r-- 第 8-11 其他用户所属权限
1 第 11 列代表文件被引用的次数
nick 第 12 列代表文件所属用户名称
nick 第 13 列代表文件所属用户组名称
0 第 14 列代表文件大小
May 12 16:05 第 15-17 列代表文件最后的修改时间
demo.php 第 18 列代表文件名称
```

### stat 命令

```
stat filename #查看文件的详细信息，文件的访问时间、修改时间、改变时间，linux 文件没有创建时间
```

#### chmod 命令

```
chmod 755 filename #将文件权限修改为 755 ,即拥有者有读写执行权限，用户组有读执行权限，其他人有读执行权限 

chmod -R 755 dirname #递归修改目录的权限
```

#### chown 命令

```
chown nick index.php #将文件拥有者改为 nick

chown :nick index.php #将文件用户组修改为 nick

chown nick:nick index.php #将文件拥有者和用户组修改为 nick

chown nick php #将目录拥有者修改为 nick

chown :nick php #将目录用户组修改为 nick

chown nick:nick php #将目录拥有者和用户组修改为 nick

chown -R nick:nick php #递归将目录拥有者和用户组修改为 nick
```

#### chattr 命令

```
chattr +i index.php #设置文件不允许修改、删除、移动、复制，root 用户也生效

chattr -i index.php #取消文件属性设置
```

#### lsattr 命令

```
lsattr filename or dirname #查看文件或目录的属性
```