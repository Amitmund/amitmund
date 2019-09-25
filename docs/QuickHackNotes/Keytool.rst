Quick notes on java keytool commands
=====


Example:
=====

.. codeblock:: Note

        Example path:
        $JAVA_HOME/jre/lib/security/cacerts

        $JAVA_HOME/bin/keytool -import -trustcacerts -keystore $JAVA_HOME/jre/lib/security/cacerts \
        -storepass changeit  -alias amund1 -file intermediary.cer

        $JAVA_HOME/bin/keytool -import -trustcacerts -keystore $JAVA_HOME/jre/lib/security/cacerts \
        -storepass changeit  -alias amund2 -file root.cer

        /a/java64/jdk1.8.0/bin/keytool  -list -v -keystore /a/java64/jdk1.8.0/jre/lib/security/cacerts






Some Enternal Links
-----
https://www.sslshopper.com/article-most-common-java-keytool-keystore-commands.html


