# kafka
Overview of Kafka and usage in Distributed Systems

# Source / References
- Hussein Nasser https://www.youtube.com/watch?v=R873BlNVUB4

# Components
- Topics are logical partitions of data.
- Producers / Consumers need to specify the Topic that they want to use
- Messages are identified by their partition + index in that partition.
- As Messages increase, Topics are to be partitioned just like how we would do a database to improve performance.
- Producer has to specify the Message, the Topic and the Partition in that topic as well.
- ![image](https://user-images.githubusercontent.com/42272776/173420222-b947f9e8-e169-4d0d-9ffc-789c2503f28f.png)

## Queue vs Pub Sub
- Queue: Message published once, consumed once.
- Pub Sub: Message published once, consumed many times.
- RabbitMQ started as a Queue. But moved to Pub-Sub using Exchanges.
- Kafka uses Consumer Groups to achieve Pub-Sub.
- ![image](https://user-images.githubusercontent.com/42272776/173421506-1b4e9f91-928a-41c8-a2bc-6bd4ef8c987b.png)
- There can be many Consumers in a Consumer Group. A Consumer in a Group can listen to many Partitions but a Partition can only work with a single Consumer in a Consumer Group.
- Multiple Consumers across Multiple Consumer Groups may however listed to the same Partition.
- To make Kafka work in Queue mode:
  - Put all the consumers into a single Consumer Group. This would make all the consumers listen to distinct partitions.
- To make Kafka work in Pub-Sub mode:
  - Put all the consumers into unique Consumer Groups. This would make all the consumers to be able to listen to the same partitions ( pub-sub simulation ).  

# Architecture
- Multiple slaves/followers can be created for Kafka that hold the same data (replication).
- One node could be leader of one partition of a topic and the other node could be leader of the next partition. This produces high availability.
- The information on who the leader is, is stored in Apache Zookeeper.
- ![image](https://user-images.githubusercontent.com/42272776/173422370-f408b26e-19c9-47b0-8e93-af397d685e2b.png)


# KSQL
# Streaming
