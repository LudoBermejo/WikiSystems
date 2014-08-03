# NGINX #

First the server!

`nano /etc/yum.repos.d/nginx.repo`

    [nginx]
    name=nginx repo
    baseurl=http://nginx.org/packages/centos/$releasever/$basearch/
    gpgcheck=0
    enabled=1

`yum install nginx`

Next change the destiny (I prefer to use /var/www)

    mkdir /var/www
    mkdir /var/www/vhosts
    mkdir /var/www/vhosts/default
    cp -rf /usr/share/nginx/html/*  /var/www/vhosts/default
    chown -R nginx:nginx /var/www

Now we create the ubuntu-esque directories structure

    mkdir /etc/nginx/sites-enabled
    mkdir /etc/nginx/sites-available
    cp /etc/nginx/conf.d/* sites-available/
    cd /etc/nginx/sites-enabled
    ln -s /etc/nginx/sites-available/default.conf

And then edit nginx.conf to enable sites-enabled (and disable /etc/nginx/conf.d)

    nano /etc/nginx.conf

    #include /etc/nginx/conf.d/*.conf;
    include /etc/nginx/sites-enabled/*;

And we edit the sites-enabled/ conf to the new path

    nano /etc/nginx/sites-enabled/default.conf


    location / {
        root   /var/www/vhosts/default;
        index  index.html index.htm;
    }

    location = /50x.html {
        root   /var/www/vhosts/default;
    }


Finally we check the nginx configuration and execute nginx

    nginx -t
    service nginx stgart

# PHP-FPM #

Now the php-fpm

     yum install php-fpm

We need to change the user that executes php-fpm. 

    nano /etc/php-fpm.d/www.conf

Replace "apache" for "nginx"



We must create the session directory for saving sessions:

    mkdir /var/lib/php/sessions
    chown -R nginx:nginx /var/lib/php/sessions



Then start the service

     service start php-fpm

And edit the default.conf to enable php

     nano /etc/nginx/sites-enabled/default.conf

     # pass the PHP scripts to FastCGI server listening on 127.0.0.1:9000
     #
     location ~ \.php$ {
     	root           /usr/share/nginx/html;
     	fastcgi_pass   127.0.0.1:9000;
     	fastcgi_index  index.php;
     	fastcgi_param  SCRIPT_FILENAME   $document_root$fastcgi_script_name;
     	include        fastcgi_params;
     }

Finally we restart nginx:

     service nginx restart

To test it, just create a phpinfo script

     nano /var/www/vhosts/default/i.php

     <?php phpinfo(); ?>

And execute it

# Install APC #

Install the cache:

    yum install php-pecl-apc

Restart php-fpm

    service php-fpm restart
