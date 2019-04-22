# PHP on nginx using php-fpm

#### install php-fpm
```` apt-get install php-fpm ````


````
user www-data

events{}

http{
    include mime.types;

    server{
        listen 80;
        server_name 35.184.52.33;
        root /home/epynic/www;

        index index.php index.html;

        location / {
            try_files $uri $uri/ = 404;
        }

        location ~\.php${
            include fastcgi.conf;
            fastcgi_pass unix:/run/php/php7.1-fpm.sock
        }
    }
}
````

To find the pph-fpm location `find /-name *fpm-sock`