

Redis installaton and configuration in CentOS server:


1. Install Redis server

wget http://redis.googlecode.com/files/redis-2.6.12.tar.gz

tar xzf redis-2.6.12.tar.gz

mv redis-2.6.12 /usr/local/redis

cd /usr/local/redis

make


2. Configure Redis Conf

cd /usr/local/redis

cp -v  redis.conf redis_6379.conf

daemonize yes

pidfile /var/run/redis/redis_6379.pid

port 6379

logfile /var/log/redis/redis_6379.log

dir /data/redis
 

3. Setup a Init script to stop/start redis service

wget https://raw.github.com/saxenap/install-redis-amazon-linux-centos/master/redis-server

mv redis-server /etc/init.d 

chmod 755 /etc/init.d/redis-server 

## update the redis_6379.conf file path and installation path ##

chkconfig add redis-server 

chkconfig --level 345 redis-server on

## To start Redis##

service redis-server start


Before starting redis instance, make sure the below kernel setup is in place:

Set the Linux kernel overcommit memory setting to 1 by adding “vm.overcommit_memory=1″ to “/etc/sysctl.conf”. 

Reboot the server or run the command, “sysctl vm.overcommit_memory=1″ for the change to take effect.

