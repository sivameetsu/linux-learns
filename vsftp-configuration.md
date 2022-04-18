## VSFTPD CONFIGURATION

 **What is Fftp?**

FTP is a standard network protocol used for the transfer of files between a client and server on a computer network

**What is vsftpd?**

vsftpd stands for very secure FTP daemon. It is secure, stable and extremely fast. If you want to setup complicated FTP, then go with vsftpd. It has ability to handle large numbers of connections efficiently and securely.

**Examine the case requirements**

|     SERVER      | 	   ACT AS  |	   IP ADDRESS    |   OS      |   PACKAGES    |
|-----------------|-------------|------------------|-----------|----------------|
|    centos       |	server      |	192.168.0.2      | centos	   |   server and client |
|    ubuntu       |	client      | 192.168.0.3      |	ubuntu    |   client & Gui |

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
 anonymous_enable=NO
 local_enable=YES
 local_enable=YES
 local_umask=022
 dirmessage_enable=YES
 xferlog_enable=YES 
 connect_from_port_20=YES
 xferlog_std_format=YES
 ftpd_banner=Welcome to blah FTP service.  # uncomment
 ascii_upload_enable=YES                   # uncomment
 ascii_download_enable=YES
 chroot_list_file=/etc/vsftpd/chroot_list  # uncomment => create chroot_list file in /etc/vsftpd/chroot_list add your users
 chroot_local_user=YES                     # uncomment
 chroot_list_enable=YES
 ls_recurse_enable=YES                     # uncoment
 vsftpd_log_file=/var/log/vsftpd.log
 user_config_dir=/etc/vsftpd/users_list
  ```
  
 **Enable log file for Ftp**
 
The more important one is logging. When a user performs an operation, we can track it for auditing purposes. You cannot obtain audit information unless  you have a log.

add the some parameters in `vsftpd.conf` file

```bash
vsftpd_log_file=/var/log/vsftpd.log
```

**Enable the user list file**

```bash
user_config_dir=/etc/vsftpd/users_list
```

**Restart the service**
 
 ```bash
 systemctl restart vsftpd
 systemctl enable vsftpd 
 ```
 
 **Create user and userpassword**
 
 ```bash
 sudo useradd ftpuser1
 sudo passwd ftpuser1
 sudo useradd ftpuser2
 sudo passwd ftpuser2
 ```
 
 **Create a directory and assign it to 755 authentications**
 
 ```bash
 sudo mkdir dodo
 sudo chmod 0755 dodo/
 ```
 
 ## **Firewall configuration**
 
 **Firwall whitelist**
 
 ```bash
 firewall-cmd --permanent --add-service=samba
 firewall-cmd --reload
```
**stop and disable the firewall**

```bash  
systemctl stop firewalld
systemctl disable firewalld
 ```
   
 **SELINUX configuration**
   
 CentOS will always enable selinux, so you must disable it.

 File location `/etc/selinux/conf`
     
 **Client Installation**
 
```bash
 sudo apt update
 sudo apt install ftp -y
```
