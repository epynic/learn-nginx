## Building nginx from source

Download latest mainline nginx version from https://nginx.org/en/download.html

At the time of writeup it is `nginx-1.15.12`

#### Download & Extract 

Download

`wget https://nginx.org/download/nginx-1.15.12.tar.gz`

Extract file

`tar -xvf nginx-1.15.12.tar.gz`


#### Other dependency to be installed

````
sudo apt-get install build-essential
sudo apt-get install libpcre3 libpcre3-dev zlib1g zlib1g-dev libssl-dev 
````

#### Configure nginx with the minimal config

````
sudo ./configure --sbin-path=/usr/bin/nginx --conf-path=/etc/nginx/nginx.conf --error-log-path=/var/log/nginx/error.log --http-log-path=/var/log/access.log --with-pcre --pid-path=/var/run/nginx.pd  --with-http_ssl_module
````

Read more about configure options at https://nginx.org/en/docs/configure.html


#### To build and install nginx 

````
sudo make 
sudo make install
````

#### Add nginx startup entry.

Create a nginx.service file `sudo vi /lib/systemd/system/nginx.service `

And add the below content, save and exit
````
[Unit]
Description=The NGINX HTTP and reverse proxy server
After=syslog.target network.target remote-fs.target nss-lookup.target
[Service]
Type=forking
PIDFile=/var/run/nginx.pid
ExecStartPre=/usr/bin/nginx -t
ExecStart=/usr/bin/nginx
ExecReload=/usr/bin/nginx -s reload
ExecStop=/bin/kill -s QUIT $MAINPID
PrivateTmp=true
[Install]
WantedBy=multi-user.target
````

1. To add an startup entry Run `systemctl enable nginx`
2. To start nginx manually Run `systemctl start nginx`
3. To check nginx status Run `systemctl status nginx`