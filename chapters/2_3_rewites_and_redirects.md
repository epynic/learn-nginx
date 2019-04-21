# Redirect vs Rewrites

### Redirects 
Changes URL in browser address bar and redirects to new URL.

* PUBLIC IP/logo --> redirects to PUBLIC IP/thumb.png 
````
location /logo {
    return 301 /thumb.png
}
````

### Rewrites
Doesn’t change URL in browser address bar

````
events{}
http{
    server{
        listen 80;
        server_name PUBLIC IP;
        root /home/epynic/site;

        location /test {
            return 200 'Hello from Test URL path';
        }

        rewrite ^/ab_test/\w+ /test 
    }
}

````
* PUBLIC IP/ab_test/123 --> rewrites to PUBLIC IP/test internally

#### rewrite parameters

`rewrite ^/ab_test(\w+) /test/$1;`

* PUBLIC IP/ab_test/123 --> rewrites to PUBLIC IP/test internally
* PUBLIC IP/ab_test/demo --> rewrites to PUBLIC IP/demo 

````
location /test {
    return 200 'Hello from Test URL path';
}

location /test/demo {
    return 200 'Hello from Test Demo URL path';
}
````