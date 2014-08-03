Simple. Just install a few packagers:


```
#!bash

npm install connect  serve-static
```

And create the simplest javascript (like server.js)

```
#!javascript

var connect = require('connect');
var serveStatic = require('serve-static');
connect().use(serveStatic(__dirname)).listen(80);

```

Then, execute node


```
#!bash

node server.js
```
