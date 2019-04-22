# Add default gzip config

Add the below config to enable gzip
````
gzip on;
gzip_comp_level 3;

gzip_types text/javascript;
gzip_types text/css;
````

To test this out `curl -I -H "Accept-Encoding: gzip,deflate" IP/.css` will return Content-Encoding: gzip

