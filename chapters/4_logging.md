# error_log & access_log

While building nginx we have specified the `access_log` & `error_log` path

`--error-log-path=/var/log/nginx/error.log` \
`--http-log-path=/var/log/access.log`


#### custom logging enabled
````
location /login {
    access_log /var/log/nginx/login_page.logs;
    return 200, 'Login Page';
}
````
Here we would have seperate logs stored for path /login


#### disable logging
````
location /login {
    access_log off;
    return 200, 'Login Page';
}
````



Read More about logging
https://docs.nginx.com/nginx/admin-guide/monitoring/logging/
