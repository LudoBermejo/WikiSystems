## At the beginning was Centos

First, download Centos [http://www.centos.org/download/]

Then, install it on a Virtual machine of VirtualBox [http://www.virtualbox.com]

_Note: if you have a Lenovo computer, you might have to enable Virtual Intel technology in Bios_

Now, you need internet. But in the Virtual machine, internet is not working! Why? Because it doesn't boot by default. I don't know why. To fix this problem, just:


```bash

sudo nano /etc/sysconfig/network-scripts/ifcfg-eth0
```

And find the line:

```bash

ONBOOT=no
```

And change it for yes:

```bash

ONBOOT=yes
```

Finally execute this command

```bash

/etc/init.d/network restart 2
```

Ah! We need to add our centos user to sudoers in order to use the "sudo" command. 

First thing to do is to enter as root:

#!bash

su
```

Next, we edit the sudoers file:

#!bash

vim /etc/sudoers
```

Find this lines


```bash

## Allow root to run any commands anywhere
root     ALL=(ALL)     ALL
```

And add this line (replace USERNAME with your user)


```bash

[USERNAME]     ALL=(ALL)     ALL
```



and voalà! 
