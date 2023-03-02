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

### Override Env Variable
```
docker run -e "ARG1=test1" java-params
```
Where DockerFile is:
```
FROM linux/java

ENV ARG1=default
ENV ARG2=default2

WORKDIR /app
COPY . /app

RUN javac DockerTestParams.java
ENTRYPOINT java DockerTestParams ${ARG1} ${ARG2}
```
>**_Note: ARGS should be passed while builder, enviroment variables are passed during running and stay/can change during runtime._**
***
### Exposing Ports
> **_Note: only for documenting_**
- Use the EXPOSE command in Dockerfile (by default it's TCP use /udp after port number for udp)
```
EXPOSE 8080
```
- Use the **–expose** flag at runtime to expose a port
```
docker run --expose=8080 <image-name>
```
### Use -p command and runtime for port mapping
```
docker run -p <host-port>:<container-port> <image-name>
```
