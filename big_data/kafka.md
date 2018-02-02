# Kafka

### Installation with Homebrew

* Binaries and scripts will be in `/usr/local/bin`
* Kafka configurations will be in `/usr/local/etc/kafka`
* Zookeeper configuration will be in `/usr/local/etc/zookeeper`
* The log.dirs config (the location for Kafka data) will be set to `/usr/ local/var/lib/kafka-logs`

> from Kafka The Definitive Guide

```
# start zookeeper
brew services start zookeeper

zkServer start /usr/local/etc/zookeeper/zookeeper.properties

zookeeper-server-start /usr/local/etc/zookeeper/zookeeper.properties

# start kafka
brew services start 

kafka-server-start /usr/local/etc/kafka/server.properties

# create topic
kafka-topics --create --zookeeper localhost:2181 --replication-factor 1 --partitions 1 --topic twitterstream

# print out topic
kafka-console-consumer --zookeeper localhost:2181 --topic twitterstream --from-beginning
```
