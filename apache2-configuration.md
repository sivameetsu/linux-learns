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

![image](https://user-images.githubusercontent.com/98270930/164885373-486c6d82-e358-4dba-8f86-d71c8d00a45d.png)





