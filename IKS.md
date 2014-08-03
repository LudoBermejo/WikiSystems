## Install Interactive Knowledge Stack

*Important: you need Java 6 to install this. Please check this article before try this commands: [Install Java on Centos](Java)*

IKS install is easy deasy. Just download the file (you can check lasts versions on [the project's page](https://code.google.com/p/iks-project/))

```
#!bash
wget http://dev.iks-project.eu/downloads/iks-stack-releases/IKS-RI-7.0.zip
```

Unzip the file

```
#!bash
unzip IKS-RI-7.0.zip
```

And finally execute the .jar

```
#!bash
cd IKS-RI-7.0/
java -Xmx1024m -jar iks-7.0-launcher.jar
```

Now you can see this page (in [localhost:8080](http://localhost:8080))

![IKS.png.png](https://bitbucket.org/repo/oAAnGq/images/1549843210-IKS.png.png)



