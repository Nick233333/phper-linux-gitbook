## tar 打包压缩命令

```
tar -czvf filename.tar.gz #打包使用gzip压缩并显示文件信息`

tar -xzvf filename.tar.gz #解压gzip文件并输出文件信息

tar -cjvf filename.tar.bz2 #打包使用gzip2压缩并显示文件信息`

tar -xjvf filename.tar.bz2 #解压使用gzip2压缩并显示文件信息`

```
补充：`-v` 为显示信息

## zip 压缩命令

```
zip html.zip./html #压缩当前目录下html目录或文件

unzip html.zip #解压在当前目录或文件

zip -qr html.zip ./html #将当前html目录递归压缩保存文件名为html.zip

unzip html.zip #解压在当前目录

unzip -o html.zip -d /usr/local/ #解压html.zip文件到/usr/loca/下

zip -qr html.zip ./html #将当前html目录递归压缩为html.zip
```


