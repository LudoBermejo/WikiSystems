# Jenkins in nodejs #

*You need to have NodeJS in order to use this tutorial. Please [check this link](https://bitbucket.org/iadlearning-team/iadlearning-wiki/wiki/nodejs)*

Now, the difficult one is to execute Jenkins with nodejs user, and not with with the ssh user that you connect. It's an awful solution, but ey, it works :)

Take a simple nodejs server. This is a customize commands in nodejs that execute node with nodejs user in the same path that jenkins. We need to create the files that we are going to use before change the owner to nodejs

```bash
mkdir -p build/testResults/
touch build/testResults/TEST-App.xml
sudo chown -R nodejs *
export customPATH=`pwd`
sudo su - nodejs <<eos
cd "$customPATH"
npm install
NODE_ENV=testing node lib/app.js &
npm test
pkill node
```

And now the same, but for Karma

```bash
touch test-results.xml
mkdir -p node_modules
sudo chown -R nodejs *
export customPATH=`pwd`
sudo su - nodejs <<eos
cd "$customPATH"
node --version
echo "Hago el install de los modulos"
npm install
echo "Hago el test"
npm test
```