#### users 命令

```
users #查看当前在线的用户名称列表
```

#### 用户分 3 种

1. `root` 用户，即超级管理员

2. 拥有 `root` 权限的用户，可以执行 `sudo` 命令

3. 普通用户

#### 用户文件与配置

- /etc/passwd

- /etc/shadow

#### adduser 命令

```
adduser demo #添加账号
```

补充：此命令在 CentOS7.2 系统中为软连接，源目标是 adduser 命令。在 Ubuntu16.04 中是独立的命令，添加账号时会有友好的提示，设置密码账号信息等。

#### useradd 命令

```
useradd demo #添加用户，默认家目录在 /home/ 目录下 demo 目录，与用户名一致

passwd demo #设置密码，默认添加用户之后没设置密码不允许登录

useradd -u 2333 demo #添加用户并指定用户 id ，一般情况很少使用

useradd -d /home/testuser demo #添加用户并指定家目录，一般情况很少使用

useradd -G xxx,xxx demo #添加用户并加入多个附加组
```

#### usermod 命令

```
usermod -L demo #锁定用户，不允许登录，相当于手动修改 /etc/shadow 文件中用户密码前加入 ! 一个感叹号

usermod -U demo #解除锁定
```

#### userdel 命令

```
userdel demo #删除用户，不删除用户家目录数据

userdel -r demo #删除用户并删除用户家目录

userdel -rf demo #强制删除用户无论是否登录，并删除用户家目录
```
#### passwd 目录

```
passwd -l demo #锁定用户，不允许登录，相当于手动修改 /etc/shadow 文件中用户密码前加入 !! 双感叹号

passwd -u demo #解除锁定
```

#### groups 命令

```
groups #查看当前用户的用户组名称
```

#### 用户组分 2 种

1. 初始组（默认组）

2. 其他组（附加组）

#### 用户组文件与配置

-  /etc/group

- /etc/gshadow


#### addgroup 命令

```
groupadd test #添加用户组
```

#### groupmod 命令

```
groupmod -n new_test test #把 test 组名修改为 new_test
```

#### gpasswd  命令

```
gpasswd -a nick new_test #将 nick 用户添加到 new_test 组

gpasswd -d nick new_test #将 nick 用户从 new_test 组删除
```

#### groupdel 命令

```
groupdel new_test #删除用户组
```

补充：每添加一个用户会自动创建一个用户组，称为默认组或初始组，这个组是不允许删除的，默认组一般不修改最好，用户 id 也一样。

#### sudo 命令

```
sudo vim /etc/passwd #以另一个用户身份执行命令，通常是 root 用户
```

补充：普通用户添加执行 `sudo` 的方法，在 `/etc/sudoers` 文件中添加 `username ALL=(ALL) ALL` 即可。

#### su 命令

```
su   #切换到 root 用户，仅切换路径

su - #切换到 root 用户，环境变量和路径一起切换

su - nick #切换到 nick 用户，环境变量和路径一起切换
```

#### whoami 命令

```
whoami #查看当前用户的名称
```

#### id 命令

```
id #查看当前用户的 id 、组 id 、附加组 id 

id -un #查看当前用户的名称

id -g #当前用户的组 id

id -G #当前用户的附加组 id

id -u root #查看指定用户的 id

id root #查看指定用户的 id gid groupsid
```

#### who 命令

```
who #查看当前的在线用户、终端号、IP、登录时间

who -q #查看在线的用户的用户名，用户数
```