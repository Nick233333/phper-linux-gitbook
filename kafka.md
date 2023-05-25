#### Kafka 命令

```
kafka-topics -bootstrap-server localhost:9092 --create --topic nick  --partitions 1 --replication-factor 1 #创建主题命令

kafka-topics -bootstrap-server localhost:9092 --delete --topic nick #删除主题命令

kafka-topics -bootstrap-server localhost:9092 --list #查看所有主题命令

kafka-topics -bootstrap-server localhost:9092 --topic test --describe #查看指定主题详情命令

kafka-run-class kafka.tools.GetOffsetShell --broker-list localhost:9092 --topic media-topic --time -1 #查看消息数量

kafka-console-producer --broker-list localhost:9092 --topic media-topic #生成数据

kafka-console-consumer --topic media-topic  --bootstrap-server localhost:9092 #消费者命令

kafka-console-consumer --topic media-topic  --bootstrap-server localhost:9092 --from-beginning  #消费者命令 --from-beginning 表示从最初的未过期的 offset 处开始消费数据。不加该参数，表示从最新 offset 处开始消费数据。

kafka-consumer-groups --bootstrap-server localhost:9092 --list #查看消费组
```