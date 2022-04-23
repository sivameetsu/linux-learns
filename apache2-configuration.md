#### apache2 configuration

---

**What is apache2**

Apache is the most commonly used Web server on Linux systems. Web servers are used to serve Web pages requested by client computers. Clients typically request and view Web pages using Web browser applications such as Firefox, Opera, Chromium, or Internet Explorer.

**Requirements**

|SERVER|IPADDRESS|
|---|---|
|Ubuntu| 192.168.0.10|

**apache2 Installation**

If the package is not found, use the following commands to install apache2.

```bash

sudo apt update
sudo apt install apache2 -y

```
**apache2 installtion verification**

After installing the apache2 package, use this command to verify the apache2 packages.

```bash
# configuration details 
apache2 -V

# version details
apache2 -v
```
![image](https://user-images.githubusercontent.com/98270930/164885249-7540a0f3-f4f3-4978-88c5-e6cb02042210.png)

**service handling process**

We can start the service after apache2 verification.

```bash
sudo systemctl start apache2
sudo systemctl status apache2
```

![image](https://user-images.githubusercontent.com/98270930/164885150-46e5e883-21d0-4abd-8f0b-bc6282c69c99.png)

**apache2 listen ports**

```bash
sudo ss -tln
```

![image](https://user-images.githubusercontent.com/98270930/164885528-9f6b6cb4-2781-45be-8e5c-f42fd3b218f9.png)

**outout verification in commandline**

```bash
curl -o /dev/null -s -w "%{http_code}\n" http://localhost
```

![image](https://user-images.githubusercontent.com/98270930/164885623-aba68ccd-0bf8-4ad2-92f3-b757ed3f009a.png)


**apache file structure details**

|LOCATION| PURPOSE |
|---|---|
| /etc/apache2 | configuration files |
| /var/log/apache2 | logs files |
|/var/www/html|Default path |
|/etc/hosts|host file|

**To Modify Apache2 Sites available Conf**
---

In this section we can modify one conf file
```bash
cd /etc/apache2/sites-available
```
![Screenshot from 2022-04-23 18-21-06](https://user-images.githubusercontent.com/102893121/164895480-7f6f38b1-444a-4091-a4ac-752171f27f97.png)

create new domain conf file or copy the 000-default.conf file  

```bash
sudo vim /etc/apache2/sites-available/dev.conf
```
![Screenshot from 2022-04-23 18-35-34](https://user-images.githubusercontent.com/102893121/164895804-6edb0681-989a-448c-ba52-66b2cfe0bbd3.png)

**Note: Line no 12,13,14 change** 

Then Enable ur site , Disable old Site and reload apache2 server

```bash
sudo a2ensite dev.conf
sudo a2dissite ooo-default_bak.conf
sudo systemctl reload apache2
```
**output Verification for command line**

![Screenshot from 2022-04-23 19-02-58](https://user-images.githubusercontent.com/102893121/164896808-be3f053f-541d-4b33-85ad-8b19c47722c5.png)

**Vhost Configuration**
---

we can make directory in default path and chage the permission and ownership 

```bash
sudo mkdir /var/www/your_domain
sudo chown -R USER:USER /var/www/domain name
sudo chmod -R 755 /var/www/domain name
```
Then create html file for website index page

```bash
sudo touch /var/www/html/index.html
```
**sample HTML page Below**

![Screenshot from 2022-04-23 19-09-22](https://user-images.githubusercontent.com/102893121/164898224-7f97b743-ce1f-412e-962c-208c81f58312.png)

**In web browser Result**
![Screenshot from 2022-04-23 19-12-42](https://user-images.githubusercontent.com/102893121/164900709-b65cede7-ce1d-4906-a0da-9d5692b9f0f4.png)

## SSL configuration

**What is SSL**
SSL stands for Secure Sockets Layer and, in short, it's the standard technology for keeping an internet connection secure and safeguarding any sensitive data that is being sent between two systems

---









