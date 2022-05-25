Docker-custom-images
Docker image details

purpose	details
operating system	centos:7
Document Root	/var/www/html/index.html
Port	80
httpd custom image build

FROM centos:7
RUN yum install httpd -y
COPY index.html /var/www/html/index.html
CMD ["/usr/sbin/httpd", "-D", "FOREGROUND"]
Build the httpd custom image

docker build -t (tagname) .
docker run commands

docker run -d -p (localhost_port):(container_port) --name (containername) (imagename)
ex:
docker run -d -p 9990:80 --name httpd-container-v1.1 httpd:v1.1
Output image
