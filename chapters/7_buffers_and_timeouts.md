# buffers & timeouts

#### For POST submission

````
client_body_buffer_size 10K;
client_max_body_size 8m;
````
when the size is above 8MB it would throw a 413 request entity too large error.


#### Other settings

````
client_header_buffer_size 1k;
client_body_timeout 12;
client_header_timeout 12;
keepalive_timeout 125;

#skip buffering for static content
sendfile on; 
#sendfile packet optimise
tcp_nopush on; 

#max time for client to accept/ receive a response.
send_timeout 10;
````