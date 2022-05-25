#### apache2 configuration

---

**What is apache2**

Apache is the most commonly used Web server on Linux systems. Web servers are used to serve Web pages requested by client computers. Clients typically request and view Web pages using Web browser applications such as Firefox, Opera, Chromium, or Internet Explorer.

_Requirements_

|SERVER|IPADDRESS|
|---|---|
|Ubuntu| 192.168.0.10|

_apache2 Installation_

If the package is not found, use the following commands to install apache2.

```bash

sudo apt update
sudo apt install apache2 -y

```
_apache2 installtion verification_

After installing the apache2 package, use this command to verify the apache2 packages.

_service handling process_

This command can be used to start the service and check its status.

```bash
sudo systemctl start apache2
sudo systemctl status apache2
```

_apache2 listen ports_

```bash
sudo ss -tln
```

_apache file structure details_

in this section we can use **dodo-found.tk** domain

|LOCATION| PURPOSE |
|---|---|
| /etc/apache2 | configuration files |
| /var/log/apache2 | logs files |
|/var/www/html|Default path |
|/etc/hosts|host file|

**Vhost Configuration**

---------
---------

we can make directory in default path and chage the permission and ownership 

```bash
sudo mkdir /var/www/your_domain
sudo chown -R dodo:dodo /var/www/dodofound
sudo chmod -R 755 /var/www/dodofound
```
Then create html file for website index page

```bash
sudo touch /var/www/html/index.html
```
 _sample index file_
 
```bash
<html>
    <head>
        <title>Welcome to DoDo Foundation!</title>
    </head>
    <body>
        <h1>Success!  The DoDo found virtual host is working!</h1>
    </body>
</html>
```

**To Modify Apache2 Sites available Conf**

`-----`

In this section we can modify one conf file

```bash
/etc/apache2/sites-available
```
create new domain conf file or copy the 000-default.conf file  

```bash
sudo vim /etc/apache2/sites-available/dodo-found.conf
```
use this conf file

```bash
<VirtualHost *:80>

        ServerAdmin webmaster@dodo-found.tk
        Servername dodo-found.tk
        DocumentRoot /var/www/dodo-found.tk

        ErrorLog ${APACHE_LOG_DIR}/dodo-found.tk.error.log
        CustomLog ${APACHE_LOG_DIR}/dodo-found.tk.access.log combined
</VirtualHost>
```

Then enable your site, disable the old one, and restart the Apache2 server.

```bash
sudo a2ensite dev.conf
sudo a2dissite ooo-default_bak.conf
sudo systemctl reload apache2
```

## SSL configuration

**What is SSL**
SSL stands for Secure Sockets Layer and, in short, it's the standard technology for keeping an internet connection secure and safeguarding any sensitive data that is being sent between two systems

---

In this Section first Enable SSL and reload the server

```bash
enable SSL
sudo a2enmod ssl
sudo systemctl restart apache2
```

**Create SSL key for Below command line**

```bash
sudo openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout /etc/ssl/private/apache-selfsigned.key -out /etc/ssl/certs/apache-selfsigned.crt
```
In this case im use https://zerossl.com/ to create the ssl certificate

**Config SSL Cetr to Apache**

```bash
sudo vim /etc/apache2/sites-available/dev.conf
```
add SSL cert for config file output shown below

```bash
<VirtualHost *:443>

        ServerAdmin webmaster@dodo-found.tk
        Servername dodo-found.tk
        DocumentRoot /var/www/dodo-found.tk

        SSLEngine                on
        SSLCertificateFile       /etc/ssl/certificate.crt
        SSLCertificateKeyFile    /etc/ssl/privates/private.key
        SSLCertificateChainFile  /etc/ssl/ca_bundle.crt

        ErrorLog ${APACHE_LOG_DIR}/dodo-found.tk.error.log
        CustomLog ${APACHE_LOG_DIR}/dodo-found.tk.access.log combined
</VirtualHost>


<VirtualHost *:80>

        ServerAdmin webmaster@dodo-found.tk
        Servername dodo-found.tk
        DocumentRoot /var/www/dodo-found.tk

        ErrorLog ${APACHE_LOG_DIR}/dodo-found.tk.error.log
        CustomLog ${APACHE_LOG_DIR}/dodo-found.tk.access.log combined
</VirtualHost>                 
```

then reload Apache2 server

```bash
sudo systemctl reload apache2
```
Using your web browser, examine the output result



