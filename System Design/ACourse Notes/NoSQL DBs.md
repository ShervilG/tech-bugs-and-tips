#nosql #db #systemdesign 
# Definition
NoSQL is not a good naming, always talk about type: Document DB, Key-Value based DB, columnar storage etc.
# Document Based DBs
Like MongoDB, CosmosDB, ElasticSearch.
- Stores data in mostly json type documents
- Supports complex operations like min, max etc etc
- Supports partial updates (e.g -> update xyz set xyz.name = 'hello'), similar to Relational DBs
# Key Value Store
Like REDIS, DynamoDB, Aerospike.
Assumes that access pattern will always be key-value based. It can be heavily partitioned based on the key. 

**Downside:** Generally no complex queries.
# Column Oriented Storage
Like Amazon Redshift, Google BigQuery (mostly used for analytics)
They support gigantic workload. Mostly used when large number of rows and few number of columns are queried. Aggregate queries work really well.

**Advantage:** If we do select avg(price) from table where ts > 100; A relational DB will fetch all rows and then project the selected columns, a columnar db will only fetch the required columns for the rows.
# Graph Based DB
>Note: Mushkil to manage in prod !! :(

Like Neo4J, DGraph.

Stores data as nodes and edges. Great for modelling social behaviours, recommendations etc.
# When to use NoSQL DBs ?
When you don't need constraints, ACID, data can stay denormalised and need partitionability out of the box. Also schemaless for cases like ProductDetails can be achieved with dbs like Mongo.
>Note: Stick with relation DBs initially if u really need to scale then experiment with NoSQL


