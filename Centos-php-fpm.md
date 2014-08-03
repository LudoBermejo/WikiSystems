# Install nginx on centos with php-fpm

## NGINX 

First the server!

```bash
nano /etc/yum.repos.d/nginx.repo

```

```bash

[nginx]
name=nginx repo
baseurl=http://nginx.org/packages/centos/$releasever/$basearch/
gpgcheck=0
enabled=1

```

```bash

yum install nginx

```

```bash
Next change the destiny (I prefer to use /var/www)

mkdir /var/www
mkdir /var/www/vhosts
mkdir /var/www/vhosts/default
cp -rf /usr/share/nginx/html/*  /var/www/vhosts/default
chown -R nginx:nginx /var/www

```

Now we create the ubuntu-esque directories structure

```bash
mkdir /etc/nginx/sites-enabled
mkdir /etc/nginx/sites-available
cp /etc/nginx/conf.d/* sites-available/
cd /etc/nginx/sites-enabled
ln -s /etc/nginx/sites-available/default.conf
```

And then edit nginx.conf to enable sites-enabled (and disable /etc/nginx/conf.d)

```bash
nano /etc/nginx.conf

#include /etc/nginx/conf.d/*.conf;
include /etc/nginx/sites-enabled/*;

```

And we edit the sites-enabled/ conf to the new path

```bash
nano /etc/nginx/sites-enabled/default.conf


location / {
root   /var/www/vhosts/default;
index  index.html index.htm;
}

location = /50x.html {
root   /var/www/vhosts/default;
}
```

Finally we check the nginx configuration and execute nginx

```bash
nginx -t
service nginx stgart

```

## PHP-FPM

Now the php-fpm

```bash
 yum install php-fpm

```

We need to change the user that executes php-fpm. 

```bash
nano /etc/php-fpm.d/www.conf

```

Replace "apache" for "nginx"



We must create the session directory for saving sessions:

```bash
mkdir /var/lib/php/sessions
chown -R nginx:nginx /var/lib/php/sessions

```



Then start the service

```bash
 service start php-fpm

```

And edit the default.conf to enable php

```bash
 nano /etc/nginx/sites-enabled/default.conf

 # pass the PHP scripts to FastCGI server listening on 127.0.0.1:9000
 #
 location ~ \.php$ {
 	root   /usr/share/nginx/html;
 	fastcgi_pass   127.0.0.1:9000;
 	fastcgi_index  index.php;
 	fastcgi_param  SCRIPT_FILENAME   $document_root$fastcgi_script_name;
 	includefastcgi_params;
 }
```

Finally we restart nginx:

```bash
 service nginx restart

```

To test it, just create a phpinfo script

```bash
 nano /var/www/vhosts/default/i.php

 <?php phpinfo(); ?>
```

And execute it

# Install APC

Install the cache:

```bash
yum install php-pecl-apc

```

Restart php-fpm

```bash
service php-fpm restart
```