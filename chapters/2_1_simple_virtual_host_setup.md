# nginx config from scratch

For this exercise copy the contents of the folder

`exercise/2_simple_site` to `/home/user_name/site` or any of your preferred location.We will be using `/home/epynic/site`

The HTML page is a cobmination of css & image file. Just to see how nginx serves the content of the respective files.

![html sample page](screenshots/2_simple_html_site.png?raw=true "Nginx Page")


#### Create the default nginx.conf file

Edit the default nginx config file at \
`sudo vi /etc/nginx/nginx.conf `

Delete all of the content of the file and add the below content.
````
events{}
http{
    server{
        listen 80;
        server_name PUBLIC IP;
        root /home/epynic/site;
    }
}
````
> File : /etc/nginx/nginx.conf

Save and exit the file.

#### Reload nginx

````
sudo nginx -t 
sudo systemctl reload nginx 
````

Navigate to your PublicIP - The HTML page will look broken as the css files are not processed.

To verify 

```` curl -I http://PUBLIC IP/bootstrap.min.css ````

> The content type would be _Content-Type: text/plain_

While the css files are loaded, but serves them as plain text files.

By default nginx does not know how to server the css and other file types so we need to include the mime.type that is provided by nginx by default to the http context.


````
events{}
http{
    include mime.types;
    server{
        listen 80;
        server_name PUBLIC IP;
        root /home/epynic/nginxwww/sites/simple;
    }
}
````
> File : /etc/nginx/nginx.conf

Save and reload nginx.