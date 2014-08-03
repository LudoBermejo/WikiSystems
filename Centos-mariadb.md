First we create the mariadb repository. 

```bash
    nano /etc/yum.repos.d/mariadb.repo

    # MariaDB 10.1 CentOS repository list - created 2014-07-21 12:14 UTC
    # http://mariadb.org/mariadb/repositories/
    [mariadb]
    name = MariaDB
    baseurl = http://yum.mariadb.org/10.1/centos6-amd64
    gpgkey=https://yum.mariadb.org/RPM-GPG-KEY-MariaDB
    gpgcheck=1

```
Next we install mariadb

```bash
    yum install MariaDB-server MariaDB-client
```

Next we change the root database password:

```bash
    mysql_secure_installation
```

And finally we start mysql

```bash
    mysql start
```

And enable it in the next reboot

```bash
chkconfig mysql on
```
If you want to use php with mariadb, install this:

```bash
    yum install php-pdo php-mysqli
```

