#### crontab 命令

__Linux下的任务调度分为两类：系统任务调度和用户任务调度。__

系统任务调度：系统周期性所要执行的工作，比如写缓存数据到硬盘、日志清理等。在 `/etc` 目录下有一个 `crontab` 文件，这个就是系统任务调度的配置文件。

系统任务调度存放的目录

- /etc/cron.hourly  小时
- /etc/cron.daily   每天
- /etc/cron.weekly  每周
- /etc/cron.monthly 每月

用户任务调度：用户定期要执行的工作，比如用户数据备份、定时邮件提醒等。

`/etc/cron.deny` 该文件中配置用户不允许使用 `crontab` 命令，亲测 `Ubuntu16.04` 默认不存在，`CentOS7.2` 存在，如果要禁止某个用户不能使用 `crontab` ，在此文件写入用户名即可，仅对普通用户生效，`root` 用户无效。

`/etc/cron.allow` 该文件中配置用户允许使用 `crontab` 命令，亲测 `Ubuntu16.04` 、`CentOS7.2` 默认不存在。

> 系统读取顺序为先读取 /etc/cron.deny 文件，再读取 /etc/cron.allow 文件，建议保留任意一个文件即可，内容为一个用户名称一行。

`/var/spool/cron/`   所有用户 `crontab` 文件存放的目录，以用户名命名，`CentOS` 系统。

```
crontab -l #显示定时任务列表

crontab -e #编辑定时任务

crontab -r #删除定时任务

sudo crontab -u root -e #指定 root 用户编辑，每个用户对应有一个 crontab 文件
```

__crontab 文件内容说明__

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
周（0-7）0 和 7 都代表星期天

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

如果没有出现或选择错误可以用 select-editor 重新选择编辑器。
```

__例子__

```
*/1 * * * * ~/http.sh #每1分钟执行一次 ~/http.sh shell 文件

01 * 2 * * ~/http.sh #每月2号第一分钟执行一次 ~/http.sh shell 文件

* 2,3 * * * ~/http.sh #每天凌晨2点，3点 执行一次 ~/http.sh shell 文件

10 * * * 1-5 root /usr/local/bin/php /home/ubuntu/demo.php #周一到周五第10分钟以 root 用户 php 命令去执行一次 demo.php 文件

*/1 * * * * run-parts /home/nick/sh/ #每分钟执行 /home/nick/sh/ 目录内的脚本，CentOS 系统生效，Ubuntu 系统不生效，原因暂时未知，请教了运维，不建议这样操作。
```
`crontab` 文件里面指定的命令建议写绝对路径，文件相对路径和绝对路径都可以。
`run-parts` 可以指定任意目录执行，路径可以为相对路径也可以为绝对路径, `CentOS` 系统该命令位置 `/usr/bin/run-parts` ，`Ubuntu` 系统该命令位置 `/bin/run-parts` 。

__crontab 日志__

CentOS7.2 crontab 日志路径为 `/var/log/cron`

CentOS 系统 crontab 执行成功日志会出现以下内容

```
May  5 11:48:01 10-13-41-254 CROND[10770]: (nick) CMD (run-parts /home/nick/sh)
May  5 11:48:01 10-13-41-254 run-parts(/home/nick/sh)[10770]: starting 1.sh
May  5 11:48:01 10-13-41-254 run-parts(/home/nick/sh)[10777]: finished 1.sh
May  5 11:48:01 10-13-41-254 run-parts(/home/nick/sh)[10770]: starting 2.sh
May  5 11:48:01 10-13-41-254 run-parts(/home/nick/sh)[10783]: finished 2.sh
```

Ubuntu16.04 crontab 日志路径为 `/var/log/cron.log`

Ubuntu16.04 默认不生成 crontab 日志，需要更改配置，方法如下

```
sudo vim /etc/rsyslog.d/50-default.conf 

cron.*              /var/log/cron.log #将cron前面的 # 注释符去掉

sudo service rsyslog restart
```

Ubuntu 系统 crontab 执行成功日志会出现以下内容

```
May  5 11:37:01 localhost CRON[26565]: (root) CMD (/root/sh/1.sh)
May  5 11:38:01 localhost CRON[26677]: (root) CMD (/usr/local/qcloud/stargate/admin/start.sh > /dev/null 2>&1 &)
```