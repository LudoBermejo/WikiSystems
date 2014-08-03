# Install nginx as a reverse proxy of nodejs #

First we need to create the nginx repo:


```bash

vi /etc/yum.repos.d/nginx.repo
```

With this lines


```bash

[nginx]
name=nginx repo
baseurl=http://nginx.org/packages/centos/$releasever/$basearch/
gpgcheck=0
enabled=1
```

Next, we install nginx

```bash

yum install nginx
```

Now the best we can do is change the nginx path. So:

```bash

mkdir /var/www
mkdir /var/www/nginx
mkdir /var/www/nodejs

sudo chown -R nginx /var/www/nginx
sudo chown -R nodejs /var/www/nodejs
```

This is an example for use nginx as a reverse proxy for nodejs. *It's not finished yet, but it works!*

## /etc/nginx/nginx.conf ##
```bash

# For more information on configuration, see:
#   * Official English Documentation: http://nginx.org/en/docs/
#   * Official Russian Documentation: http://nginx.org/ru/docs/

user  nginx;
worker_processes  1;

error_log  /var/log/nginx/error.log;
#error_log  /var/log/nginx/error.log  notice;
#error_log  /var/log/nginx/error.log  info;

pid        /var/run/nginx.pid;


events {
    worker_connections  1024;
}


http {
    include       /etc/nginx/mime.types;
    default_type  application/octet-stream;

    log_format  main  '$remote_addr - $remote_user [$time_local] "$request" '
                      '$status $body_bytes_sent "$http_referer" '
                      '"$http_user_agent" "$http_x_forwarded_for"';

    access_log  /var/log/nginx/access.log  main;

    sendfile        on;
    #tcp_nopush     on;

    #keepalive_timeout  0;
    keepalive_timeout  65;

    #gzip  on;

    gzip on;
    gzip_disable "MSIE [1-6]\.";
    gzip_vary on;
    gzip_proxied any;
    gzip_comp_level 6;
    gzip_buffers 16 8k;
    gzip_http_version 1.1;
    gzip_min_length 512;
     gzip_types
    # text/html is always compressed by HttpGzipModule
    text/plain
    text/css
    text/xml
    text/javascript
    text/x-component
    application/json
    application/javascript
    application/x-javascript
    application/xml
    application/xml+rss
    application/vnd.ms-fontobject
    font/truetype
    font/opentype
    image/svg+xml;

    # Load modular configuration files from the /etc/nginx/conf.d directory.
    # See http://nginx.org/en/docs/ngx_core_module.html#include
    # for more information.

    include /etc/nginx/conf.d/*.conf;
    include /etc/nginx/sites-enabled/*;
}

```

Ok, next is the host configuration. Check this example:

/etc/nginx/conf.d/vhost.conf (*example*)


```bash

    server {
        listen       80;
        server_name  localhost;
        root         /var/www/nginx;

        #charset koi8-r;

        #access_log  /var/log/nginx/host.access.log  main;

        location / {
        }


          location /api {
              # root /srv/www/your_app;
              # index index.html;
              proxy_set_header X-Real-IP $remote_addr;
              proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
              proxy_set_header Host $http_host;
              proxy_set_header X-NginX-Proxy true;
              proxy_pass http://127.0.0.1:8080/api;
              proxy_redirect off;
          }


        # redirect server error pages to the static page /40x.html
        #
        error_page  404              /404.html;
        location = /40x.html {
        }

        # redirect server error pages to the static page /50x.html
        #
        error_page   500 502 503 504  /50x.html;
        location = /50x.html {
        }

        # proxy the PHP scripts to Apache listening on 127.0.0.1:80
        #
        #location ~ \.php$ {
        #    proxy_pass   http://127.0.0.1;
        #}

        # pass the PHP scripts to FastCGI server listening on 127.0.0.1:9000
        #
        #location ~ \.php$ {
        #    root           html;
        #    fastcgi_pass   127.0.0.1:9000;
        #    fastcgi_index  index.php;
        #    fastcgi_param  SCRIPT_FILENAME  /scripts$fastcgi_script_name;
        #    include        fastcgi_params;
        #}

        # deny access to .htaccess files, if Apache's document root
        # concurs with nginx's one
        #
        #location ~ /\.ht {
        #    deny  all;
        #}
    }

```


