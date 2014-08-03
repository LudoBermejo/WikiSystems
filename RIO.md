# Install RIO to work with R on Nodejs #

First, create a project with rio package


```
#!bash

npm install rio
```

Next, execute R and activate Rserve (for more information of Rserve, please check [this link](http://rforge.net/Rserve/). Note: Rserve must be installed


```
#!bash

R
install.packages("Rserve",dependencies=TRUE)
require('Rserve')
Rserve()
q()
```

Ok, now we have the Rserve listening. Now we can simply create a file to test the connection


```
#!nodejs

var rio = require('rio');

rio.evaluate("pi / 2 * 2");
rio.evaluate('c(1, 2)');
rio.evaluate("as.character('Hello World')");
rio.evaluate('c("a", "b")');
rio.evaluate('Sys.sleep(5); 11')

```