Quick notes on the docker
=====


Command to run a container from docker image
-----

Example:

docker run -d -p 8888:80 --name php_server php_ubuntu

---

Dockerfile
-----

:: 
  # This is a sample image

  From ubuntu:14.04

  MAINTAINER amitmund@gmail.com

  RUN apt-get update
  RUN apt-get install -y apache2
  RUN apt-get install -y curl
  #RUN apt-get install -y php-pear php-fpm php-dev php-zip php-curl php-xmlrpc php-gd php-mysql php-mbstring php-xml libapache2-mod-php

  # Apache config



  EXPOSE 80
  CMD /usr/sbin/apache2ctl -D FOREGROUND

---

To Build an image from Dockerfile
-----

Create a directory for each Dockerfile.


---

Logging to a docker container
-----

Example:

docker exec -it <container_id> /bin/bash

---

