# Kafka

### Installation with Homebrew

* Binaries and scripts will be in `/usr/local/bin`
* Kafka configurations will be in `/usr/local/etc/kafka`
* Zookeeper configuration will be in `/usr/local/etc/zookeeper`
* The log.dirs config (the location for Kafka data) will be set to `/usr/ local/var/lib/kafka-logs`

> from Kafka The Definitive Guide

### Frequent Command

```
# start zookeeper

zkServer start /usr/local/etc/kafka/zookeeper.properties

zkServer stop /usr/local/etc/kafka/zookeeper.properties

zookeeper-server-start /usr/local/etc/kafka/zookeeper.properties

# start kafka
brew services start 

kafka-server-start /usr/local/etc/kafka/server.properties

# create topic
kafka-topics --create --zookeeper localhost:2181 --replication-factor 1 --partitions 1 --topic twitterstream

# print out topic
kafka-console-consumer --bootstrap-server localhost:9092 --topic s --from-beginning

kafka-console-consumer --zookeeper localhost:2181 --topic twitterstream --from-beginning
Using the ConsoleConsumer with old consumer is deprecated and will be removed in a future major release. Consider using the new consumer by passing [bootstrap-server] instead of [zookeeper].

# list all topics
kafka-topics --list --zookeeper localhost:2181

# delete topic
kafka-topics --delete --topic meetup --zookeeper localhost:2181

# find largest
kafka-run-class kafka.tools.GetOffsetShell --broker-list localhost:9092 --time -1 --topic meetup

# find smallest
kafka-run-class kafka.tools.GetOffsetShell --broker-list localhost:9092 --time -2 --topic meetup
```
