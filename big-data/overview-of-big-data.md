### Data Warehouse

* Traditional data warehouse
  * Use Extraction, Transform and Load\(ETF\) to load data from different data sources to data warehouse

### NoSQL Database

* Key-Value Pairs storage
* Retrieval and Storage, Pre-processing, Analysis as different layers

### Big Data Technologies![](/assets/Big Data Stack.png)

* * Big Data Frameworks: Hadoop, HBase, Hive
* Big Data should be **used with caution **under
  * Small datasets/low data growth
  * advanced algorithms
  * infrastructure replacement
  * task level parallelism
  * random data access



Data Storage

* Traditional RDBMS
* ![](/assets/RDBMS.png)
* \(By Scifipete - Own work, CC BY-SA 3.0, https://commons.wikimedia.org/w/index.php?curid=11506013\)



Google DFS and HDFS

Low Level: Storage and Scheduling, High Level: Interactivity 

* HDFS - Distributed File System
* YARN : Resource Manager
  * on top of applicaitons
  * shared across applications
  * Data Computation Framework = Resource Manager + Node Manager
    * Every machine gets a Node Manager
    * Master Node\(NameNode in HDFS\): Manage File System's metadata
    * Slave Node\(DataNode in HDFS\): Stored the real data\(persisted on disk\)
    * ![](/assets/HDFSArchitecture.png)
    * ![](/assets/Yarn1.png)
    * * Each Container is a Machine
* 


