# header expires default

That would add the cache config for css,js,jpg & png files.
````
location ~* \.(css|js|jpg|png)$ {
    add_header Cache-Control public;
    add_header Pragma public;
    add_header Vary Accept-Encoding;
    expires 1M;
}
````