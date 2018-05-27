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
