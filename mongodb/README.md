# mongodb

## Papers
- [SIGMOD2019: Implementation of Cluster-wide Logical Clock and Causal Consistency in MongoDB](https://dl.acm.org/citation.cfm?id=3314049)
- [VLDB2019: Tunable Consistency in MongoDB](http://www.vldb.org/pvldb/vol12/p2071-schultz.pdf)

## Videos
- [Implementation of Cluster-Wide Causal Consistency in MongoDB](https://www.mongodb.com/presentations/implementation-of-cluster-wide-causal-consistency-in-mongodb)

***Important:*** mongoDB offical site. (Not available yet!)

- [ReadConcern and WriteConcern MongoDB (Sep 2018)](https://youtu.be/HQRtW8OSkDY)

## Official Documentation
- [The MongoDB 4.2 Manual](https://docs.mongodb.com/manual/)
- [Read Concerns](https://docs.mongodb.com/manual/reference/read-concern/?_ga=2.214513239.1537524606.1571995321-1885120209.1571995321#readconcern-option)
- [Read Isolation, Consistency, and Recency](https://docs.mongodb.com/manual/core/read-isolation-consistency-recency/#read-isolation-consistency-and-recency)

## Jepsen Tests
- [Call Me Maybe: MongoDB 2.4.3 (2013-05-18)](https://aphyr.com/posts/284-call-me-maybe-mongodb)

> In this post, we’ll see MongoDB drop a phenomenal amount of data.

- [Jepsen: MongoDB stale reads 2.6.7 (2015-04-20)](https://aphyr.com/posts/322-jepsen-mongodb-stale-reads)

> Mongo’s consistency model is broken by design: 
not only can “strictly consistent” reads see stale versions of documents, 
but they can also return garbage data from writes that never should have occurred.

- [MongoDB 3.4.0-rc3 (2017-02-07); Kyle Kingsbury](https://jepsen.io/analyses/mongodb-3-4-0-rc3)

> In this Jepsen analysis, we develop new tests which show the MongoDB v0 replication protocol is intrinsically unsafe, 
allowing the loss of majority-committed documents. 
In addition, we show that the new v1 replication protocol has multiple bugs, 
allowing data loss in all versions up to MongoDB 3.2.11 and 3.4.0-rc4. 
While the v0 protocol remains broken, 
fixes for v1 are available in MongoDB 3.2.12 and 3.4.0, and now pass the expanded Jepsen test suite. 

- [MongoDB 3.6.4 (2018-10-23); Kit Patella](https://jepsen.io/analyses/mongodb-3-6-4)

> We’ll also discuss MongoDB’s new support for causal consistency (CC) in version 3.6.4 and 4.0.0-rc1, 
and show that sessions prevent anomalies so long as user stick to majority reads and writes. 
However, with MongoDB’s default consistency levels, CC sessions fail to provide the claimed invariants.

## Evergreen CI
- [Evergreen Continuous Integration: Why We Reinvented The Wheel; Kyle Erf, July 27, 2016](https://engineering.mongodb.com/post/evergreen-continuous-integration-why-we-reinvented-the-wheel/)

- [Testing Linearizability with Jepsen and Evergreen: "Call Me Continuously!"; Jonathan Abrahams, February 16, 2017](https://engineering.mongodb.com/post/testing-linearizability-with-jepsen-and-evergreen-call-me-continuously)

> In our case we have added linearizable reads to MongoDB 3.4 and use Jepsen to test it.

## Articles
- [Causal Guarantees are Anything but Casual (Aly Cabral, October 23, 2018)](https://engineering.mongodb.com/post/ryp0ohr2w9pvv0fks88kq6qkz9k9p3)

- [Causal Consistency and Read and Write Concerns (MongoDB Official Site)](https://docs.mongodb.com/manual/core/causal-consistency-read-write-concerns/)

## Code
- [mongodb/specifications @ github](https://github.com/mongodb/specifications/blob/master/source/causal-consistency/causal-consistency.rst)

***Important:*** Specification for causal consistency in mongoDB

## TLA at/for mongoDB
- [mongo-repl-tla](https://github.com/tlaplus/Examples/tree/master/specifications/mongo-repl-tla)
- [tla-at-mongodb@reddit](https://www.reddit.com/r/tlaplus/comments/76zule/tla_at_mongodb/)

Unavailable to me (hfwei)!

- [Fixing a MongoDB Replication Protocol Bug with TLA+ (TLA+ Conf, William Schultz (MongoDB), Sep, 2019)](https://conf.tlapl.us/program/williamschultz/)

## mongoDB Issues
- [Causal Consistency Violation for local read/write concerns in Jepsen Sharded Cluster Test (May 2018)](https://jira.mongodb.org/browse/SERVER-35316)

## forum
### [mongodb-user@googlegroup](https://groups.google.com/forum/#!forum/mongodb-user)

### mongodb@Hacker News
  - [MongoDB 3.4.0-rc3 (jepsen.io); aphyr on Feb 7, 2017](https://news.ycombinator.com/item?id=13590385)

  ```
  Bigger news is that Jepsen tests are now part of the MongoDB continuous integration suite EverGreen.
  ```
  - [MongoDB 3.4.0-rc3 (jepsen.io); kenwalger on Feb 7, 2017](https://news.ycombinator.com/item?id=13590457)

  > MongoDB 3.4 passes the rigorous and tough Jepsen test. 
    Jepsen designs tests to make databases fail in terms of data consistency, correctness, and safety... 
    MongoDB 3.4 passed through their newest tests.

I think that this really shows how mature of a Database MongoDB is. 
