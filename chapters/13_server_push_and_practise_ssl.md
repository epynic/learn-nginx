# HTTP2 Server push

We can use nghttp2 to test HTTP2 server push

```` apt-get install nghttp2-client ````

````
location = /index.html {
    http2_push /style.css;
    http2_push /thumb.png;
}
````

nghttp -nysa URL - will show the request/response time

## SSL best practises

REdirect 80 to 443
````
server {
    listen 80;
    server_name IP;
    return 301 https://$host$requst_uri;
}
````

````
#disable ssl and use TLS
ssl_protocols TLSv1 TLSv1.1 TLSv1.2;

ssl_prefer_server_ciphers on;
ssl_ciphers ECDHE-RSA-AES256-GCM-SHA512:DHE-RSA-AES256-GCM-SHA512:ECDHE-RSA-AES256-GCM-SHA384:DHE-RSA-AES256-GCM-SHA384:ECDHE-RSA-AES256-SHA384;

# Enable DH params - Better key exchanges
ssl_dhparam /etc/nginx/ssl/dhparam.pem;
#to generate pem  openssl dgparam 2048 -out /etc/nginx/ssl/dhparams.pem


#ssl sessions cache #
ssl_session_cache shared:SSL:40m;
ssl_session_timeout 4h;
ssl_session_tickets on;