# Install sublime 3 on Centos #

First we download Sublime 3 package from [here](http://www.sublimetext.com/3)


```bash

wget http://c758482.r82.cf2.rackcdn.com/sublime_text_3_build_3059_x64.tar.bz2
```

Next we uncompress the file

```bash

tar xvjf sublime_text_3_build_3059_x64.tar.bz2
```

Now we copy the sublime_text directory into /opt

```bash

cp -rf sublime_text_3 /opt
```

And then create a symbolic link.

```bash

sudo ln -s /opt/sublime_text_3/sublime_text /usr/bin/sublime3
```

Now we can execute sublime3 with only one line

```bash

sublime3
```

Now we are going to create an icon in our desktop. Just open a new document with sublime3

```bash

sudo sublime3 /usr/share/applications/sublime3.desktop
```

And put this code into it:


```bash

[Desktop Entry]
Name=Sublime3
Exec=sublime3
Terminal=false
Icon=/opt/sublime_text_3/Icon/48x48/sublime-text.png
Type=Application
Categories=TextEditor;IDE;Development
X-Ayatana-Desktop-Shortcuts=NewWindow
 
[NewWindow Shortcut Group]
Name=New Window
Exec=sublime -n
TargetEnvironment=Unity
```
