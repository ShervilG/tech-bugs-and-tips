#systemdesign #basics 
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





