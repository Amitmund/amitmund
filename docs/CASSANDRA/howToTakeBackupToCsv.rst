Taking backup to CSV in Cassandra
=====


.. NOTE::

With My current understanding, if any of the host is down in the Cassandra cluster, 
we will not be able to take a backup of a table to a CSV file, in Cassandra cluster.

To check the culster:

::

  nodetool -u <username> -p <password> status

And you should see all as "UN"



Command to take backup, (Make sure all the cassandra node is up within the culster)

::

  cqlsh -u <username> -p password --ssl --cqlshrc=</path/to/cert> -e "copy <keyspace>.<tablename> to '/path/to/csv/backup/file'"

