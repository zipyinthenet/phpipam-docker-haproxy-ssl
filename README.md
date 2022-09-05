#PHPIPAM with docker-compose

With this version you have a compose file with:

- phpipam web instance
- phpipam cron instance
- phpipam Mysql instance
- HAProxy instance configure with bridge

* * *

Network in compose is defined to create by the name net-phpipam , when you run this compose you can get a new bridge network that works with all the image that we run as containers 

The idea for this network is that , clients can connect to 443/tcp and 80/tcp to haproxy that servers SSL with cert , and do the proxy to connect to web container that is running on the network that we defined and created in compose when we run the compose file.

the only things you need to do is:

- create a self signed cert or use your cert if u have one , and move or copy certs to haproxy_ssl

- you dont have to write nothing on file haproxy_cfg/haproxy.cfg , there is configured yet to do a proxy pass to containers (also the containers have a name defined)

- simple run 'docker-compose -f docker-compose.yml up -d' to run all the containers

if you want to comprobe containers:

- docker-compose status

- docker ps -a

- docker networks inspect  (this command allows you to see networks of containers if u need it)

- docker inspect <name of container>

[phpipam.net](https://phpipam.net/documents/all-documents/)

[hub.docker.com/r/phpipam](https://hub.docker.com/r/phpipam/phpipam-www)