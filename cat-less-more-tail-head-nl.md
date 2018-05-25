#### cat 显示文件内容

```
cat demo.php #在屏幕上显示 demo.php 文件的内容

cat -n demo.php #查看文件内容并从 1 开始添加序号
```

#### less 分屏显示文件内容

```
less demo.php #显示 demo.php 文件，退出按 q 键
```
补充：Enter（向下翻滚一行），空格（向下滚动一屏），Q（退出命令）

#### more 和 less 命令类似，也是分屏显示文件内容

```
more -10 demo.php #指定没屏显示 10 行内容

morw +50 demo.php #指定从第 50 行开始显示
```
补充：Enter（向下翻滚一行），空格（向下滚动一屏），Q（退出命令）

#### tail 显示文件尾部的内容

```
tail demo.php #默认显示文件尾部 10 行

tail -2 demo.php #显示文件尾部 2 行
```

#### head 显示文件头部内容

```
head demo.php #显示文件内容，默认显示 10 行

head -5 demo.php #显示文件头部 5 行内容
```

#### nl 命令

```
nl demo.php #查看文件内容并加行号显示
```


