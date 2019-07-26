# mongodb

## Papers
- [Implementation of Cluster-wide Logical Clock and Causal Consistency in MongoDB](https://dl.acm.org/citation.cfm?id=3314049)

***Important:*** mongoDB@SIGMOD2019

## Videos
- [Implementation of Cluster-Wide Causal Consistency in MongoDB](https://www.mongodb.com/presentations/implementation-of-cluster-wide-causal-consistency-in-mongodb)

***Important:*** mongoDB offical site. (Not available yet!)

- [ReadConcern and WriteConcern MongoDB](https://youtu.be/HQRtW8OSkDY)

Sep 2018

## Jepsen Tests
- [Jepsen: MongoDB stale reads](https://aphyr.com/posts/322-jepsen-mongodb-stale-reads)

- [MongoDB 3.4.0-rc3](https://jepsen.io/analyses/mongodb-3-4-0-rc3)

Kyle Kingsbury, 2017-02-07

- [MongoDB 3.6.4](https://jepsen.io/analyses/mongodb-3-6-4)

***Important:*** Kit Patella, 2018-10-23

> We’ll also discuss MongoDB’s new support for causal consistency (CC) in version 3.6.4 and 4.0.0-rc1, 
and show that sessions prevent anomalies so long as user stick to majority reads and writes. 
However, with MongoDB’s default consistency levels, CC sessions fail to provide the claimed invariants.

## Articles
- [Causal Guarantees are Anything but Casual](https://engineering.mongodb.com/post/ryp0ohr2w9pvv0fks88kq6qkz9k9p3)

***Important:*** Aly Cabral, October 23, 2018 

## Code
- [mongodb/specifications @ github](https://github.com/mongodb/specifications/blob/master/source/causal-consistency/causal-consistency.rst)

***Important:*** Specification for causal consistency in mongoDB

## mongoDB Issues
- [Causal Consistency Violation for local read/write concerns in Jepsen Sharded Cluster Test](https://jira.mongodb.org/browse/SERVER-35316)

May 2018
