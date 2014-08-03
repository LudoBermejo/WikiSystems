# Install last version of R on Centos #

First, you must update your system:


```bash

sudo su
yum update -y
```

Next, you must remove R:

```bash

yum remove R
yum remove R-*

```

Finally, you can install the new version:


```bash

yum install R

```

You may want to install Rstudio:


```bash

wget http://download2.rstudio.org/rstudio-server-0.98.953-x86_64.rpm
sudo yum install --nogpgcheck rstudio-server-0.98.953-x86_64.rpm
```
