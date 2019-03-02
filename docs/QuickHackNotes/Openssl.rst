Some Quick notes on openssl
=====

General OpenSSL Commands
-----

Generate a new private key and Certificate Signing Request
``openssl req -out CSR.csr -new -newkey rsa:2048 -nodes -keyout privateKey.key``


Generate a self-signed certificate
``openssl req -x509 -sha256 -nodes -days 365 -newkey rsa:2048 -keyout privateKey.key -out certificate.crt``


Generate a certificate signing request (CSR) for an existing private key
``openssl req -out CSR.csr -key privateKey.key -new``


Generate a certificate signing request based on an existing certificate
``openssl x509 -x509toreq -in certificate.crt -out CSR.csr -signkey privateKey.key``


Remove a passphrase from a private key
``openssl rsa -in privateKey.pem -out newPrivateKey.pem``



Checking Using OpenSSL
-----

Check a Certificate Signing Request (CSR)
``openssl req -text -noout -verify -in CSR.csr``

Check a private key
``openssl rsa -in privateKey.key -check``

Check a certificate
``openssl x509 -in certificate.crt -text -noout``

Check a PKCS#12 file (.pfx or .p12)
``openssl pkcs12 -info -in keyStore.p12``


Debugging Using OpenSSL
-----

Check an MD5 hash of the public key to ensure that it matches with what is in a CSR or private key

::


    openssl x509 -noout -modulus -in certificate.crt | openssl md5
    openssl rsa -noout -modulus -in privateKey.key | openssl md5
    openssl req -noout -modulus -in CSR.csr | openssl md5


Check an SSL connection. All the certificates (including Intermediates) should be displayed
``openssl s_client -connect www.paypal.com:443``





Converting Using OpenSSL
-----

Convert a DER file (.crt .cer .der) to PEM
``openssl x509 -inform der -in certificate.cer -out certificate.pem``

Convert a PEM file to DER
``openssl x509 -outform der -in certificate.pem -out certificate.der``

Convert a PKCS#12 file (.pfx .p12) containing a private key and certificates to PEM
``openssl pkcs12 -in keyStore.pfx -out keyStore.pem -nodes``

You can add -nocerts to only output the private key or add -nokeys to only output the certificates.


Convert a PEM certificate file and a private key to PKCS#12 (.pfx .p12)
``openssl pkcs12 -export -out certificate.pfx -inkey privateKey.key -in certificate.crt -certfile CACert.crt



Some vefirication commands
------

::



    echo | openssl s_client -connect www.example.com:443 2>/dev/null | openssl x509 -noout -dates

    echo | openssl s_client -servername shellhacks.com -connect www.example.com:443 2>/dev/null | openssl x509 -noout -issuer

    echo | openssl s_client -servername shellhacks.com -connect www.example.com:443 2>/dev/null | openssl x509 -noout -subject

    echo | openssl s_client -servername shellhacks.com -connect www.example.com:443 2>/dev/null | openssl x509 -noout -issuer -subject -dates

    echo | openssl s_client -servername shellhacks.com -connect www.example.com:443 2>/dev/null | openssl x509 -noout -text | grep 'Signature Algorithm'





How to create a self-signed SSL Certificate For your Apache
-----

Step 1: Generate a Private Key
``openssl genrsa -des3 -out server.key 1024``

Step 2: Generate a CSR (Certificate Signing Request)

``openssl req -new -key server.key -out server.csr``

Step 3: Remove Passphrase from Key
``cp server.key server.key.org``
``openssl rsa -in server.key.org -out server.key``

Step 4: Generating a Self-Signed Certificate
``openssl x509 -req -days 365 -in server.csr -signkey server.key -out server.crt``

Step 5: Installing the Private Key and Certificate
When Apache with mod_ssl is installed, it creates several directories in the Apache config directory. The location of this directory will differ depending on how Apache was compiled.

``cp server.crt /usr/local/apache/conf/ssl.crt``
``cp server.key /usr/local/apache/conf/ssl.key``

Step 6: Configuring SSL Enabled Virtual Hosts

::

    SSLEngine on
    SSLCertificateFile /usr/local/apache/conf/ssl.crt/server.crt
    SSLCertificateKeyFile /usr/local/apache/conf/ssl.key/server.key
    SetEnvIf User-Agent ".*MSIE.*" nokeepalive ssl-unclean-shutdown
    CustomLog logs/ssl_request_log \
        "%t %h %{SSL_PROTOCOL}x %{SSL_CIPHER}x \"%r\" %b"

Step 7: Restart Apache and Test

::

    /etc/init.d/httpd stop
    /etc/init.d/httpd stop







Debugging connect problems
-----

::


    Problems connecting to the server with a browser can have many reasons, many of them on the client (proxy, DNS, general IE dumbness).

    So, if you encounter problems connecting with SSL, try another browser and/or look into the settings. If even this doesn't work, you can use OpenSSL to debug the problem.

    bb@www$ openssl s_client -connect no-such-machine:443
    gethostbyname failure 	# Error resolving this DNS name. Connect with the IP address.
    connect:errno=2

    bb@www$ openssl s_client -connect www1.tud.at:443
    connect: Connection refused		
    connect:errno=111
    # No SSL server on this port. Double-check the Listen and Port directives.

    bb@www$ openssl s_client -connect apcenter.apcinteractive.net:443
    # everything OK. OpenSSL shows the information it obtained from the server.
    CONNECTED(00000003)
    depth=0 /C=at/ST=Wien/L=Wien/O=APC interactive/OU=Lifecycle Management/CN=apcenter.apcinteractive.net/Email=bb@apcinteractive.net
    verify error:num=18:self signed certificate
    verify return:1
    depth=0 /C=at/ST=Wien/L=Wien/O=APC interactive/OU=Lifecycle Management/CN=apcenter.apcinteractive.net/Email=bb@apcinteractive.net
    verify return:1
    ---
    Certificate chain
    0 s:/C=at/ST=Wien/L=Wien/O=APC interactive/OU=Lifecycle Management/CN=apcenter.apcinteractive.net/Email=bb@apcinteractive.net
    i:/C=at/ST=Wien/L=Wien/O=APC interactive/OU=Lifecycle Management/CN=apcenter.apcinteractive.net/Email=bb@apcinteractive.net
    ---
    Server certificate
    -----BEGIN CERTIFICATE-----
    MIIC0TCCAjoCAQAwDQYJKoZIhvcNAQEEBQAwgbAxCzAJBgNVBAYTAmF0MQ0wCwYDV
    [...]
    9ucXUnk=
    -----END CERTIFICATE-----
    subject=/C=at/ST=Wien/L=Wien/O=APC interactive/OU=Lifecycle Management/CN=apcenter.apcinteractive.net/Email=bb@apcinteractive.net
    issuer=/C=at/ST=Wien/L=Wien/O=APC interactive/OU=Lifecycle Management/CN=apcenter.apcinteractive.net/Email=bb@apcinteractive.net
    ---
    No client certificate CA names sent
    ---
    SSL handshake has read 1281 bytes and written 320 bytes
    ---
    New, TLSv1/SSLv3, Cipher is EDH-RSA-DES-CBC3-SHA
    Server public key is 1024 bit
    SSL-Session:
        Protocol  : TLSv1
        Cipher    : EDH-RSA-DES-CBC3-SHA
        Session-ID: 49ACE1CF484A67D2C476B923D52110A6FCA1A7CE53D76DF7F233DEBF2333D4FB
        Session-ID-ctx:
        Master-Key: 00E9FA964253752294ECD69C18ADBA527B7170C112E2B3BCB25EA8F4FD847EC46E1FF0194EF8E16985B5E38BF6F12131
        Key-Arg   : None
        Start Time: 980696025
        Timeout   : 300 (sec)
        Verify return code: 0 (ok)
    ---
    [Enter: 
    GET / HTTP/1.0
    and press RETURN twice]
    HTTP/1.1 200 OK
    Date: Sun, 28 Jan 2001 15:34:58 GMT
    Server: Apache/1.3.9 (Win32) mod_ssl/2.4.9 OpenSSL/0.9.4
    Cache-Control: no-cache, no-store, must-revalidate, private
    Expires: 0
    Pragma: no-cache
    X-Powered-By: PHP/4.0.4
    Last-Modified: Sun, 28 Jan 2001 15:35:00 GMT
    Connection: close
    Content-Type: text/html

    <!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.0 Transitional//EN">
    <html>
    # the server shows its main document


Some more unsorted Commands
-----

::


    openssl req -config openssl.cnf -new -out my-server.csr
    openssl rsa -in privkey.pem -out my-server.key
    openssl x509 -in my-server.csr -out my-server.cert -req -signkey my-server.key -days 365
    openssl x509 -in my-server.cert -out my-server.der.crt -outform DER



Questions
-----

Why we have so many different type of certificate format?



Some External links:
-----

https://www.sslshopper.com/ssl-faq.html

https://www.sslshopper.com/what-is-ssl.html

https://www.sslshopper.com/article-most-common-openssl-commands.html

https://www.sslshopper.com/article-how-to-create-and-install-an-apache-self-signed-certificate.html

https://serverguy.com/security/types-of-ssl-certificates/

http://tud.at/programm/apache-ssl-win32-howto.php3

http://slacksite.com/apache/certificate.php

http://www.g-loaded.eu/2005/11/10/be-your-own-ca/

http://www.eclectica.ca/howto/ssl-cert-howto.php *

https://www.openssl.org/docs/

https://www.openssl.org/docs/manmaster/man1/

https://www.openssl.org/docs/faq.html

https://www.openssl.org/docs/standards.html

https://www.akadia.com/services/ssh_test_certificate.html

https://www.akadia.com/html/publications.html

