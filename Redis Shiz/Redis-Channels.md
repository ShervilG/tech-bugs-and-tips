#redis

# About
***
Used as pub sub queues, where a single message is pushed to multiple subscribers. On one connection, you can connect to multiple channels. (One REDIS instance typically can handle 10000 connections or 4 connections per memory MB, whichever is larger).

# Advantages
***
- They are lightweight.
- Older messages are not saved.
- Very fast data transfer.
- A Redis instance with GBs of memory can handle millions of channels easily.
- Redis' Pub/Sub exhibits _at-most-once_ message delivery semantics.
- Message size limit can be in 10-20MBs
