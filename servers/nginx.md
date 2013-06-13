## Nginx

 - [Installation](#installation)
 - [Basic authentication](#basic-authentication)
 - [SSL configuration](#ssl-configuration)
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
nano /etc/init.d/nginx # content from http://wiki.nginx.org/Nginx-init-ubuntu - change some params within file
cd /etc/init.d/
/usr/sbin/update-rc.d -f nginx defaults 
chmod 755 nginx
 
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

### Resources

 - [Install options](http://wiki.nginx.org/InstallOptions)
 - [Ubuntu init](http://wiki.nginx.org/Nginx-init-ubuntu)
 - [HTTP Basic Auth module](http://wiki.nginx.org/HttpAuthBasicModule)
 - [SSL configuration](http://nginx.org/en/docs/http/configuring_https_servers.html)

