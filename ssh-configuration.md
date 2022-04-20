## ssh configuration

**what is ssh?**

SSH is a client program for logging into a remote Linux/Unix server.ssh port runs on TCP port 22 on Ubuntu Linux

**Requirements**

| SERVER | OPERATING SYSTEM | ADDRESS |
|---|---| --- |
| virtual machine | ubuntu | 192.168.0.2 |

**how to install the ssh packages**

```bash
sudo apt update
sudo apt install openssh-client -y
```


**how to enable ssh server on ubuntu**

```bash
sudo systemctl enable ssh
```
**how to view status of ssh run**

```bash
sudo systemctl status ssh
```
**Once the installation done, use this command to loging to the remote server**

```bash
ssh user@server-ip-here
```

**how do disable the ssh server on ubuntu**

```bash
sudo systemctl stop ssh
sudo systemctl disable ssh
sudo apt-get remove opnessh-server
```
