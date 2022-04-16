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

**Modification of the configuration based on customization**

Once the Samba packages have been installed, you can use this location to determine whether or not files exist. If the file exists, you must backup it before making changes.

File location `/etc/samba/smb.conf`

**Unwanted global parameters remove process**



