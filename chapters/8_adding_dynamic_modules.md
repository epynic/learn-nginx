# Adding dynamic modules to existing nginx installation

We need to have the source code downloaded in chapter 1 and also get the existing nginx configuration used.

#### copy existing config
Run `ngnix -V` to get the current configuration that would look like 

````
configure arguments: --sbin-path=/usr/bin/nginx --conf-path=/etc/nginx/nginx.conf --error-log-path=/var/log/nginx/error.log --http-log-path=/var/log/nginx/access.log --with-pcre --pid-path=/var/run/nginx.pid --with-http_ssl_module
````
#### search module to add
To see modules available run `./configure --help` \
filter with grep `./configure --help | grep dynamic`

#### adding module
We are going to add the module `--with-http_image_filter_module`

ImageFilter modules reuired us to install imagegd library run to install `apt-get install libgd-dev` 

we need to apped that to the configure and also add the ` --module-path=/etc/nginx/modules`

````
sudo ./configure --sbin-path=/usr/bin/nginx --conf-path=/etc/nginx/nginx.conf --error-log-path=/var/log/nginx/error.log --http-log-path=/var/log/access.log --with-pcre --pid-path=/var/run/nginx.pd  --with-http_ssl_module --with-http_image_filter_module --module-path=/etc/nginx/modules

````
Run
````
make 
make install
````

Add the module path and to test it as

````
load_module modules/ngx_http_image_filter_module.so
location =/thumb.png {
    image_filter rotate 180;
}
````



