### Docker-custom-images
---

**_httpd custom image build_**

```bash
FROM centos:7
RUN yum install httpd -y
COPY index.html /var/www/html/index.html
CMD ["/usr/sbin/httpd", "-D", "FOREGROUND"]
```
**_Build the httpd custom image_**
```bash
docker build -t (tagname) .
```
**Docker image details**
|purpose|details|
|---|---|
|operating system| centos:7 |
|Document Root|/var/www/html/index.html|
|Port| 80 |

**_docker run commands_**

```bash
docker run -d -p (localhost_port):(container_port) --name (containername) (imagename)
ex:
docker run -d -p 9990:80 --name httpd-container-v1.1 httpd:v1.1
```
**Output**
![image](https://user-images.githubusercontent.com/91359308/169489103-86482fc6-4e30-41c8-b2f3-ca1e9a89740f.png)
