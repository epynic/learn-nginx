## Install via APT package manager
* This installation  process is Quick & Easy 
* Downside - No Support for additional modules & customization.

#### To Install and run nginx
````
apt-get update 
apt-get install nginx  
`````

#### To verify nginx process is running.

```` ps aux | grep nginx ````
>a = show processes for all users* \
u = display the process's user/owner* \
x = also show processes not attached to a terminal ,boot processes

#### Verify nginx installation.
Point your browser to Instance public IP, you will see the nginx welcome page.

If you dont know your public IP, run `curl ifconfig.me` in terminal.

By default all nginx configs can be found at
`/etc/nginx/`
