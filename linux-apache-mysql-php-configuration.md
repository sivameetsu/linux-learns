## Configuration of apache2 with two domains:

We have to check the apache2 packages

```bash
apt list apache2
```

In case it is not installed, we can use this command.

```bash

sudo apt update
sudo apt install apache2 -y

```

### We have to consider the `fourtimes.ml` domain. The below steps are followed in this domain.

| Domain       | document root      |
| ------------ | ------------------ |
| fourtimes.ml | /var/www/fourtimes |

**create the document root for this vhost configuration**

```bash

sudo mkdir -p /var/www/fourtimes.ml
sudo vim /var/www/fourtimes.ml/index.html

```

_remove the default configuration_

```bash

rm -rf /etc/apache2/sites-enabled/default
rm -rf /etc/apache2/sites-available/default

```

_SSL Certificate Creation_

We got the SSL from zerossl.com. These are the documents we have.

![image](https://user-images.githubusercontent.com/57703276/170814060-b0817bd0-d722-4d8f-8a25-052965a81130.png)

download the file and move to target location

```bash

mkdir -p /etc/apache2/ssl

cp * /etc/apache2/ssl # copy for all in this file.
                        [or]
cp ca_bundle.crt        /etc/apache2/ssl/ca_bundle.crt
cp certificate.crt      /etc/apache2/ssl/certificate.crt
cp private.key          /etc/apache2/ssl/private.key

```

_Vhost configuration with **http** to **https** redirection_

`/etc/apache2/sites-enabled/fourtimes.ml.conf`

```bash

sudo vim /etc/apache2/sites-enabled/fourtimes.ml.conf

```

`/etc/apache2/sites-enabled/fourtimes.ml.conf`

```


# HTTPS SECTION

<VirtualHost *:443>

        ServerAdmin  webmaster@fourtimes.ml
        Servername   fourtimes.ml
        DocumentRoot /var/www/fourtimes.ml

        # HTTP TO HTTPS REDIRECTION
        SSLEngine                on
        SSLCertificateFile       /etc/apache2/ssl/certificate.crt
        SSLCertificateKeyFile    /etc/apache2/ssl/private.key
        SSLCertificateChainFile  /etc/apache2/ssl/ca_bundle.crt

        # APACHE2 LOGS
        ErrorLog  ${APACHE_LOG_DIR}/fourtimes.ml.error.log
        CustomLog ${APACHE_LOG_DIR}/fourtimes.ml.access.log combined

</VirtualHost>

# HTTP SECTION

<VirtualHost *:80>

        ServerAdmin webmaster@fourtimes.ml
        Servername fourtimes.ml
        DocumentRoot /var/www/fourtimes.ml
        # Redirect permanent / https://fourtimes.ml/
        RewriteEngine On
        RewriteCond %{HTTPS} off
        RewriteRule (.*) https://%{HTTP_HOST}%{REQUEST_URI}

        ErrorLog ${APACHE_LOG_DIR}/fourtimes.ml.error.log
        CustomLog ${APACHE_LOG_DIR}/fourtimes.ml.access.log combined

</VirtualHost>

```
_Enter the domain in hosts_

```bash
sudo /etc/hosts

add this content:
----------------
192.168.20.83 fourtimes.ml
```
_validation the apache2_

```bash
apache2ctl -t
```

_restart the service_

```bash
systemctl restart apache2
```

**OutPut:**
It will give your domain secure access. We can get to https://fourtimes.ml using a browser.

---

### We have to consider the `dodo-found` domain. The below steps are followed in this domain.

| Domain        | document root      |
| ------------- | ------------------ |
| dodo-found.tk | /var/www/dodofound |

create the document root for this vhost configuration

```bash
sudo mkdir -p /var/www/dodofound
sudo vim /var/www/dodofound/index.html
```

_vhost configuration_

`/etc/apache2/sites-enabled/dodo-found.tk.conf`

_SSL Certificate Creation_

We got the SSL from zerossl.com. These are the documents we have.

![image](https://user-images.githubusercontent.com/57703276/170814060-b0817bd0-d722-4d8f-8a25-052965a81130.png)

download the file to the target machine and move to tager get location

**Note- In this example, the content of the certificate.crt and ca_bundle.crt files is copied to a new file and named certificate.crt.\***

```bash
mkdir -p /etc/apache2/ssl

cp * /etc/apache2/ssl # copy for all in this file.
                        [or]
cp ca_bundle.crt        /etc/apache2/ssl/ca_bundle.crt
cp certificate.crt      /etc/apache2/ssl/certificate.crt
cp private.key          /etc/apache2/ssl/private.key

```

_vhost configuration with **http** to **https** redirection_

```bash
sudo vim /etc/apache2/sites-enabled/dodo-found.tk.conf
```

`/etc/apache2/sites-enabled/dodo-found.tk.conf`

```bash
<VirtualHost *:443>

        ServerAdmin  webmaster@dodo-found.tk
        Servername   dodo-found.tk
        DocumentRoot /var/www/dodo-found.tk

        # HTTP TO HTTPS REDIRECTION
        SSLEngine                on
        SSLCertificateFile       /etc/apache2/ssl/certificate.crt
        SSLCertificateKeyFile    /etc/apache2/ssl/private.key
        SSLCertificateChainFile  /etc/apache2/ssl/ca_bundle.crt

        # APACHE2 LOGS
        ErrorLog  ${APACHE_LOG_DIR}/dodo-found.tk.error.log
        CustomLog ${APACHE_LOG_DIR}/dodo-found.tk.access.log combined

</VirtualHost>

# HTTP SECTION

<VirtualHost *:80>

        ServerAdmin webmaster@dodo-found.tk
        Servername dodo-found.tk
        DocumentRoot /var/www/dodo-found.tk
        # Redirect permanent / https://dodo-found.tk/
        RewriteEngine On
        RewriteCond %{HTTPS} off
        RewriteRule (.*) https://%{HTTP_HOST}%{REQUEST_URI}

        ErrorLog ${APACHE_LOG_DIR}/dodo-found.tk.error.log
        CustomLog ${APACHE_LOG_DIR}/dodo-found.tk.access.log combined

</VirtualHost>
```

Enter the domain in hosts

```bash
sudo /etc/hosts

add this content:
----------------
192.168.20.83 dodo-found.tk
```
_validation the apache2_

```bash
sudo apache2ctl -t
```

_restart the service_

```bash
sudo systemctl restart apache2
```
**OutPut:
It will give your domain secure access. We can get to https://dodo-found.tk using a browser.

---

### Create a MySQL user and database, then assign privileges to the database.

We can create a `fourtimes`, `dodofound` user and create the `fourtimes_db`, `dodofound_db` database.

| User_name | Database_name | password | host|
| --------- | --------- | ------------------- | --------- |
| fourtimes | fourtimes_db | Passwordchanged@123 | localhost |
| dodofound | dodofound_db | Passwordchanged@123 | localhost |

_database usage_

- We build the 'fourtimes_db' database, which can only be accessed by the 'fourtimes' user.

- We build the 'dodofound_db' database, which can only be accessed by the 'dodofound' user.

Create a root password and set privileges in this section.

_Install the packages of mysql_
```bash

sudo apt update
sudo apt-get install mysql-server -y
sudo mysql_secure_installation

```

To log in with root and a password, go here.

```bash

sudo mysql -u root -p
root password

```

Then create a user and  database, and assign privileges to the database.

_Create User and Database for fourtimes_

```bash

CREATE USER 'fourtimes'@'localhost' IDENTIFIED BY 'Passwordchanged@123';
CREATE DATABASE fourtimes;
GRANT all ON fourtimes.* TO 'fourtimes'@'localhost';
flush privileges;

```

_Create User and Database for dodofound_

```bash
CREATE USER 'dodofound'@'localhost' IDENTIFIED BY 'Passwordchanged@123';
CREATE DATABASE dodofound;
GRANT all ON dodofound.* TO 'dodofound'@'localhost';
flush privileges;

```

#### Create a VSFTPD account and give it a specific path to access the user.

---

_user document root create_

| user      | password | Path               |
| --------- | -------- | ------------------ |
| fourtimes | a        | /var/www/fourtimes |
| dodofound | b        | /var/www/dodofound |

_vsftpd package installation_

```bash

sudo apt update
sudo apt install vsftpd -y

```

_vsftpd configuration for fourtimes_
```bash
# Install the vsftpd packages
sudo apt update && apt install vsftpd -y

# create the new user
sudo useradd -m -s /bin/bash ashli

#  set the password of new user
echo "ashli:password" | sudo chpasswd

# Create a directory
sudo mkdir -p /etc/vsftpd/users /var/www/html/fourtimes.ml /var/run/vsftpd/empty

# give the owner permission of new user
sudo chown -R ashli:ashli /var/www/html/fourtimes.ml

# give the local root
echo "local_root=/var/www/html/fourtimes.ml" | sudo tee -a /etc/vsftpd/users/ashli

# give the change root
echo "ashli" | sudo tee /etc/vsftpd.chroot_list

# Create a configuration file in vsftpd
vim /etc/vsftpd.conf

add this content in vsftpd.conf file:
-------------------------------------
listen=YES
listen_ipv6=NO
anonymous_enable=NO
local_enable=YES
write_enable=YES
local_umask=022
dirmessage_enable=YES
use_localtime=YES
xferlog_enable=YES
connect_from_port_20=YES
xferlog_file=/var/log/vsftpd.log
xferlog_std_format=NO
idle_session_timeout=600
data_connection_timeout=120
ascii_upload_enable=YES
ascii_download_enable=YES
ftpd_banner=Welcome to fourtimes.ml FTP service.
chroot_local_user=NO
chroot_list_enable=YES
user_config_dir=/etc/vsftpd/users
allow_writeable_chroot=YES
secure_chroot_dir=/var/run/vsftpd/empty
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
ssl_enable=NO
chroot_list_file=/etc/vsftpd.chroot_list

#  start the vsftpd service
sudo systemctl start vsftpd

#  status of vsftpd service
sudo systemctl status vsftpd
```
_vsftpd configuration for dodofound_
```bash
# Install the vsftpd packages
sudo apt update && apt install vsftpd -y

# create the new user
sudo useradd -m -s /bin/bash ashli

#  set the password of new user
echo "dodofound:password123" | sudo chpasswd

# Create a directory
sudo mkdir -p /etc/vsftpd/users /var/www/html/dodo-found.tk /var/run/vsftpd/empty

# give the owner permission of new user
sudo chown -R ashli:ashli /var/www/html/dodo-found.tk

# give the local root
echo "local_root=/var/www/html/dodo-found.tk" | sudo tee -a /etc/vsftpd/users/ashli

# give the change root
echo "ashli" | sudo tee /etc/vsftpd.chroot_list

# Create a configuration file in vsftpd
vim /etc/vsftpd.conf

add this content in vsftpd.conf file:
-------------------------------------
listen=YES
listen_ipv6=NO
anonymous_enable=NO
local_enable=YES
write_enable=YES
local_umask=022
dirmessage_enable=YES
use_localtime=YES
xferlog_enable=YES
connect_from_port_20=YES
xferlog_file=/var/log/vsftpd.log
xferlog_std_format=NO
idle_session_timeout=600
data_connection_timeout=120
ascii_upload_enable=YES
ascii_download_enable=YES
ftpd_banner=Welcome to dodo-found.tk FTP service.
chroot_local_user=NO
chroot_list_enable=YES
user_config_dir=/etc/vsftpd/users
allow_writeable_chroot=YES
secure_chroot_dir=/var/run/vsftpd/empty
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
ssl_enable=NO
chroot_list_file=/etc/vsftpd.chroot_list

#  start the vsftpd service
sudo systemctl start vsftpd

#  status of vsftpd service
sudo systemctl status vsftpd
```

**Note:** If the error /home directory does not appear, check your user shell type, delete your user, then create a new user with the `adduser` command.
