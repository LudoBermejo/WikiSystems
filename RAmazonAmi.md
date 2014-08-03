# Install last version of R on AWS Amazon AMI #

Ok, this is a little tricky. Amazon AMI doesn't have a repository with the last R, so we must download it and compile from the source.

First is first, we need to install the packages we need:


```
#!bash

sudo yum -y install make libX11-devel.* libICE-devel.* libSM-devel.* libdmx-devel.* libx* xorg-x11* libFS* libX*  readline-devel gcc-gfortran gcc-c++ texinfo tetex

```
Next we download the last version of R and uncompress it([just check in webpage](http://cran.at.r-project.org/src/base/R-3/))


```
#!bash

wget http://cran.at.r-project.org/src/base/R-3/R-3.1.0.tar.gz
tar xf R-3.1.0.tar.gz
cd R-3.1.0
```

Ok, now this is important. We must configure R in order to support some algorithms, so *we must* to include some directives. Just like this:


```
#!bash

./configure --enable-R-shlib 
```

Finally we can make & install the complete R. Just write a book, rise a child or wait to a change in government. Yeah, it takes so long.


```
#!bash

make
sudo make install
```




