## Database

* Sharding
  * vertical sharding
  * horizontal sharding
    * [Consistent Hashing](https://en.wikipedia.org/wiki/Consistent_hashing)
      * minimize data migration
      * Virtual node
  * to prevent [single point failure](https://en.wikipedia.org/wiki/Single_point_of_failure)
* [Replica](https://en.wikipedia.org/wiki/Replication_%28computing%29)
  * SQL - master \(write\) - slave\(read, sync\)
  * NoSQL - 3 virtual node
* Single Point Failure 

#### SQL vs NoSQL

* SQL 
  * structured data
  * multi-indexing
  * transaction
* NoSQL
  * distribution, parallel computing
  * auto-scale
  * replica

NoSQL Databases

* Hard drive based
  * Cassandra
  * MongoDB
* Memory based
  * Redis
  * Memecached
    * no data persistency
* Cloud
  * Dynamo DB
  * [Couchbase](http://horicky.blogspot.in/2012/07/couchbase-architecture.html)

## Cache

Use memory based DB such as Memecached is a common choice

#### Cache Techniques

* Cache Models
  * LRU Cache, LFU Cache
* best practice: db.set\(\), cache.delete\(\)
  * db fails more frequently
  * have problem in multi-process
* Cache Model
  * Cache Aside 
  * Cache Through
* Thundering Herd
  * [Memcache lease get](http://www.cs.utah.edu/~stutsman/cs6963/public/papers/memcached.pdf)
  * [How facebook solve thundering herd](#)
* Dirty Data problem
  * [dirty data](https://www.quora.com/What-does-dirty-mean-in-the-context-of-caching)



