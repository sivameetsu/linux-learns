#### Centos samba configuration

**what is samba?**

If you are either a power home user or you are in a business environment, you know the importance of machines being able to see one another. "Sharing Files  & Folders Between Linux, Mac, and Windows" which skimmed this topic, showing how simple it is to allow these different operating systems to see one another - with the help of Samba. 

**what is nmbd?**

This daemon handles all name registration and resolution requests. It is the primary vehicle involved in network browsing. It handles all UDP-based protocols. The nmbd daemon should be the first command started as part of the Samba startup process.

**what is smbd?**

This daemon handles all TCP/IP-based connection services for file- and print-based operations. It also manages local authentication. It should be started immediately following the startup of nmbd.


