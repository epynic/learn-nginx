# Basic Auth 

Requires `apache2-utils` need to be installed to generate password file.

#### generate password file
```` htpasswd -c /etc/nginx/.htpasswd webuser ```` \
And type the required password


#### nginx config 
````
location /admin {
    auth_basic "Secure Area";
    auth_basic_user_file /etc/nginx/.htpasswd;
}
````