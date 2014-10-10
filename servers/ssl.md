## SSL

 - [Bundle certificate](#bundle-certificate)
 - [Generate self signed certificate](#generate-self-signed-certificate)
 - [Resources](#resources)
 
### Bundle certificate

Some browsers may complain about a certificate signed by a well-known certificate authority, while other browsers may accept the certificate without issues. This occurs because the issuing authority has signed the server certificate using an intermediate certificate that is not present in the certificate base of well-known trusted certificate authorities which is distributed with a particular browser. In this case the authority provides a bundle of chained certificates which should be concatenated to the signed server certificate. The server certificate must appear before the chained certificates in the combined file (in case of nginx).

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
