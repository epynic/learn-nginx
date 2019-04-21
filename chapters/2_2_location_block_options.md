# nginx location block config options

#### Prefix match 
This will match URL 
* PUBLIC IP/test
* PUBLIC IP/test_anything

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

    }
}
````
_Update the PUBLIC IP & root path accordingly._


#### Exact match
This is a strict match to URL 
* PUBLIC IP/test

````
location = /test {
    return 200 'Hello from Test URL path';
}
````

#### Regex case sensitive match
This is a strict match to URL 
* PUBLIC IP/test1
* PUBLIC IP/test2 upto 9

````
location ~ /test[0-9] {
    return 200 'Hello from Test URL path';
}
````


#### Regex - case insensitive match 
This is a strict match to URL 
* PUBLIC IP/test1
* PUBLIC IP/TEST1

````
location ~* /text[0-9] {
    return 200 'Hello from Test URL path';
}
````

#### Preferential prefix match - priority
by default nginx prefers location blocks with regex

This is a strict match to URL 
* PUBLIC IP/Test2

````
location ^~ /Text2 {
    return 200 'Hello from Test URL Test2  path';
}
````
