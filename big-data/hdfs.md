### Distributed File System

* File System
  * Long-term information storage
  * Access results of a process later
  * Store large amounts of information
  * enable access of multiple processes
* RAMS
  * Data Stored in Racks
  * Data Partitioning - Data Replication
  * Data Scalability, Fault Tolerance
  * High Concurrency vs low Consistency
* Commodity Cluster
  * not specialized parallel computers\(expensive\), use less-specialized computers for large scale computing
  * Racks connected by network
  * Data Parallel Scalability - Deal with Node Failures
    * Redundant Data Storage
    * Data Parallel Job Start
* Programmability of Big Data 
  * provides programmability on top of DFS
  * requirements
    * support big data operations
      * split volumes of data
      * access fast
      * distribute computation to nodes
    * handle fault tolerance
      * replicate data partitions
      * recover files when needed
    * enable adding more racks
    * optimized for specific data types
      * stream, graph, multimedia, key-value, document, table...
    * Models independent parallel processes over multiple resources
* cloud computing
  * IT infrastructure + Applications to rent over the internet
  * separation of business logic
  * Cloud Service Models - Different levels of engagement
    * IaaS: infrastructure as a service
      * virtual machines, servers, storage, load balancers, network
    * PaaS: Platform
      * Execution runtime, database, web server, development tools
    * SaaS: Software/Application ... 
      * CRM, Email, virtual desktop, communication, games
  * Cloud Service Models
* HDFS
  * splits files across nodes for parallel access
  * node replication
  * customized reading to handle variety of data types
  * Two Key components
    * NameNode for metadata - usually per cluster
      * file name, location in directory, mapping of contents on data node
    * DataNode for block storage - usually per machine![](/assets/HDFS1.png)
      * listens to NameNode for block creation, deletion, replication
        * scalability, fault tolerance, data locality

### Map Reduce

1. Map on each node
   1. generate key-value pairs on each node
2. Sort and Shuffle
   1. Pairs with same key move to the same node
3. Reduce
   1. add the values for the same key

### HDFS Commands

* hadoop fs
  * -copyFromLocal &lt;file&gt; : copy file to HDFS
  * -copyToLocal &lt;file&gt;: copy to local 
  * -ls: List current files
  * -cp: copy within HDFS
  * -rm : delete
* hadoop jar &lt;executable&gt; \[argv\] \[function\]
  * java programs distributed in jar



