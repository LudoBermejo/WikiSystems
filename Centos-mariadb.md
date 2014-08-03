First we create the mariadb repository. 

    nano /etc/yum.repos.d/mariadb.repo

    # MariaDB 10.1 CentOS repository list - created 2014-07-21 12:14 UTC
    # http://mariadb.org/mariadb/repositories/
    [mariadb]
    name = MariaDB
    baseurl = http://yum.mariadb.org/10.1/centos6-amd64
    gpgkey=https://yum.mariadb.org/RPM-GPG-KEY-MariaDB
    gpgcheck=1

Next we install mariadb

    yum install MariaDB-server MariaDB-client

Next we change the root database password:

    mysql_secure_installation

And finally we start mysql

    mysql start

And enable it in the next reboot

    chkconfig mysql on

If you want to use php with mariadb, install this:

    yum install php-pdo php-mysqli