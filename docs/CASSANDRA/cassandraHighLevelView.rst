Cassandra High Level View
=====


Understanding the architecture
-----
.. Note:: In this section we will go through few "Understanding the architecture"

Architecture in brief
~~~~~
Essential information for understanding and using Cassandra.

Internode communications (gossip)
~~~~~
Cassandra uses a protocol called gossip to discover location and state information about the other nodes participating in a Cassandra cluster.

Data distribution and replication
~~~~~
How data is distributed and factors influencing replication.

Partitioners
~~~~~
A partitioner determines how data is distributed across the nodes in the cluster (including replicas).

Snitches
~~~~~
A snitch determines which datacenters and racks nodes belong to.

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
