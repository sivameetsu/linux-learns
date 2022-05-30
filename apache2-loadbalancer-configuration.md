
_Load Balancing Process_

 Load balancing is the process of distributing network traffic across multiple servers. This ensures no single server bears too much demand. B_Load Balancing Process_

 Load balancing is the process of distributing network traffic across multiple servers. This ensures no single server bears too much demand. By spreading the work evenly, load balancing improves application responsiveness. It also increases availability of applications and websites for users.


 file:///home/dodo/Pictures/Screenshots/Screenshot%20from%202022-05-30%2018-33-53.png


**_configuration_**

In this section 2 apache container running as a server
  * Apache1
  * Apache2

_create Apache DockerFile_   

* Refer this post to create Apache container
```bash

https://github.com/dodo-foundation/linux-learns/blob/main/dockercustom_https.md

```

once create Apache2 image run the image to create 2 container with Diffrent port like this

```bash

docker run -d -p 8081:80 --name Apache1 imageid
docker run -d -p 8082:80 --name Apache1 imageid

```
and check ur container running status 

---

### Apache Configuration file 

```bash

sudo vim /etc/apache2/sites-available/load_balance.conf

```
_sample load balance file_

```bash
<VirtualHost *:80>
<Proxy balancer://mycluster>
    BalancerMember http://localhost:8081
    BalancerMember http://localhost:8082
</Proxy>

    ProxyPreserveHost On

    ProxyPass / balancer://mycluster/
    ProxyPassReverse / balancer://mycluster/
</VirtualHost>
```
_Check ur config_

```bash
apache2ctl -t
sudo systemctl restart apache2.service
```y spreading the work evenly, load balancing improves application responsiveness. It also increases availability of applications and websites for users.


**_configuration_**

In this section 2 apache container running as a server
  * Apache1
  * Apache2

_create Apache DockerFile_   

* Refer this post to create Apache container
```bash

https://github.com/dodo-foundation/linux-learns/blob/main/dockercustom_https.md

```

once create Apache2 image run the image to create 2 container with Diffrent port like this

```bash

docker run -d -p 8081:80 --name Apache1 imageid
docker run -d -p 8082:80 --name Apache1 imageid

```
and check ur container running status 

---

### Apache Configuration file 

```bash

sudo vim /etc/apache2/sites-available/load_balance.conf

```
_sample load balance file_

```bash
<VirtualHost *:80>
<Proxy balancer://mycluster>
    BalancerMember http://localhost:8081
    BalancerMember http://localhost:8082
</Proxy>

    ProxyPreserveHost On

    ProxyPass / balancer://mycluster/
    ProxyPassReverse / balancer://mycluster/
</VirtualHost>
```
_Check ur config_

```bash
apache2ctl -t
sudo systemctl restart apache2.service
```


