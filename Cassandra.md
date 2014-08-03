# Install Cassandra on Centos #

You *must* have java7 in order to use Cassandra. You can check [how to install java](java7).

Next, edit the repositories

```bash

sudo vi /etc/yum.repos.d/datastax.repo
```

And add one


```
#!vi

[datastax]
name= DataStax Repo for Apache Cassandra
baseurl=http://rpm.datastax.com/community
enabled=1
gpgcheck=0
```

And install Cassandra


```bash

sudo yum install dsc20  
```

It's no over yet! We must modify /etc/hosts to add our host. To do so, we need to know our IP. Best way to do it? Just execute 

```bash

cassandra
```

And you see an error with a host. Just edit /ect/vhosts


```
#!python

sudo nano /etc/vhosts
```

And add the host, just like this:


```
#!vi

127.0.0.1   localhost localhost.localdomain localhost ip-172-30-0-212
```




