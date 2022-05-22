## nginx configuration

**What is Nginx?**

Nginx (pronounced ‘engine X’) is an alternative to Apache and is considered to be one of the most popular HTTP web servers in the world. As opposed to Apache, Nginx tends to consume fewer resources and improves server responsiveness. Its event-driven design is what makes it resource-friendly.

Above all, it allows admins to set up advanced configurations and can deal with a high load of concurrent connections. Besides being a good fit for an HTTP web server, Nginx also works as a reverse proxy, load balancer, and standard mail server.


**Requirements**

  | SERVER 	       |  IPADDRESS |
  | --- | --- |
  | Ubuntu 	       |  192.168.0.10 |

**NGINX Installation**

Nginx is available in Ubuntu’s default repositories, it is possible to install it from these repositories using the apt packaging system.
```bash
sudo apt update
sudo apt install nginx
```

**NGINX installation verification**

after instaling the nginx package, use this commmand to verification the nginx package

```bash
# configuration details 
    nginx -v
```

to check service status

```bash
sudo systemctl status nginx.service 
```

**Config Nginx**

In this section **fourtimes.ml** domain config

To create domain folder using and change perission to the folder

```bash
sudo mkdir -p /var/www/fourtimes.ml
sudo vim /var/www/fourtimes.ml/index.html
sudo chown -R dodo:dodo /var/www/fourtimes.ml/
```
![Screenshot from 2022-05-22 19-05-42](https://user-images.githubusercontent.com/102893121/169697870-f864dce6-aa56-4704-916b-304fc73611a3.png)

Then change /etc/nginx/sites-available directoy

```bash
cd /etc/nginx/sites-available
```

In this directory already default page are there so backup the file and delete the default file using this command

```bash
cp default default_backup
rm -f default
```
then copy the backup file using ur domain name like this

```bash
cp default_backup fourtimes.ml.conf
```
change root path and server name like below

![Screenshot from 2022-05-22 19-14-16](https://user-images.githubusercontent.com/102893121/169698221-8e9ecbb1-6b54-4ec5-b9ac-bf15bd4eb43c.png)

In this case i will assign separate access log and error log for my domain, so add the below command for uyour sites available conf file

```bash
access_log /var/log/nginx/fourtimes.ml.access.log;
error_log /var/log/nginx/fourtimes.ml.error.log;
```
```bash 
vim /etc/nginx/sites-available/fourtimes.ml.conf
```
![Screenshot from 2022-05-22 19-19-33](https://user-images.githubusercontent.com/102893121/169699164-96fa7e01-d9cd-43f7-bfc8-baeeeb7ab10a.png)



then enable the file by creating a link from it to the sites-enabled directory,

```bash 
sudo ln -s /etc/nginx/sites-available/fourtimes.ml.conf /etc/nginx/sites-enabled/
```

in this case i will face error so i skip the step to move on

so erase the link using rm command

```bash
rm -rf fourtimes.ml.conf 
```
then cop the sites available conf file insert directly to sites enables directory

```bash
sudo cp ../sites-available/al.fourtimes.ml.conf .
```

then check nginx status

``bash
 nginx -t
```
![Screenshot from 2022-05-22 19-25-50](https://user-images.githubusercontent.com/102893121/169698744-d2b9ac2d-0870-4c35-919e-87be700b5a71.png)

Add ur hosts using this command

```bash
vim etc/hosts
```
![image](https://user-images.githubusercontent.com/102893121/169699049-5fcfb5fe-d193-4e28-bacc-9791fcfe7b63.png)

then restart ur service and check ur index page using this command

```bash
systemctl restart nginx
curi fourtimes.ml
```

![image](https://user-images.githubusercontent.com/102893121/169698940-283b90c0-6342-4b08-87e1-f971abca268b.png)

_ssl and http to https redirection_

`/etc/nginx/sites-enabled/fourtimes.ml.conf`

```conf

server {
    listen       80;
    server_name  fourtimes.ml www.fourtimes.ml;
    return 301 https://$host$request_uri;
    
    location / {
        root   /var/www/fourtimes.ml;
        index  index.html index.htm;
    }
}

server {
    listen                443 ssl;
    ssl                  on;
    ssl_certificate      /etc/nginx/ssl-certificate/certificate.crt; 
    ssl_certificate_key  /etc/nginx/ssl-certificate/private.key;
    server_name  fourtimes.ml;
    access_log   /var/log/nginx/fourtimes.ml.access.log;
    error_log    /var/log/nginx/fourtimes.ml.error.log;

    location     / {
        root         /var/www/fourtimes.ml;
        index        index.html index.htm;
    }
}

```

_validation the nginx_

```bash
nginx -t
```

_restart the service_

```bash
systemctl stop nginx
systemctl start nginx 
```

We can validate the domain using http or https in your browser. If you visit the domain http, it will automatically redirect to https.

