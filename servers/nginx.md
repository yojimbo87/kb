## Nginx

 - [Installation](#installation)
 - [Basic authentication](#basic-authentication)
 - [SSL configuration](#ssl-configuration)
 - [Default website fallback](#default-website-fallback)
 - [Resources](#resources)
 
### Installation

Dependencies:

```
apt-get install libpcre3-dev zlib1g-dev libssl-dev
```

Download:

```
mkdir /var/src/nginx/
cd /var/src/nginx/
wget ...tar.gz
tar -xvf ...tar.gz
cd nginx-<version>
```

Build:

```
./configure --conf-path=/etc/nginx/nginx.conf --sbin-path=/usr/local/sbin --error-log-path=/var/log/nginx/error.log --http-log-path=/var/log/nginx/access.log --pid-path=/var/run/nginx.pid --lock-path=/var/lock/nginx.lock --with-http_ssl_module
make
make install
```

Setup and run:

```
# copy content from http://wiki.nginx.org/Nginx-init-ubuntu to "/etc/init.d/nginx" file 

nano /etc/init.d/nginx

# change variables within file, e.g.:
# NGINXPATH=/usr/local/nginx
# DAEMON=/usr/local/sbin/nginx
# PIDSPATH=/var/run
# lockfile=/var/lock/nginx.lock
# NGINX_CONF_FILE=/etc/nginx/nginx.conf

cd /etc/init.d/
chmod 755 nginx
/usr/sbin/update-rc.d -f nginx defaults 
 
/etc/init.d/nginx start
```

### Basic authentication

```
nano /etc/nginx/.htpasswd
printf "user_name:$(openssl passwd -crypt user_password)\n" >> .htpasswd
```

```
location  / {
        auth_basic            "Restricted";
        auth_basic_user_file  /etc/nginx/.htpasswd;
}
```

### SSL configuration

Certificate and key needs to be copied to /etc/ssl/ locations:

```
cp /home/<user>/server.crt /etc/ssl/certs/
cp /home/<user>/server.key /etc/ssl/private/
```

nginx.conf

```
# rewrites all http requests to https
server {
        listen 80;
        server_name foo.bar.baz;
 
        rewrite ^(.*) https://$host$1 permanent;
}
    
server {
        listen       443;                                                      # on win its 8080
        server_name  foo.bar.baz;                                              # on win its localhost
        
        ssl         on;
        ssl_certificate      /etc/ssl/certs/server.crt;                        # on win its cert/server.crt
        ssl_certificate_key  /etc/ssl/private/server.key;                      # on win its cert/server.key
 
        ssl_session_timeout  5m;
 
        ssl_protocols  SSLv2 SSLv3 TLSv1;
        ssl_ciphers  HIGH:!aNULL:!MD5;
        ssl_prefer_server_ciphers   on;
 
        location / {
            root   /var/www/;                                                  # on win its var/www/
            index  index.html;
        }
 
        ...
}
```

### Default website fallback

nginx.conf

```
server {
        listen 80;
        server_name default_server;

        location / {
                root /var/www/default/;
                index index.html;
        }
}
```

### Resources

 - [Install options](http://wiki.nginx.org/InstallOptions)
 - [Ubuntu init](http://wiki.nginx.org/Nginx-init-ubuntu)
 - [HTTP Basic Auth module](http://wiki.nginx.org/HttpAuthBasicModule)
 - [SSL configuration](http://nginx.org/en/docs/http/configuring_https_servers.html)
 - [SSL config example](https://github.com/properssl/nginx-pfs/blob/master/Vagrant-setup/share/ssl-pfs-site.conf)
 - [Using nginx to avoid node.js load](http://blog.argteam.com/coding/hardening-node-js-for-production-part-2-using-nginx-to-avoid-node-js-load/)
 - [Zero downtime deployments with nginx](http://blog.argteam.com/coding/hardening-node-js-for-production-part-3-zero-downtime-deployments-with-nginx/)

