#### tar 打包压缩命令

```
tar -czvf filename.tar.gz test #打包test目录并使用gzip压缩并显示文件信息

tar -xzvf filename.tar.gz #解压gzip文件并输出文件信息

tar -cjvf filename.tar.bz2 test #打包test目录并使用gzip2压缩并显示文件信息

tar -xjvf filename.tar.bz2 #解压使用gzip2压缩并显示文件信息

```
补充：`-v` 为显示信息

#### zip 压缩命令，文件后缀.zip

```
zip html.zip ./html #压缩当前目录下html目录或文件

unzip html.zip #解压在当前目录或文件

zip -qr html.zip ./html #将当前html目录递归压缩保存文件名为html.zip

unzip html.zip #解压在当前目录

unzip -o html.zip -d /usr/local/ #解压html.zip文件到/usr/local/下

zip -qr html.zip ./html #将当前html目录递归压缩为html.zip
```

#### gzip 压缩命令，文件后缀.gz

```
gzip index.php #压缩index.php文件,文件名为index.php.gz，不会保留原文件

gunzip index.php.gz #解压文件

gzip -d index.php.gz #解压文件

```

#### bzip2 压缩命令，文件后缀.bz2

```
bzip2 index.php #压缩index.php文件,文件名为index.php.bz2，不会保留原文件

bunzip2 index.php.bz2 #解压文件

bzip2 -d index.php.bz2 #解压文件

```

#### xz 压缩命令,文件后缀.xz

```
xz -z index.php #压缩文件

xz -d index.php.xz #解压文件
```



