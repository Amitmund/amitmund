Cassandra In details
=====

-----

.. Tip::
        Reference Link: https://docs.datastax.com/en/cassandra/3.0/index.html

-----

About Apache Cassandra
-----

.. Note:: About Apache Cassandra.

Overview of Apache Cassandra
~~~~~

Apache Cassandra™ is a massively scalable open source NoSQL database. Cassandra is perfect for managing large amounts of structured, semi-structured, and unstructured data across multiple datacenters and the cloud. Cassandra delivers continuous availability, linear scalability, and operational simplicity across many commodity servers with no single point of failure, along with a powerful dynamic data model designed for maximum flexibility and fast response times.


How does Cassandra work?
~~~~~

Cassandra’s built-for-scale architecture means that it is capable of handling petabytes of information and thousands of concurrent users/operations per second.

- Cassandra is a partitioned row store database
- Automatic data distribution
- Built-in and customizable replication
- Cassandra supplies linear scalability

How is Cassandra different from relational databases?
~~~~~

Cassandra is designed from the ground up as a distributed database with peer-to-peer communication. As a best practice, queries should be one per table. Data is denormalized to make this possible. For this reason, the concept of JOINs between tables does not exist, although client-side joins can be used in applications.

What is NoSQL?
~~~~~

Most common translation is "Not only SQL", meaning a database that uses a method of storage different from a relational, or SQL, database.

What is CQL?
~~~~~

Cassandra Query Language (CQL) is the primary interface into the Cassandra DBMS. Using CQL is similar to using SQL (Structured Query Language). CQL and SQL share the same abstract idea of a table constructed of columns and rows. The main difference from SQL is that Cassandra does not support joins or subqueries. Instead, Cassandra emphasizes denormalization through CQL features like collections and clustering specified at the schema level.


How can I move data to/from Cassandra?
~~~~~

Data is inserted using the CQL INSERT command, the CQL COPY command and CSV files, or sstableloader. But in reality, you need to consider how your client application will query the tables, and do data modeling first. The paradigm shift between relational and NoSQL means that a straight move of data from an RDBMS database to Cassandra will be doomed to failure.

What other tools come with Cassandra?
~~~~~

Cassandra automatically installs nodetool, a useful command-line management tool for Cassandra. A tool for load-stressing and basic benchmarking, cassandra-stress, is also installed by default.

-----

Understanding the architecture
-----

.. Note:: Understanding the architecture of Cassandra.
