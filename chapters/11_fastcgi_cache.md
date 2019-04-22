# FastCGI cache

Configure micro caching

````
fastcgi_cache_path /tmp/nginx_cache levels=1:2 key_zone=ZONE1:100m inactive=60m
fastcgi_cache_key "$scheme$request_method$host$request_uri"
add_header X-Cache $upstream_cache_status;

````

level - depth of directory to split cache entry written
key_zone - naming:size
inactive - keep cache entry active


To enable cache

````
location ~\.php${
    include fastcgi.conf;
    fastcgi_pass unix:/run/php/php7.1-fpm.sock

    #Enable cache
    fastcgi_cache ZONE1;
    fastcgi_cache_valid 200 60m;
    fastcgi_cache_valid 404 10m;
}
````

To test caching - we will use a tool called Apache Bench

Install Apache Bench : `apt-get install apache2-utils` \
To Test result ` ab -n 100 -c 10 SiteURL`

To set cache skip on arg skipcache=1

````
set $no_cache 0;
if($arg_skipcache = 1) {
    set $no_cache 1;
}

fastcgi_cache_bypass $no_cache;
fastcgi_no_cache $no_cache;
````