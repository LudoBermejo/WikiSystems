# Install zeromq on Amazon Centos #

*You need to have NodeJS in order to use this tutorial. Please [check this link](https://bitbucket.org/iadlearning-team/iadlearning-wiki/wiki/nodejs)*

First of all, we need to create a new repos. By default, the amazon repository has an old version of zeromq.

So first we create the repo:

```
#!bash

sudo nano /etc/yum/zeromq.repo

```

With this data:

```
#!bash

[home_fengshuo_zeromq]
name=The latest stable of zeromq builds (CentOS_CentOS-6)
type=rpm-md
baseurl=http://download.opensuse.org/repositories/home:/fengshuo:/zeromq/CentOS_CentOS-6/
gpgcheck=1
gpgkey=http://download.opensuse.org/repositories/home:/fengshuo:/zeromq/CentOS_CentOS-6/repodata/repomd.xml.key
enabled=1

```

Next we need to install zeromq and zeromq-dev


```
#!bash

yum install zeromq
yum install zeromq-devel

```

So... now we need to prove all it's working. We have a new repository to test zeroqm. Let's install it.

First download de repo:



```
#!bash

cd ~
git clone https://bitbucket.org/LudoItop/zeromq-example.git
cd zeromq-example/zeromq-client
npm install
cd ../zeromq-server
npm install

```

So, finally we need to open the server & the client:


```
#!bash

# server
node ~/zeromq-example/zeromq-server/server.js

# client
node ~/zeromq-example/zeromq-client/client.js

```

If you see messages in the log, then it's working :)



