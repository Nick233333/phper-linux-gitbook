#### grep 命令

```
sudo grep -c '500' fielename.log #查找文件包含500的行数

sudo cat index.html | grep -o 'js' #只输出文件中匹配到的部分

ps -aux | grep sshd #查找指定访问

ps -aux | grep 80 #查找指定端口

echo hello world | grep -i "HELLO" #查找指定内容忽略大小写

grep "sudo git pull" ~/test -R -n #递归查找指定目录下文件内容，如果找到返回文件名称，行号，查找到的内容

grep "sudo git pull" . -r --exclude "gitbook.sh" #递归查找指定目录下文件内容，并忽略指定文件

grep "sudo git pull" . -r --exclude-dir "test" #递归查找指定目录下文件内容，并忽略指定目录
```

#### sed 命令

```
sed -i '$d' root.sh #删除文件最后一行

sed '/^$/d' root.sh #打印文件内容删除掉空行

sed -n '-p' demo.php #查看文件第 2 行

sed '2d' demo.php #打印文件内容不显示第 2 行

sed '2,5d' demo.php #打印文件内容不显示第 2 行到第 5 行内容

sed '2,$d' demo.php #打印文件内容不显示 2 行到最后一行

sed '2a hello' demo.php #打印文件内容并在第 2 行后面追加内容

sed '2i hello' demo.php #打印文件内容并在第 2 行前面插入内容

sed 's/text/html/g' demo.php #打印并将文件内容 text 替换成 html 

sed -e 's/text//g' demo.php #打印并将文件内容 text 替换为空
```

补充：`sed` 命令不会修改原文件内容，除非使用 `-i` 选项

#### awk 命令

```
awk '{print $9}' filename.log | grep 500 | wc -l #统计日志 500 状态码的数量

awk '{print $1}' filename.log | grep 'ip' | wc -l #统计指定 IP 的访问次数

awk '{a[b[$1]++]}END{for(i=length(a);i>0;i--)for(j in b)if(b[j]==i){c++;if(c<=10)print j,i}}' filename.log #统计访问前 10 的 IP 并输出访问数量

awk '{print $7}' filename.log | grep 'url' | wc -l #统计指定 url 的访问次数

sed "/Baiduspider/d;/Googlebot/d;/Sogou web spider/d;" filename.log | awk -F' ' '{print $7}' | sort | uniq -c | sort -k1,2 -nr #统计所有 url 访问次数，过滤搜索引擎的信息
```

补充：$1 代表第一列，默认从 1 开始