#kafka #queue
### Basics
---
- Topics -> Partition -> Offset (here the message is accessed)
- Each Consumer group can read from same topic
- Each consumer from a consumer group can read from one partition only and one partition is assigned to one consumer only (**in case the number of consumers is less than the number of partitions, then one consumer can consume from multiple partitions, kafka takes care of this)**
- Each message in a topic can be in one partition only
### What if A consumer goes down ?
---
Consumer commits it's last read offset and Zookeeper stores this information, so consumer can start reading from that offset again.
### What if broker goes down ?
---
In a kafka cluster, there are multiple brokers spread managed by zookeper, so the replica topic (of the went down broker that went down and had primary) becomes the primary topic.
### Who commits the offset ?
---
The consumer commits the offset. The logic can be set as auto-commit after some time or manual commit.
