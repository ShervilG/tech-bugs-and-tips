#docker #docker-basics #basics 
***
### Docker Pull
1. Start the docker engine.
2. Docker Pull (by default pulls from docker hub if we don't specify a registry).
***
### Docker Images
Gives a list of docker images in ur local machine.
***
### Start Local Terminal Session of a Container Image
```
docker run -i -t <base-image-name> /bin/bash
```
***
### Docker Commit
Sometimes after installing dependencies in container, we can commit a snapshot of it.
- First check the docker container history
```
docker ps -a
```
- Choose the container Id and do a commit
```
docker commit <container-id> <new-name-of-image>
```
