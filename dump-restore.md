#### dump 命令

```
dump -0uj -f /home/vda1.bak.bz2 /dev/vda1/ #增量备份分区，将 /dev/vda1/ 备份到 /home 目录下，使用 gzip2 压缩，备份层级为 0 并在 /etc/dumpdates 中记录相关信息

cat /etc/dumpdates  #查看备份信息

dump -1uj -f /home/vda1.bak.bz2 /dev/vda1/ #增量备份分区，仅备份新添加的数据

dump -W #查看备份级别

dump -0j -f /home/etc.bak.bz2 /etc #备份目录，备份目录级别只能为 0 不能增量备份
```

补充：备份的级别有 `0-9` ，`-u` 代表添加备份记录，`-j` 代表使用 `gzip2` 压缩, `-f` 代表备份后的文件名，`-W` 代表查看需要备份的文件及其最后一次备份的层级、时间与日期

#### restore 命令

```
restore -tf /home/etc.bak.bz2 #查看备份数据内容

restore -C -f /home/etc.bak.bz2 #对比备份的数据和原有数据的变化

restore -rf /home/etc.bak.bz2 #恢复数据，增量备份需要把所有增量数据恢复，建议新建空目录，把恢复的数据保存在空目录中，在复制到指定目录
```

补充：`-C` 对比备份数据和原有数据的变化，`-f` 指定备份的文件名，`-r` 还原数据，`-t` 查看备份数据的内容