#### wget 命令

```
wget url #下载文件

wget -O demo.html url #下载文件并改为指定名称

wget -c url #断点续传

wget -i url url url #下载多个文件
```

补充：`wget` 命令适用于下载。

#### curl 命令

```
curl www.baidu.com #请求指定网址并显示出来

curl -o demo.html https://www.baidu.com/index.php #下载指定文件并重命名为 demo.html

curl -v www.baidu.com #显示请求的过程信息

curl -X GET www.baidu.com #指定请求方法，请求方法必须大写

curl -C url #断点续传，适用网络不顺畅时下载大文件，无须重新下载
```

补充：`curl` 命令适用于上传与请求。