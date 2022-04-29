## nginx configuration

**What is Nginx?**

Nginx (pronounced ‘engine X’) is an alternative to Apache and is considered to be one of the most popular HTTP web servers in the world. As opposed to Apache, Nginx tends to consume fewer resources and improves server responsiveness. Its event-driven design is what makes it resource-friendly.

Above all, it allows admins to set up advanced configurations and can deal with a high load of concurrent connections. Besides being a good fit for an HTTP web server, Nginx also works as a reverse proxy, load balancer, and standard mail server.


**Requirements**

  SERVER 	         IPADDRESS

  Ubuntu 	         192.168.0.10

**NGINX Installation**

Nginx is available in Ubuntu’s default repositories, it is possible to install it from these repositories using the apt packaging system.
```bash
sudo apt update
sudo apt install nginx
```

**NGINX installation verification**

after instaaling the nginx package, use this commmand to verification the nginx package
