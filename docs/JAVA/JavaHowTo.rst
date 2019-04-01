JavaHowTo
=====

Java thread dump
#####

.. Note:: jstack `java_pid` > OutputFile
          Thread dump: Momory dump of only thread.

::

    Lets say the process runs a port 8443, Then please find the following script, that will take the thread dump of the same.

    JAVA_PID=$(lsof -ti :8443)
    CUR_TIME=$(date +%Y-%m-%d-%H-%M)
    CUR_CPU=$(ps -p $JAVA_PID -o %cpu| tail -1)
    echo "current cpu use: $CUR_CPU" >> /var/tmp/jstack_dump-$CUR_TIME
    jstack $JAVA_PID >> /var/tmp/jstack_dump-$CUR_TIME


Heap dump
#####

`kill -3 pid` // Complete memory dump.


Reading core dump:
#####

off=$(($RANDOM % ($(stat -c "%s" core.7916)/4096))); dd if=core.7916 bs=4096 skip=$off count=1 | xxd|less

jmap -dump:file=heapdump.bin 5749