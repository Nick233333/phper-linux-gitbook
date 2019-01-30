#### 检测 Web 服务器

新建文件 `vim ~/http.sh` 写入以下内容

```
#!/bin/bash

ip=xxxxxx #自定义

port=$(nmap -sT $ip | grep tcp | grep http | grep 80 | awk '{print $2}')
if [ "$port" == "" ]; then
    systemctl restart nginx
    echo "http error $(date +%Y-%m-%d' '%H:%M:%S)" >> ~/http_logs_error.log
fi
```

设置定时任务

```
*/10 * * * * ~/http.sh #10分钟执行一次
```

---

#### 检测指定服务是否正常运行

新建文件写入以下内容

```
#!/usr/bin/env bash

read name
pgrep $name > /dev/null
if [ $? -gt 0 ];then
    echo "`date` $name is stop" >> ~/mysql_listen.log
    systemctl $name mysql
else
    echo "`date` $name running" >> ~/mysql_listen.log
fi
```

给脚本添加执行权限后运行，输入服务名称即可

---

#### 备份数据库

新建文件 `vim ~/mysqldump.sh` 写入以下内容

```
#!/bin/bash

dir=~/data_bak #自定义
filename=demo  #自定义
username=nick  #自定义
password=xxx   #自定义
database=demo  #自定义

if [ -d $dir ]; then
    mysqldump -u$username -p$password $database | gzip > $dir/$filename\_$(date +%Y%m%d).sql.gz
else
    mkdir $dir
    mysqldump -u$username -p$password $database | gzip > $dir/$filename\_$(date +%Y%m%d).sql.gz
fi
```

设置定时任务

```
1 3 * * 0 ~/mysqldump.sh # 每周日凌晨3点1分执行
```

补充：新建的 `shell` 脚本默认没有执行权限，需要自己添加

---

#### 获取文件名

```
#!/bin/bash

file_jpg="sample.jpg"
name=${file_jpg%.*}
echo File name is: $name
```

---

#### 获取文件扩展名

```
#!/bin/bash

file="sample.png.text"
echo ${file##*.} #贪婪模式，匹配到最后一个 .
```

---

#### 重命名文件

```
#!/bin/bash

count=1;
for file in $(find . -maxdepth 1 -type f -iname '*.html')
do
    new_file=filename-$count.${file##*.}
    echo "Renaming $file to $new_file"
    mv "$file" "$new_file"
    let count++
done
```