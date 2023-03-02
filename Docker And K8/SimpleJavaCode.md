#java-docker #docker-java #java 
***
### Running A Simple Java Program In Docker
- Create a Java Program
```
import java.util.*;

public class DockerTest {
    
    public static void main(String[] args) {
        System.out.println("Hello World !");    
    }
}
```
- Create DOCKERFILE (without .)
```
FROM <your-base-image-having-jdk-installed>

WORKDIR /app
COPY . /app

RUN javac DockerTest.java
ENTRYPOINT [ "java", "DockerTest" ]
```
- Build and run the image
```
docker build -t java-simple .
docker run java-simple
```

```
bash docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' b01d8028b33c
```