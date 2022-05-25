## vsftpd configuration

 **What is Ftp?**

FTP is a standard network protocol used for the transfer of files between a client and server on a computer network

**What is vsftpd?**

vsftpd stands for **Very Secure FTP Daemon**. It is secure, stable and extremely fast. If you want to setup complicated FTP, then go with vsftpd. It has ability to handle large numbers of connections efficiently and securely.

**Examine the case requirements**

|     SERVER      | 	   ACT AS  |	   IP ADDRESS   |   PACKAGES    |
|-----------------|-------------|------------------|----------------|
|    centos       |	server      |	192.168.0.2      |   server and client |
|    ubuntu       |	client      | 192.168.0.3      |   client & Gui |

**Server Installation**

if already is not installed,we must install the vsftpd package on server machine

```bash
sudo yum update -y
sudo yum install vsftpd -y
```

**Process flow** 
 
I have two users who must authenticate and upload flies to the ftp folder

* ftpuser1
* ftpuser2
 
**Modification of the configuration based on customization**

Once the Ftp packages have been installed,you can use this location to determine whether or not file exist.if the file exists,you must backup it before    making changes
  
 File location `/etc/vsftpd/vsftpd.conf`
 
 ```bash
# Based on this value you can insert or update the config file

anonymous_enable=NO line no 25
local_enable=YES line no 28
write_enable=YES line no 31
local_umask=022 line no 35
dirmessage_enable=YES line no 48
xferlog_enable=YES line no 57
xferlog_std_format=YES line no 74
ascii_upload_enable=YES
ascii_download_enable=YES
ftpd_banner=Welcome to Radiant FTP service.
listen=YES line no 14
listen_ipv6=NO line no 22
pam_service_name=vsftpd line no 145
userlist_enable=YES
tcp_wrappers=YES
use_localtime=YES line no 54
user_config_dir=/etc/vsftpd/users
allow_writeable_chroot=YES
```
  
 **Enable log file for Ftp**
 
The more important one is logging. When a user performs an operation, we can track it for auditing purposes. You cannot obtain audit information unless  you have a log.

add the some parameters in `vsftpd.conf` file

```bash
vsftpd_log_file=/var/log/vsftpd.log
```

 **Create user and userpassword**
 
 ```bash
 sudo useradd ftpuser1
 sudo passwd ftpuser1
 ```

 **Create a directory and assign it to 755 authentications**
 
 ```bash
mkdir /etc/vsftpd/users
mkdir /var/www/html/ftpuser1
chown ftpuser1:ftpuser1 /var/www/html/ftpuser1
 ```
 
_**Enable the user list file**_

```bash
echo "local_root=/var/www/html/ftpuser1" | tee /etc/vsftpd/users/ftuser1 
```

_**Restart the service**_
 
 ```bash
 systemctl restart vsftpd
 systemctl enable vsftpd 
 ```

 **Firewall configuration**
 
 ---
 
 
 _**Firwall whitelist**_
 
 ```bash
 firewall-cmd --permanent --add-service=samba
 firewall-cmd --reload
```
_**stop and disable the firewall**_

```bash  
systemctl stop firewalld
systemctl disable firewalld
 ```
   
_**SELINUX configuration**_
   
 CentOS will always enable selinux, so you must disable it.

 File location `/etc/selinux/conf`
     
_**Client Installation**_
 
```bash
 sudo apt update
 sudo apt install filezilla -y
```
