#### wget 命令

```
wget url #下载文件

wget -O demo.html url #下载文件并改为指定名称

wget -c url #断点续传

wget -i url url url #下载多个文件

wget -t 5 url #网络不好时重试 5 次

wget -t 0 url #不断重试

wget --limit-rate 20k url #限速下载

wget -Q 100m url #设置下载最大额度

wget --mirror --convert-links url #递归复制其他网站作为镜像，类似爬虫

wget --user username --password pass url #认证

```

补充：`wget` 命令适用于下载。

#### curl 命令

```
curl ifconfig.me #查看外网 IP

curl www.baidu.com #请求指定网址并显示出来

curl -o demo.html https://www.baidu.com/index.php #下载指定文件并重命名为 demo.html

curl -v www.baidu.com #显示请求的过程信息

curl url --silent #不显示下载进度信息

curl url -o index.html --progress #显示下载进度信息

curl --referer Referer_URL target_URL #设置 referer

curl url --cookie "user=username;pass=password" #设置 cookie 

curl url --user-agent "Mozilla/5.0 ..." #设置 User-Agent

curl url --limit-rate 20k  #限速

curl url --max-filesize bytes #设置下载最大额度

curl url -H 'HOST: 1.1.1.1' -H 'X-Real-IP: 2.2.2.2' #设置 http header

curl -X GET www.baidu.com #指定请求方法，请求方法必须大写

curl -C url #断点续传，适用网络不顺畅时下载大文件，无须重新下载

curl --connect-timeout 20 https://wp.hellocode.name/?p=701 #指定 url 并限制连接时间
```

补充：`curl` 命令适用于上传与请求。