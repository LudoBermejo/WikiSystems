# Install Cucumber on Centos #

*We need NodeJS to install cucumber. Please check [this article](nodejs) to install it on Centos.*

Cucumber lets software development teams describe how software should behave in plain text. The text is written in a business-readable domain-specific language and serves as documentation, automated tests and development-aid - all rolled into one format. You can check more info in:

[https://github.com/cucumber/cucumber-js](https://github.com/cucumber/cucumber-js)

Cucumber.js is tested on:

* Node.js 0.6, 0.8 and 0.10.0 (see CI builds)
* Google Chrome
* Firefox
* Safari
* Opera

## Installing cucumber ##


```bash

npm install -g cucumber
```


OR

You may also define cucumber.js as a development dependency of your application by including it in a package.json file.



```
#!javascript

// package.json

{ "devDependencies" : {
    "cucumber": "latest"
  }
}

# Important links #

[Best tutorial of cucumber-js I have found] (http://custardbelly.com/blog/blog-posts/2014/01/08/bdd-in-js-cucumberjs/)

[Webdriver.js Library for link with selenium webdriver](http://webdriver.io/)

For use Selenium Webdriver it's neccesary install Webdriver.js Library. 

**1. sudo npm install webdriverjs**
**2. install last selenium server version . The last when make this tutorial is 2.42.2**

  [selenium server version 2.42.2](http://selenium-release.storage.googleapis.com/2.42/selenium-server-standalone-2.42.2.jar)

**3. Install phantomjs** 
sudo npm -g install phantomjs

**4. Run selenium server first:**

cloudera@localhost.localdomain:/home/cloudera/ls -lrt selenium-server-standalone-2.42.2.jar 
-rw-rw-r-- 1 cloudera cloudera 34823352 Jun 25 01:54 selenium-server-standalone-2.42.2.jar
cloudera@localhost.localdomain:/home/cloudera/java -jar selenium-server-standalone-2.42.2.jar 
Jun 25, 2014 3:38:16 AM org.openqa.grid.selenium.GridLauncher main
INFO: Launching a standalone server
03:38:16.746 INFO - Java: Sun Microsystems Inc. 20.6-b01
03:38:16.746 INFO - OS: Linux 2.6.32-431.17.1.el6.x86_64 amd64
03:38:16.777 INFO - v2.42.2, with Core v2.42.2. Built from revision 6a6995d
03:38:16.908 INFO - Default driver org.openqa.selenium.ie.InternetExplorerDriver registration is skipped: registration capabilities Capabilities [{platform=WINDOWS, ensureCleanSession=true, browserName=internet explorer, version=}] does not match with current platform: LINUX
03:38:16.946 INFO - RemoteWebDriver instances should connect to: http://127.0.0.1:4444/wd/hub
03:38:16.947 INFO - Version Jetty/5.1.x
03:38:16.948 INFO - Started HttpContext[/selenium-server/driver,/selenium-server/driver]
03:38:16.949 INFO - Started HttpContext[/selenium-server,/selenium-server]
03:38:16.949 INFO - Started HttpContext[/,/]
03:38:16.978 INFO - Started org.openqa.jetty.jetty.servlet.ServletHandler@d8d9850
03:38:16.979 INFO - Started HttpContext[/wd,/wd]
03:38:16.981 INFO - Started SocketListener on 0.0.0.0:4444
03:38:16.982 INFO - Started org.openqa.jetty.jetty.Server@1827391d




**5. Execute example test in another console.** 

cloudera@localhost.localdomain:/home/cloudera/cucumber.js -pretty ./node_modules/webdriverjs/examples/cucumber/features/my-feature.feature 
.........

3 scenarios (3 passed)
9 steps (9 passed)
cloudera@localhost.localdomain:/home/cloudera/
