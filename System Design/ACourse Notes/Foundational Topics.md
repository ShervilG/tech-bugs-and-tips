#systemdesign #basics #foundation
# How To Approach System Design
- Start with Day-0 Architecture
- Analyse how components will behave under load
- Identify Bottlenecks
- Re-Architect
- Repeat from step-2

>Don't go beyond 2-3 years of estimates
>Understand core properties and access-pattern in your design then decide DB and tech
>If you have N choices, evaluate them all
# Some Concepts
### Kafka
[Kafka Notes](Kafka)
### Sockets
Socket is the combination of [SourceIp, SourcePort, DestinationIp, Destination Port] this uniquely identifies a connection. Theoretically one client can hold 64k connections to a single sourceIp, serverIp, serverPort combo based on varying sourcePort numbers.
### Connection Pooling
Servers keep a pool of open connections that are used for firing DB queries and are re-usable. This reduces the latency of creating a new connection every-time for a new query.
### Soft Delete
Having a **soft_delete** column helps where we wanna keep the data for tracking, archival and audit. Also deleting data would require re-balancing of partitions in some cases.
Data can be kept persisted for **N** days and then hard-deleted.
### New Cache Concepts
#### Debounce
If there are N hits on cache for non existent data, let only one request go to DB to fetch data and N - 1 wait instead of sending them to DB as well.
#### Load Leak
In case of a cache heavy system, don't under provision your database because if cache goes down, the flooded calls on DB won't take it down. 
How much to provision? -> Leak roughly 10% load to DB even if there is a cache hit and see if it is able to handle load. This way, in memory buffer pools of the DB will be filled up with those 10% requests data and will be warmed up.
>Note: We can serve request from cache and async way mai fire the query to DB.
# Some Tech
### DB with KV and Expiry
- Redis and DynamoDB -> Redis DB is stored In-Memory and if dataset is small, it is an efficient choice. Data storage simplicity++
- DynamoDB is a Managed solution on AWS, If we use our own REDIS solution, it will incur cost for devops team to manage it.
- If we use DynamoDB for certain use case, it would result in vendor lock-in. It means we cant migrate easily from AWS to some other cloud since DynamoDB is proprietary DB provided by AWS.
- DynamoDB Accelerator -> Fully managed cache for DynamoDB (write through cache).
# How To Scale ?
Scale-up in a bottom up manner. Scale dependent service first. E.g -> before scaling up servers, scale up the DB the servers talk to.
### Scaling Up DB
#### Read Replicas
- If system is read heavy i.e. read:write ratio is around 8:1 or  9:1, create read replicas.
- Now, either our API servers needs to be aware of read replica or we'll create a reverse-proxy server that our api-server talks to and that proxy server routes the request to replicas/master.
>Reads can also go to master (e.g ->. critical reads)
#### Sharding
- If we have a lot of write data, we create shards where each shard holds subset of data.

>If we use a proxy server, then our API servers will have connection pool for proxy server thinking it's DB server and proxy server will have connection pool for actual DBs. e.g -> ProxySQL for RDS in AWS.

### Delegate
Delegate all tasks to async workers that don't have to be synchronous.
#### Message Queues
Only one consumer can read a particular packet, it gets lost for others.
e.g-> RabbitMQ, SQS, Service Bus Queue
#### Message Streams
Multiple types of consumers can read same message.
e.g-> Kafka, Kinesis

