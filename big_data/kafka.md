# Kafka

```
brew services start zookeeper

zkServer start

brew services start kafka

kafka-topics --create --zookeeper localhost:2181 --replication-factor 1 --partitions 1 --topic twitterstream

kafka-console-consumer --zookeeper localhost:2181 --topic twitterstream --from-beginning

# 
/usr/local/Cellar/kafka/0.11.0.1/libexec/config/zookeeper.properties

# 
/usr/local/Cellar/kafka/0.11.0.1/libexec/config/server.properties
```