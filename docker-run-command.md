#### docker-run-command.md
---

To pull images to dockerhub use this command

```bash
docker pull imagename
```

To check install images use this
```bash
docker images
```
lists all the docker containers
```bash
docker ps 
docker ps -a
```

to check version
```bash
docker --version
```

To run the container
```bash
docker run -it -d imagename
```

To enter inside the containes use this
```bash
docker exec -it containerID bash
```
