## NTP server configuration

**Network Time Protocol** (NTP) is an internet protocol used to synchronize with computer clock time sources in a network. It belongs to and is one of the 
oldest parts of the TCP/IP suite.  The term NTP applies to both the protocol and the client-server programs that run on computers.


**Requirements**

|OS |SERVICE |PORT|
|---|---|---|
|Ubuntu |NTP |123|


**NTP Installation**

If the package is not found, use the following commands to install NTP.

```bash
sudo apt update
sudo apt install ntp -y
```
**Find Version**
```bash
sntp --version
```
**Edit server Config file**
```bash
vim/etc/ntp.con
```
In this section line no 21 to 24 and 27 and 51 lines are customise for ur needs get backup then edit

to get pool file plz visit for more info ---> https://www.pool.ntp.org/zone/asia

Next restart the service 

```bash
systemctl restart ntp 
```
and check status
```bash
systemctl status ntp
```

## config NTP client

first check the running status  using this command
```bash
systemctl status systemd-timesyncd 
```
then edit conf file
```bash 
 vi /etc/systemd/timesyncd.conf 
 ```
 add ur domain name in last line
 **NTP=ur ntp server name**
 
 then restart
 ```bash
 systemctl restart systemd-timesyncd 
 ```
 and check status using this command
 ```bash
 timedatectl timesync-status 
 ```
 
