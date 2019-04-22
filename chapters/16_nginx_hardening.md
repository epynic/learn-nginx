# nginx hardening


#### remove nginx version from header response
````server_tokens off;````

#### prevent iframe embed & XSS  
````
add_header X-Frame-Options "SameORIGIN";
add_header X-XSS-Protection "1; node=block";
````

#### removing default modules
In our case if we need to remove directory listing

append to config --without autoindex


#### SSL by LetsEncrypt
https://www.digitalocean.com/community/tutorials/how-to-secure-nginx-with-let-s-encrypt-on-ubuntu-18-04
