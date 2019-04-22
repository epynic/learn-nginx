# Rate Limiting in Nginx

To Test we can use tools like seige `apt-get install siege`

seige run command `seige -v -r 2 -c 5 URL`

### per IP limiting
`limit_req_zone $binary_remove_addr;`

### URI limiting
````
limit_req_zone $request_uri zone=ZONE:10m rate=60r/m;
# 60 request / minute limit
````

Add this to prefered location context
````
limit_req zone = ZONE burst=5 nodelay;
````

Read more at https://www.nginx.com/blog/rate-limiting-nginx/