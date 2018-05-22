#### users 命令

```
users #查看当前在线的用户
```

#### adduser 命令

```

```

#### useradd 命令

```

```

#### usermod 命令

```

```

#### userdel 命令

```

```

#### groups 命令

```

```

#### addgroup 命令

```

```

#### groupmod 命令

```

```


#### groupdel 命令

```

```

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