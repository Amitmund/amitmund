
#----------------------------------------------------------------
# Links:

https://stackoverflow.com/questions/44024170/upgrading-cassandra-without-losing-the-current-data

https://dba.stackexchange.com/questions/71781/cassandra-maintenance

#----------------------------------------------------------------

Steps for upgrade cassandra version
1. Run nodetool drain before shutting down the existing Cassandra service.
nodetool drain -h hostname
2. Stop cassandra services.
service cassandra stop

3. Back up your Cassandra configuration files from the old installation to safe place.

4. Update java version.
apt-get update
apt-get install oracle-java8-set-default
java -version

5. Install the new version of Apache Cassandra.
apt-get update
apt-get install cassandra=3.7.0

If you are running Cassandra from a source you should download the latest tar.gz instead of using the package manager.

6. Configure the new product. Review, compare, merge and/or update any modifications you have previously made into the new configuration files for the new version (cassandra.yml, cassandra-env.sh, etc.).

7. Start the cassandra services.
service cassandra start
Check the logs for warnings, errors, and exceptions.
tail -f /var/logs/cassandra/system.log # or path where you set your logs.

8. Run nodetool upgradesstables
nodetool upgradesstables

9. Check the logs for warnings, errors, and exceptions.
tail -f /var/logs/cassandra/system.log # or path where you set your logs.

10. Check the status of the cluster
nodetool -h hostname status

11. Repeat theses upgrade steps on each node in the cluster.

#----------------------------------------------------------------
