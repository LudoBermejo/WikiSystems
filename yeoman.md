# Install yeoman on Centos #

*Important: before you can install yeoman, you must have nodejs. Please check this article before try this commands: [Install NodeJs on Centos](nodejs)*

You can check what yeoman is in [this page](http://yeoman.io/)

So... the first thing we must do is to install bower & yeoman client:


```
#!bash

sudo npm install -g bower
sudo npm install -g yo
```

Easy, right? Now perhaps we need to install a express-angular generator ([check this page](https://www.npmjs.org/package/generator-angular-fullstack)):

```
#!bash

npm install generator-angular-fullstack
```

When finished, we have a good-shiny-new generator. Just make a directory and execute yeoman

```
#!bash

mkdir express
cd express
yo angular-fullstack
```


