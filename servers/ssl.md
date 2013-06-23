## SSL

 - [Generate self signed certificate](#generate-self-signed-certificate)
 - [Resources](#resources)
 
### Generate self signed certificate

Windows:

```
genrsa -des3 -out server.key 4096
req -config C:\OpenSSL-Win32\bin\openssl.cfg -new -key server.key -out server.csr
rsa -in server.key -out server.key                                                     # removes passphrase
x509 -req -days 365 -in server.csr -signkey server.key -out server.crt
```

### Resources

 - [OpenSSL binaries](http://www.openssl.org/related/binaries.html)
 - [Use OpenSSL on Windows](http://www.faqforge.com/windows/use-openssl-on-windows/)

 - [Cheapest found SSL certificate](http://www.exossl.sk/#certifikaty)
