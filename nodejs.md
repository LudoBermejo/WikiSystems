# Install NodeJS on Centos #

First of all, we need to update our system:

```bash

sudo yum -y update

```

Next, we need to download NodeJS source, compile and install it.

First it's first, we need to install the development tools:

```bash

sudo yum -y groupinstall "Development Tools"  

```

Now we create a nodejs user and change her password


```bash

sudo adduser nodejs --home /home/nodejs --shell /bin/bash
sudo passwd nodejs

```

Now we enter as this user


```bash

su nodejs
```

Create the ~/.npmrc file:


```bash

vim ~/.npmrc
```

Set the contents of the ~/.npmrc file to the following:


```bash

root = /home/nodejs/.local/lib/node_modules
binroot = /home/nodejs/.local/bin
manroot = /home/nodejs/.local/share/man
```

Create the ~/.local directory:


```bash

mkdir ~/.local
```

Next we download the sources

```bash

wget http://nodejs.org/dist/node-latest.tar.gz  

```

Now we uncompress the sources:

```bash

tar zxf node-*.tar.gz  
cd node-v*  

```

We prepare the compiler and compile node:

```bash

./configure --prefix=~/.local
make  
```

And finally we install it

```bash

make install  
```

Finally we must add the path to node to .bashrc


```bash

vi ~/.bashrc
```

And add this line of code


```bash

export PATH=$HOME/.local/bin:$PATH

```

Finally, we must create a symbolic link to npm


```bash

ln -s ~/.local/lib/node_modules ~/.node_modules

```


