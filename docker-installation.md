## Docker installation

**Setup the repository**

```bash
  sudo apt-get update
  sudo apt-get install \
    ca-certificates \
    curl \
    gnupg \
    lsb-release -y
```
**Add Docker’s official GPG key**

```bash
 curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg \
      --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```
**set up the stable repository**

```bash
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

**Install Docker Engine**

```bash
 sudo apt-get update
 sudo apt-get install docker-ce docker-ce-cli containerd.io
```

**Start the Docker**

```bash
sudo systemctl start docker
```

**Stop the Docker**

```bash
sudo systemctl stop docker
```

**Restart the Docker**

```bash
sudo systemctl restart docker
```

**Enable the Docker**
```bash
sudo systemctl enable docker
```
**Add the users into Docker group**

```bash
sudo usermod -aG docker $USER
```
