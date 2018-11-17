Cassandra High Level View
=====


Key structures
-----

.. Note:: In this section we will go through few "Key structures" of cassandra.

Node
~~~~
Where you store your data. It is the basic infrastructure component of Cassandra.

datacenter
~~~~~
A collection of related nodes. A datacenter can be a physical datacenter or virtual datacenter. Different workloads should use separate datacenters, either physical or virtual. Replication is set by datacenter. Using separate datacenters prevents Cassandra transactions from being impacted by other workloads and keeps requests close to each other for lower latency. Depending on the replication factor, data can be written to multiple datacenters. datacenters must never span physical locations.

Cluster
~~~~~
A cluster contains one or more datacenters. It can span physical locations.

Commit log
~~~~~
All data is written first to the commit log for durability. After all its data has been flushed to SSTables, it can be archived, deleted, or recycled.

SSTable
~~~~~
A sorted string table (SSTable) is an immutable data file to which Cassandra writes memtables periodically. SSTables are append only and stored on disk sequentially and maintained for each Cassandra table.

CQL Table
~~~~~
A collection of ordered columns fetched by table row. A table consists of columns and has a primary key.


-----


Key components for configuring Cassandra
-----

.. Note:: In this section we will go through few "Key components for configuring Cassandra" of cassandra.

Gossip
~~~~~
A peer-to-peer communication protocol to discover and share location and state information about the other nodes in a Cassandra cluster. Gossip information is also persisted locally by each node to use immediately when a node restarts.

Partitioner
~~~~~
A partitioner determines which node will receive the first replica of a piece of data, and how to distribute other replicas across other nodes in the cluster. Each row of data is uniquely identified by a primary key, which may be the same as its partition key, but which may also include other clustering columns. A partitioner is a hash function that derives a token from the primary key of a row. The partitioner uses the token value to determine which nodes in the cluster receive the replicas of that row. The Murmur3Partitioner is the default partitioning strategy for new Cassandra clusters and the right choice for new clusters in almost all cases.

You must set the partitioner and assign the node a num_tokens value for each node. The number of tokens you assign depends on the hardware capabilities of the system. If not using virtual nodes (vnodes), use the initial_token setting instead.

Replication factor
~~~~~
The total number of replicas across the cluster. A replication factor of 1 means that there is only one copy of each row on one node. A replication factor of 2 means two copies of each row, where each copy is on a different node. All replicas are equally important; there is no primary or master replica. You define the replication factor for each datacenter. Generally you should set the replication strategy greater than one, but no more than the number of nodes in the cluster.

Replica placement strategy
~~~~~
Cassandra stores copies (replicas) of data on multiple nodes to ensure reliability and fault tolerance. A replication strategy determines which nodes to place replicas on. The first replica of data is simply the first copy; it is not unique in any sense. The NetworkTopologyStrategy is highly recommended for most deployments because it is much easier to expand to multiple datacenters when required by future expansion.

When creating a keyspace, you must define the replica placement strategy and the number of replicas you want.

Snitch
~~~~~
A snitch defines groups of machines into datacenters and racks (the topology) that the replication strategy uses to place replicas.

You must configure a snitch when you create a cluster. All snitches use a dynamic snitch layer, which monitors performance and chooses the best replica for reading. It is enabled by default and recommended for use in most deployments. Configure dynamic snitch thresholds for each node in the cassandra.yaml configuration file.

The default SimpleSnitch does not recognize datacenter or rack information. Use it for single-datacenter deployments or single-zone in public clouds. The GossipingPropertyFileSnitch is recommended for production. It defines a node's datacenter and rack and uses gossip for propagating this information to other nodes.

The cassandra.yaml configuration file
~~~~~
The main configuration file for setting the initialization properties for a cluster, caching parameters for tables, properties for tuning and resource utilization, timeout settings, client connections, backups, and security.

By default, a node is configured to store the data it manages in a directory set in the cassandra.yaml file.

In a production cluster deployment, you can change the commitlog-directory to a different disk drive from the data_file_directories.

System keyspace table properties
~~~~~
You set storage configuration attributes on a per-keyspace or per-table basis programmatically or using a client application, such as CQL.


-----

Database Internals
------

.. Note:: In this section we will go through few "Database Internals" of cassandra.


Storage engine
~~~~~
A description about Cassandra's storage structure and engine.

How Cassandra reads and writes data
~~~~~
Understanding how Cassandra stores data.

Data consistency
~~~~~
Topics about how up-to-date and synchronized a row of data is on all replicas.


-----


configuration
------

.. Note:: In this section we will go through few "configuration" of cassandra.


cassandra.yaml
~~~~~
The cassandra.yaml file is the main configuration file for Cassandra.

Cassandra include file
~~~~~
Set environment variables (cassandra.in.sh).

Security
~~~~~
Topics for securing Cassandra.

Configuring gossip settings
~~~~~
Using the cassandra.yaml file to configure gossip.

Configuring the heap dump directory
~~~~~
Analyzing the heap dump file can help troubleshoot memory problems.

Configuring virtual nodes
~~~~~
Topics about configuring virtual nodes.

Using multiple network interfaces
~~~~~
Steps for configuring Cassandra for multiple network interfaces or when using different regions in cloud implementations.

Configuring logging
~~~~~
Cassandra logging functionality using Simple Logging Facade for Java (SLF4J) with a logback backend.

Commit log archive configuration
~~~~~
Cassandra provides commit log archiving and point-in-time recovery.

Change Data Capture (CDC) logging
~~~~~
Change Data Capture (CDC) logging captures changes to data.

Generating tokens
~~~~~
If not using virtual nodes (vnodes), you must calculate tokens for your cluster.

Hadoop support
~~~~~
Cassandra support for integrating Hadoop with Cassandra.


-----


Initializing a cluster
-----

.. Note:: In this section we will go through few "Initialization a cluster" of cassandra.


Initializing a multiple node cluster (single datacenter)
~~~~~
A deployment scenario for a Cassandra cluster with a single datacenter.

Initializing a multiple node cluster (multiple datacenters)
~~~~~
A deployment scenario for a Cassandra cluster with multiple datacenters.

Starting and stopping Cassandra
~~~~~
Topics for starting and stopping Cassandra.


-----

Operations
-----

.. Note:: In this section we will go through few "Operations" of cassandra.


Cassandra operation topics, such as node and datacenter operations, changing replication strategies, configuring compaction and compression, caching, and tuning Bloom filters.

Adding or removing nodes, datacenters, or clusters
~~~~~
Topics for adding or removing nodes, datacenters, or clusters.


Backing up and restoring data
~~~~~
Cassandra backs up data by taking a snapshot of all on-disk data files (SSTable files) stored in the data directory.

Repairing nodes
~~~~~
Node repair topics.

Monitoring Cassandra
~~~~~
Monitoring topics.

Tuning Java resources
~~~~~
Tuning the Java Virtual Machine (JVM) can improve performance or reduce high memory consumption.

Data caching
~~~~~
Data caching topics.

Configuring memtable thresholds
~~~~~
Configuring memtable thresholds to improve write performance.

Configuring compaction
~~~~~
Steps for configuring compaction. The compaction process merges keys, combines columns, evicts tombstones, consolidates SSTables, and creates a new index in the merged SSTable.

Compression
~~~~~
Compression maximizes the storage capacity of Cassandra nodes by reducing the volume of data on disk and disk I/O, particularly for read-dominated workloads.

Testing compaction and compression
~~~~~
Enabling write survey mode.
Tuning Bloom filters
Cassandra uses Bloom filters to determine whether an SSTable has data for a particular row.

Moving data to or from other databases
~~~~~
Solutions for migrating from other databases.

Purging gossip state on a node
~~~~~
Correcting a problem in the gossip state.


-----

Cassandra tools
-----

.. Note:: In this section we will go through few "Cassandra tools" of cassandra.


The nodetool utility
~~~~~
A list of the available commands for managing a cluster.

The cassandra utility
~~~~~
You can start Cassandra 3.0 and 3.1 by adding them to the cassandra-env.sh file (package or tarball installations) or entering them at the command line in tarball installations.

The cassandra-stress tool
~~~~~
A Java-based stress testing utility for basic benchmarking and load testing a Cassandra cluster.

SSTable utilities
~~~~~
Tools for using, upgrading, and changing Cassandra SSTables.


.. Note:: Will go through in more details about these.

-----
