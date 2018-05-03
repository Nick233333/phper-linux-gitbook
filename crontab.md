#### crontab 命令

```
crontab -l #显示定时任务列表

crontab -e #编辑定时任务

crontab -r #删除定时任务

sudo crontab -u root -e #指定 root 用户编辑，每个用户对应有一个 crontab 文件
```

crontab 文件内容说明

```
Minute Hour Day Month Week command
  |     |    |    |    |      |
  |     |    |    |    |      |
  分    时   天   月   周  命令或文件或url

取值范围
分（0-59） 
时（0-23） 
天（1-31） 
月（1-12） 
周（0-6）

* 代表所有可能的值,
/ 代表每,
- 代表从某个数字到某个数字,
, 分开几个指定的数字

第一次执行 crontab -e 会出现一些内容，选择编辑器，建议选 3，vim 编辑器
Select an editor.  To change later, run 'select-editor'.
  1. /bin/ed
  2. /bin/nano        <---- easiest
  3. /usr/bin/vim.basic
  4. /usr/bin/vim.tiny

```

例子

```
*/1 * * * * ~/http.sh #每1分钟执行一次 ~/http.sh shell 文件

01 * 2 * * ~/http.sh #每月2号第一分钟执行一次 ~/http.sh shell 文件

* 2,3 * * * ~/http.sh #每天凌晨2点，3点 执行一次 ~/http.sh shell 文件

10 * * * 1-5 root /usr/local/bin/php /home/ubuntu/demo.php #周一到周五第10分钟以 root 用户 php 命令去执行一次 demo.php 文件
```