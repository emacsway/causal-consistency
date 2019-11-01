# mongodb-causal-consistency

## Papers
- [SIGMOD2019: Implementation of Cluster-wide Logical Clock and Causal Consistency in MongoDB](https://dl.acm.org/citation.cfm?id=3314049)

## Videos
- [Implementation of Cluster-Wide Causal Consistency in MongoDB @ mongoDB offical site](https://www.mongodb.com/presentations/implementation-of-cluster-wide-causal-consistency-in-mongodb)

## Articles
- [Causal Guarantees are Anything but Casual (Aly Cabral, October 23, 2018)](https://engineering.mongodb.com/post/ryp0ohr2w9pvv0fks88kq6qkz9k9p3)

- [Causal Consistency Violation for local read/write concerns in Jepsen Sharded Cluster Test (May 2018)](https://jira.mongodb.org/browse/SERVER-35316)

> ***Response:*** We've created DOCS-11866 and updated the documentation 
to recommend read and write concern configurations that are always safe, even during network partitions. 
When used with causal consistency, the combination of read concern majority and write concern majority 
always safely delivers causal guarantees. 

## TLA/TLAPS
- [mongo-repl-tla](https://github.com/tlaplus/Examples/tree/master/specifications/mongo-repl-tla)
- [tla-at-mongodb@reddit](https://www.reddit.com/r/tlaplus/comments/76zule/tla_at_mongodb/)
- [Fixing a MongoDB Replication Protocol Bug with TLA+ (TLA+ Conf, William Schultz (MongoDB), Sep, 2019)](https://conf.tlapl.us/program/williamschultz/)
