# mongodb-system-model

## Client vs. Server

## [Replica Set](https://docs.mongodb.com/manual/replication/)

### Overview Architecture

> A *replica set* is a group of mongod instances that maintain the same data set.
A replica set contains several data bearing nodes and optionally one *arbiter* node. 
Of the data bearing nodes, one and only one member is deemed the *primary* node, 
while the other nodes are deemed *secondary* nodes.

### [Replica Set Primary](https://docs.mongodb.com/manual/core/replica-set-primary/)

> The primary is the only member in the replica set that receives write operations. 
MongoDB applies write operations on the primary and then records the operations on the primary’s oplog.
Secondary members replicate this log and apply the operations to their data sets.

> The replica set can have at most one primary. 
If the current primary becomes unavailable, an *election* determines the new primary.

### [Replica Set Secondary Members](https://docs.mongodb.com/manual/core/replica-set-secondary/)

> A secondary maintains a copy of the primary’s data set.
To replicate data, a secondary applies operations from the primary’s oplog to its own data set in an asynchronous process.

### [Replica Set Arbiter](https://docs.mongodb.com/manual/core/replica-set-arbiter/)

> An arbiter does not have a copy of data set and cannot become a primary.
Replica sets may have arbiters to add a vote in elections for primary. 
Arbiters always have exactly 1 election vote, 
and thus allow replica sets to have an uneven number of voting members 
without the overhead of an additional member that replicates data.

### [Replica Set Oplog](https://docs.mongodb.com/manual/core/replica-set-oplog/#replica-set-oplog)

> All replica set members contain a copy of the oplog, in the *local.oplog.rs collection*.

> MongoDB applies database operations on the primary and then records the operations on the *primary*’s oplog.
The secondary members then copy and apply these operations in an asynchronous process. 

### [Replica Set Data Synchronization](https://docs.mongodb.com/manual/core/replica-set-sync/#replica-set-sync)

> In order to maintain up-to-date copies of the shared data set, 
secondary members of a replica set sync or replicate data from other members.
MongoDB uses two forms of data synchronization: 
*initial sync* to populate new members with the full data set, 
and *replication* to apply ongoing changes to the entire data set.

### [Replica Set Elections](https://docs.mongodb.com/manual/core/replica-set-elections/)

> Replica sets use elections to determine which set member will become primary.

> The replica set *cannot process write operations* until the election completes successfully.
The replica set *can continue to serve read queries* if such queries are configured to run on secondaries.

#### [Replica Set Protocol Version](https://docs.mongodb.com/manual/reference/replica-set-protocol-versions/)

> Starting in version 4.0, MongoDB only supports replica set protocol version 1 (pv1).

- [Detection of Simultaneous Primaries](https://docs.mongodb.com/manual/reference/replica-set-protocol-versions/#detection-of-simultaneous-primaries)

> In some circumstances, two nodes in a replica set may transiently believe that they are the primary, 
but at most, one of them will be able to complete writes with { w: "majority" } write concern.

#### [Heartbeats](https://docs.mongodb.com/manual/core/replica-set-elections/#heartbeats)

> *Replica set members send heartbeats (pings) to each other every two seconds.* 
If a heartbeat does not return within 10 seconds, the other members mark the delinquent member as inaccessible.

### Problems
- How to guarantee ["Idempotence"](https://docs.mongodb.com/manual/core/replica-set-oplog/#replica-set-oplog)?

> Each operation in the oplog is *idempotent*. 
That is, oplog operations produce the same results whether applied once or multiple times to the target dataset.

- Which is correct?

> Push: [To facilitate replication](https://docs.mongodb.com/manual/core/replica-set-oplog/#replica-set-oplog), 
all replica set members send *heartbeats* (pings) to all other members.
Any secondary member can import oplog entries from any other member.

> Pull: [Secondary members *copy the oplog from* their sync from source](https://docs.mongodb.com/manual/core/replica-set-sync/#replication) 
and apply these operations in an asynchronous process.

> Pull: [MongoDB secondaries *pull* oplogs from any nodes that have more up-to-date oplogs](https://github.com/visualzhou/mongo-repl-tla),
which is different from the push model in Raft.

## Shard
