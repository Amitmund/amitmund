#################################################################################

# Key Store:
    Holds Private key and Certified Public key of own application.

# Trust Store:
    Holds Certified Public keys of other applications.

# For java:
    keytool: is the tool to work with 'Key store' and the 'Trust Store'.

#################################################################################

# Notes:
https://bootstrap-it.com/encryption/

x.509 certificate encodeing:
    
# Free CA:
    www.cacert.org
    letsencrypt.org
    aws.amazon.com/certificate-manager/ # Only for the amazon resources.

# OpenSSL CLI:
    sudo apt install openssl
    sudo apt-cache search libssl # you can find the latest `libssl` version from this command, so that, the same version can be used on the following command.
    sudo apt install libssl1.0.0

    openssl -h
    openssl enc -h
    openssl # openssl shell.

# Generating a Certificate Signing Request (CSR)
    openssl req -nodes -days 356 -newkey rsa:2048 -keyout keyfile.pem -out certfile.pem

    req: request
    -nodes: not decript the output key
    -days: max time the certificate will be valid.
    -newkey: rsa key of 2048 bit
    -keyout: the name that we want our pem file to have
    -out: output file that we are after.

    certfile.pem # Containing my CSR.
    keyfile.pm # Have my key.

    cat certfile.pem # will display your certficate request.
    
    For Verification:
    openssl req -in certfile.pem -noout -verify -key keyfile.pem
    openssl req -in certfile.pem -noout -text # for further recheck.

# Building your own Private Certificate Authority:

    mkdir ~/my-ca
    cd ~/my-ca
    mkdir signedcerts private
    # signedcert : to keep the signed certificate.
    # private: To keep our private key of our private certificate Authority.

    # Simple database with serial and index.txt
    echo '01' > serial # Simple database.
    touch index.txt # simple database.

    # Creating a configuration file:
    touch caconfig.cnf
    # example from /etc/ssl/
    

export OPENSSL_CONF=~/my-ca/caconfig.cnf
# To create the file.
openssl req -x509 -newkey rsa:2048 -out cacert.pem -outform PEM -days 1825

-x509: to create an actual certificate, and not the CSR.
# never ever forget this pass phrase:
# it will generate `cacert.pem` at the root directory and private key `cakey.pem` under the private folder.

# Then create a self sign certificate:


# Revoking a certificate:
CRL.


# OCSP:
    Online Certificate Status Protocol (OCSP)
    Online Certificate Status Protocol stapling.



# Website Authentication:

Configuring Apache SSL:

sudo a2enmod ssl # a2: Apache2, en: enable, mod: module => Apache2 enable module.
sudo a2ensite default-ssl
# setup your certificate in the configuration.
/etc/apache2/site-available/
# Update over here.
vi default-ssl.conf
    SSLCertificateFile
    SSLCertificateKeyFile
vi /etc/apache/apache2.conf
    ServerName example.com
sudo systemctl restart apache2
#First time it will ask for the pass pharse
sudo systemctl status apache2
#service apache2 reload


# Configuring Named Virtual Hosts:
Subject Alt Name (SAN) CSR. # Not practical.
SNI: # Is the solution.

# For some example:
sni.velox.ch


# How to import root certificate to the browser:
openssl pkcs12 -export -in server_crt.pem -inkey basekey.pem -out browser.p1

openssl s_client -connect google.com:443
    Verify return code: 0 (ok) # ==> Mean all good.
    Verify return code: 21 (unable to verify the first certificate) # ==> Not good.


# HTTP Strict Transport Secutiry (HSTS)
https://bootstrap-it.com/encryption/ 
HSTS
Environment:
Add the first entry to the tag to deploys HSTS. Substitute the second entry to add Preload.

Header always set Strict-Transport-Security: max-age=31536000; includeSubDomains
Header always set Strict-Transport-Security: max-age=31536000; includeSubDomains; preload


# Securing filesystem at rest:
ecryptfs # Work within the filesystem.
https://bootstrap-it.com/encryption/

Ecryptfs
Environment:
From a VirtualBox instance.

sudo modprobe ecryptfs
sudo apt install ecryptfs-utils
sudo adduser mydata
sudo ecryptfs-migrate-home -u mydata
su mydata
ecryptfs-unwrap-passphrase ~/.ecryptfs/wrapped-passphrase
ecryptfs-mount-private
cd /home/mydata
touch newfile
ls
cd /home
ls
diff mydata mydata.h0q-gaF6
sudo rm -r mydata.h9q0gaF6
ecryptfs-setup-swap	
cd /home/mydata/.ecryptfs
ls 
cat Private.mnt
sudo adduser newacc
su newacc
cd ~
ecryptfs-setup-private
ecryptfs-unwrap-passphrase ~/.ecryptfs/wrapped-passphrase
touch newfile
ls

sudo mount -t ecryptfs /home/.ecryptfs/mydata/.Private /home/mydata
mount | grep ecrypt
sudo umount.ecryptfs /home/mydata
mount | grep ecrypt
su mydata
cd /home/.ecryptfs/mydata/.ecryptfs
ls

cd /etc/pam.d
less common-auth
less common-session



#################################################################################


# Links:
    https://stackoverflow.com/questions/10725572/two-way-ssl-clarification

    Note: 
    
    The client certificate should be created by a CA that the server trusts.

    When the client connects to a server that requests client-certificate authentication, the server sends a list of CAs it's willing to accept as part of the client-certificate request. The client is then able to send its client certificate, if it wishes to and a suitable one is available.

    https://tutorialspedia.com/an-overview-of-one-way-ssl-and-two-way-ssl/


   # How One-Way SSL Works?
 
        In one way SSL, only client validates the server to ensure that it receives data from the intended server. For implementing one-way SSL, server shares its public certificate with the clients. 
        Below is the high level description of the steps involved in establishment of connection and transfer of data between a client and server in case of one-way SSL:
        
        1. Client requests for some protected data from the server on HTTPS protocol. This initiates SSL/TLS handshake process. 
        2. Server returns its public certificate to the client along with server hello message.
        3. Client validates/verifies the received certificate. Client verifies the certificate through certification authority (CA) for CA signed certificates.
        4. SSL/TLS client sends the random byte string that enables both the client and the server to compute the secret key to be used for encrypting subsequent message data. The random byte string itself is encrypted with the server’s public key.
        5. After agreeing on this secret key, client and server communicate further for actual data transfer by encryping/decrypting data using this key. 
        Below is the pictorial description explaining how one way ssl works:



#################################################################################
