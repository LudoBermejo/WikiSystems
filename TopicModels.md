#Install topicmodels in R on Centos#

First install the gsl libraries:

```bash

yum install gsl
```

Next you need the gsl-dev libraries. To do so, download them from [here](http://www.rpmfind.net/linux/rpm2html/search.php?query=gsl-devel). Just choose the right package (Centos in this case). Download with wget, and install it with rpm -i:


```bash

wget ftp://195.220.108.108/linux/centos/6.5/os/x86_64/Packages/gsl-devel-1.13-1.el6.x86_64.rpm

rpm -i gsl-devel-1.13-1.el6.x86_64.rpm 
```

Now you can install topicmodels from Rstudio.

## Topic models in AWS ##

In case of Amazon server, the yum install gsl version is not compatible with gsl-devel version. So, the first step is the manual download of gsl rpm:


```bash

wget ftp://rpmfind.net/linux/centos/6.5/os/x86_64/Packages/gsl-1.13-1.el6.x86_64.rpm

rpm -i gsl-1.13-1.el6.x86_64.rpm
```



