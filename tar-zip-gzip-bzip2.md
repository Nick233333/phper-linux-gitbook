### tar 打包压缩命令

```
tar -cxvf filename.tar #打包压缩并显示文件信息`

tar -zxvf filename.tar #解压并输出文件信息
```

### zip 压缩命令

```
zip -qr html.zip ./html #将当前html目录递归压缩保存文件名为html.zip

unzip -v html.zip #查看压缩文件信息

unzip html.zip #解压在当前目录

unzip -o html.zip -d /usr/local/ #解压html.zip文件到/usr/loca/下

zip -qr html.zip ./html #将当前html目录递归压缩为html.zip
```


