# Installing Neo4j on CentOS #

First of all, we must make sure to have the **Java JDK 7** installed.

Then, the next steps are:

```
#!bash

wget -O neo4j.tar.gz http://dist.neo4j.org/neo4j-community-2.1.2-unix.tar.gz
tar zxvf neo4j.tar.gz
mv neo4j-community-2.1.2/ /opt/neo4j
cd /opt/neo4j
./bin/neo4j-installer install

```
To avoid some problems with the neo4j service, we'll install lsof:


```
#!bash

yum install lsof
```

At this point you must follow the instructions of the installer ( don't worry, it's easy :) ).

To start/stop the neo4j service:


```
#!bash

/opt/neo4j/bin/neo4j start
/opt/neo4j/bin/neo4j stop
```

To check if neo4j is running, in a web browser go to 
```
#!bash

http://localhost:7474/
```

# Resolving problems initializing CentOS after installing Neo4j #

If CentOS isn't init after the Neo4j we must quit the neo4j-service init.

The first step is init CentOS in single mode. When the init starts, we have to press the **Esc** button, to enter in grub mode.

In the grub menu, we press 'e' to edit the second line (it begins like "kernel /boot/..."). At the end of the line, we write 'single' (without ' ' ) and press Enter. After we press 'b', to start CentOS.

In the single mode we have to deactivate the neo4j-service. To do this, we write:

```
#!bash

chkconfig --del neo4j-service
reboot
```

And...that's all!