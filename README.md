# springboot-docker-circleci-demo

This is a simple example on how to add Spring Boot application in a Docker image and how to build the Docker image from a docker file using CircleCI's native Docker support and push the Docker image to the Docker Hub.

In this example it's covered not only the build of the Docker image but also how to start the container and how to perform some tests against the container. 

### Spring Boot Application

The Spring Boot Application was generated using the [Spring Initializr](http://start.spring.io/)

### How to create Docker image from Dockerfile

In order to create a Docker image you need to create a Dockerfile. I prefered to create the [Dockerfile](https://github.com/Prates23/springboot-docker-circleci-demo/blob/master/Dockerfile) at project root although [Spring Boot Docker](https://spring.io/guides/gs/spring-boot-docker/) recomends creating the following file structure `src/main/docker/Dockerfile`


```
FROM frolvlad/alpine-oraclejdk8:slim
VOLUME /tmp
ADD target/sbdocker-0.0.1.jar app.jar
RUN sh -c 'touch /app.jar'
ENV JAVA_OPTS=""
ENTRYPOINT [ "sh", "-c", "java $JAVA_OPTS -Djava.security.egd=file:/dev/./urandom -jar /app.jar" ]
```


### How to build and test with Circle CI

First create a [circle.yml](https://github.com/Prates23/springboot-docker-circleci-demo/blob/master/circle.yml) file at project root.

### Pushing to Docker Hub

Create a deployment section


### Additional Information

[CircleCI Docker](https://circleci.com/docs/1.0/docker/)
