#### touch 命令

```
touch index.html #新建空文件
```

#### mkdir 命令

```
mkdir demo #创建目录
```

#### rmdir 目录

```
rmdir demo #删除空目录，如果目录有文件无法删除
```

#### cp 目录

```
cp index.php php #复制 index.php 文件到当前 php 目录下

cp -a index.php php #复制 index.php 文件到当前 php 目录下,保留文件的属性、权限、软连接自动指向目标文件

cp index.php ~/app.php #复制文件到指定目录下并修改文件名

cp -R php app #递归复制 php 目录下所有文件到 app 目录 
```

#### mv 目录

```
mv index.php app.php #将 index.php 名称更改为 app.php

mv ~/php /home #将家目录下 php 目录移动到根目录 home 目录下
```

#### rm 目录

```
rm index.php #删除文件

rm -i index.php #执行删除询问 y 代表删除 n 代表取消

rm -r test #递归删除目录

rm -f test #强制删除目录

rm -rf php #强制递归删除目录
```

#### tree 目录

```
tree ~ #以树状图列出指定目录的内容

tree -d laravel #以树状图列出指定目录的内容，不包括文件
```