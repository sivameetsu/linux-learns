#### apache-reverse-proxy-configuration.md

---

_reverse proxy process_

In addition to being a "basic" web server, and providing static and dynamic content to end-users, Apache httpd (as well as most other web servers) can also act as a reverse proxy server, also-known-as a "gateway" server.

In such scenarios, httpd itself does not generate or host the data, but rather the content is obtained by one or several backend servers, which normally have no direct connection to the external network. As httpd receives a request from a client, the request itself is proxied to one of these backend servers, which then handles the request, generates the content and then sends this content back to httpd, which then generates the actual HTTP response back to the client.

There are numerous reasons for such an implementation, but generally the typical rationales are due to security, high-availability, load-balancing and centralized authentication/authorization. It is critical in these implementations that the layout, design and architecture of the backend infrastructure (those servers which actually handle the requests) are insulated and protected from the outside; as far as the client is concerned, the reverse proxy server is the sole source of all content.

_A typical implementation is below_

![image](https://user-images.githubusercontent.com/57703276/170813018-f09b2467-7f12-44c7-9873-26741706e406.png)


create the domain in the name of domain

```bash

sudo vim /etc/apache2/sites-available/reverse.fourtimes.ml.conf

```

use this conf file

```bash

<VirtualHost *:80>

        # Domain mapping section
        ServerAdmin webmaster@fourtimes.ml
        Servername fourtimes.ml
        
        # Reverse proxy configuration
        ProxyPass "/"  "http://www.google.com/"
        ProxyPassReverse "/"  "http://www.google.com/"
        
        # Logs location
        ErrorLog ${APACHE_LOG_DIR}/fourtimes.ml.error.log
        CustomLog ${APACHE_LOG_DIR}/fourtimes.ml.access.log combined
        
</VirtualHost>

```

enable the site location

```bash

a2ensite reverse.fourtimes.ml.conf

```

_restart the `apache2` service_

```bash

systemctl restart apache2

```

_conslusion_

When you visit the domain `fourtimes.ml` your browser will automatically redirect to google.com.

**_reverse proxy with https configuration_**


```bash


```

