#### crontab 命令

Linux下的任务调度分为两类：系统任务调度和用户任务调度。

系统任务调度：系统周期性所要执行的工作，比如写缓存数据到硬盘、日志清理等。在 `/etc` 目录下有一个 `crontab` 文件，这个就是系统任务调度的配置文件。

用户任务调度：用户定期要执行的工作，比如用户数据备份、定时邮件提醒等。

`/etc/cron.deny`     该文件中所列用户不允许使用 `crontab` 命令，亲测 Ubuntu16.04 默认不存在，CentOs7.2 存在

`/etc/cron.allow`    该文件中所列用户允许使用 `crontab` 命令,亲测 Ubuntu16.04 、CentOs7.2 存在默认不存在

`/var/spool/cron/`   所有用户 `crontab` 文件存放的目录，以用户名命名

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

01 * * * * root run-parts /etc/cron.hourly #每小时第1分钟执行 /etc/cron.hourly 目录内的脚本
```

run-parts 参数指定的目录必须是以下任意一个，其他位置的目录无法执行

- /etc/cron.hourly  小时
- /etc/cron.daily   每天
- /etc/cron.weekly  每周
- /etc/cron.monthly 每月

日志

CentOs7.2 crontab 日志路径为 `/var/log/cron`

Ubuntu16.04 crontab 日志路径为 `/var/log/cron.log`

Ubuntu16.04 默认不生成 crontab 日志，需要更改配置，方法如下

```
sudo vim /etc/rsyslog.d/50-default.conf 

cron.*              /var/log/cron.log #将cron前面的 # 注释符去掉

sudo service rsyslog restart
```