#### Centos samba configuration

**what is samba?**

If you are either a power home user or you are in a business environment, you know the importance of machines being able to see one another. "Sharing Files  & Folders Between Linux, Mac, and Windows" which skimmed this topic, showing how simple it is to allow these different operating systems to see one another - with the help of Samba. 

**what is nmbd?**

This daemon handles all requests for name registration and resolution. It is the primary mode of transport for network browsing. It is capable of handling all UDP-based protocols. The nmbd daemon should be the first command to be executed during the Samba startup process.

**what is smbd?**

This daemon manages all TCP/IP-based connection services for file- and print-based operations. It also handles local authentication. It should be started as soon as nmbd boots up.

**Examine the case requirements.**

| SERVER | ACT AS | IP ADDRESS | PACKAGES |
| --------------- | --------------- | --------------- | --------------- |
| centos | server | 192.168.0.2 | server and client |
| ubuntu | client | 192.168.0.3 | client & Gui |
| windows | client | 192.168.0.4 | Gui |

**Server installation**

If aleady is not installed, we must install the sambea packages on server machine

```bash
sudo yum update -y
sudo yum install samba samba-client -y
```
**Process flow**

I have two users who must authenticate and upload files to the Samba folder. These two users created a single group in order to easily maintain their privileges.

| user | group |
| --------------- | --------------- | 
| smbuser | dod0 | 
| linuxes | dodo | 

**Modification of the configuration based on customization**

Once the Samba packages have been installed, you can use this location to determine whether or not files exist. If the file exists, you must backup it before making changes.

File location `/etc/samba/smb.conf`

**create group**
 
 ```bash
groupadd dodo
 ```
   
**create user and userpassword**
   
useradd smbuser1
passwd  smbuser1
useradd linuxes
passwd  linuxes
    
**The user is added to the dodo-foundation group**

```bash    
usermod -aG dodo smbuser1
usermod -aG dodo linuxes
```     
     
**Create a diectory and assign it to 0770 authorizations**

```bash   
mkdir /dodo-foundation
chmod 0770 /dodo-foundation
```
      
**modify the directory's groupname**

```bash    
chgrp dodo /dodo-foundation
```

**Unwanted global parameters remove process**

Backup the original config file 

```bash
cp /etc/samba/smb.conf /etc/samba/smb.conf_backup
```

Remove the unwanted section like homes, printers, Prints.
  
 **modifying the smb.conf file with some options**
 
 update the configuration based on what you need.
 
 ```txt
 [dodo-foundation]
 comment=Directory for collaboration of the company's finance team
 browsable=yes
 path=/dodo-foundation
 public=no
 valid users=@dodo
 write list=@dodo
 writeable=yes
 create mask=0770
 Force create mode=0770
 force group=dodo
 ```
  
 **Restart the service**
 
 ```bash
 sudo systemctl start smbd nmbd
 ```
 
 **Add the user into samba authendication**
 
```bash        
smb -a smbuser1
smb -a linuxes
```
     
**Access the samba server from local machine*

```bash
smbclient -L localhost -U smbuser1
smbclient -L localhost -U linuxes
```
**Output**
![centos](https://user-images.githubusercontent.com/98270930/163677237-e71152c5-c74e-43ee-9974-a863ed54ebb5.png)


**Access the samba server from ubuntu machine*

commnd line

```bash
smbclient -L 192.168.0.2 -U smbuser1
smbclient -L 192.168.0.2 -U linuxes
```
Graphical user interface

![ubuntu](https://user-images.githubusercontent.com/98270930/163677190-b59b90c3-87b4-4ab1-bc62-e95ac7eb6103.png)





**Access the samba server from windows machine*
