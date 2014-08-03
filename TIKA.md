# Install TIKA on Centos

We are going to install Tika under the Nodejs user. Please check [this tutorial](https://bitbucket.org/iadlearning-team/iadlearning-wiki/wiki/nodejs)

First, we need to download Tika from [here](http://tika.apache.org/download.html)


```bash

sudo su nodejs
cd 
mkdir .tika
cd .tika
wget http://ftp.cixug.es/apache/tika/tika-app-1.5.jar
cp tika-app-1.5.jar tika.jar
```

Next we need to make it executable. We need to create a execute script:

```bash

nano stub.sh

```

With this text:

```bash

#!/bin/sh
MYSELF=`which "$0" 2>/dev/null`
[ $? -gt 0 -a -f "$0" ] && MYSELF="./$0"
java=java
if test -n "$JAVA_HOME"; then
    java="$JAVA_HOME/bin/java"
fi
exec "$java" $java_args -jar $MYSELF "$@"
exit 1 

```

Next, we append this file to tika:

```bash

cat stub.sh tika.jar > tika && chmod +x tika
```

And we try it

```bash

mkdir tmp
cd tmp
wget http://www.sa.is/media/1039/example.pdf
cd ..
tika --text tmp/example.pdf >prueba.txt

```

Ok, first is done. Now we only have to add this path to the nodejs script loading server. Just edit .bashrc:

```bash

cd 
nano .bashrc

```

And edit the PATH (something like this):


```bash


# User specific aliases and functions
export PATH=$HOME/.local/bin:$HOME/.tika/:$PATH
exit
sudo su nodejs

```

Now you can call (only with nodejs!) tika from all over the world (AKA the computer) :)


