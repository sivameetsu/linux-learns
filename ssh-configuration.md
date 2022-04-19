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


HOW TO ENABLE SSH SERVER ON UBUNTU 
# sudo systemctl enable ssh

HOW TO VIEW STATUS OF SSH RUN
# sudo systemctl status ssh

Once the installation done, use this command to loging to the remote server 
# ssh user@server-ip-here

HOW DO DISABLE THE SSH SERVER ON UBUNTU 
# sudo systemctl stop ssh
# sudo systemctl disable ssh
# sudo apt-get remove opnessh-server
