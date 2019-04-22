# HTTP2

1. Binary Protocol
2. Compressed headers
3. Persistent connections
4. multiplex streaming


#### HTTP2 needs SSL enabled

To selfsign certificates

To create ssl certs run,

````
openssl req -x509 -days 10 -nodes -newkey rsa:2058 -keyout /etc/nginx/ssl/self.key -out /etc/nginx/ssl/self.crt
````

nginx config

````
listed 443 ssl;
ssl_certificate /filelocation/self.crt;
ssl_certificate_key /filelocation/self.key
````

#### Build nginx source with HTTP2 config

````--with_-http_v2_module````

Dont forget to compile and install


#### Enable HTTP2 
````
listed 443 ssl http2;
````