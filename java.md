## Install Java 6

First thing we must to do is install Java. But **privative java version 6**, not the **openjdk**, not other version of privative java.

```bash

wget http://uni-smr.ac.ru/archive/dev/java/SDKs/sun/j2se/6/jdk-6u45-linux-x64-rpm.bin
cp jdk-6u45-linux-x64-rpm.bin /opt

```

Next, we must execute the bin file to install it on opt directory

```bash

chmod +x /opt/jdk-6u45-linux-x64-rpm.bin /opt/./jdk-6u45-linux-x64-rpm.bin
```

Next, we configure the system to accept JAVA

```bash
alternatives --install /usr/bin/java java /usr/java/jdk1.6.0_45/jre/bin/java 20000
alternatives --install /usr/bin/jar jar /usr/java/jdk1.6.0_45/bin/jar 20000
alternatives --install /usr/bin/javac javac /usr/java/jdk1.6.0_45/bin/javac 20000
alternatives --install /usr/bin/javaws javaws /usr/java/jdk1.6.0_45/jre/bin/javaws 20000
alternatives --set java /usr/java/jdk1.6.0_45/jre/bin/java
alternatives --set javaws /usr/java/jdk1.6.0_45/jre/bin/javaws
alternatives --set javac /usr/java/jdk1.6.0_45/bin/javac
alternatives --set jar /usr/java/jdk1.6.0_45/bin/jar
```

And finally we check that it's working:

```bash
java -version
```

Ohhhh.... java is OpenJDK. Let's try to change it:

```bash
sudo rm /usr/bin/java
/usr/sbin/alternatives --config java
```

Now select the good one. And pray!
