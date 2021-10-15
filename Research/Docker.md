## Create and deploy docker


Create docker file 
```
FROM openjdk:11
EXPOSE <PORT>
ADD target/<PROJECT_NAME>.jar <PROJECT_NAME>.jar
ENTRYPOINT ["java", "-jar", "/<PROJECT_NAME>"]
```



1. create a "Dockerfile" with special commands to build your docker from your project
2. make sure for java applications there is a jar file from your project and rename it to projectname.jar if this is not the case use ```mvn package``` to add it (dont forget to rename it!
3. run ```Docker build -t username/your-project-name . ```
4. ```docker tag username/your-project-name username/your-project-name```
5. ```docker push username/your-project-name```

this will create a repo on dockerhub from there you can clone it to a server. it may be required to login ```docker login``` will work if you're logged in on docker desktop





for creating a executable jar build from your application automatically you have to adjust your docker file: tutorial https://octopus.com/blog/java-ci-cd-co/from-jar-to-docker


current working dockerfile mvn spring java format is not working

```FROM maven:3.8.3-jdk-11 AS build-env

WORKDIR /app

COPY pom.xml ./
RUN mvn dependency:go-offline

#RUN mvn spring-javaformat:help
#RUN ./mvnw spring-javaformat:help

COPY . ./

#RUN mvn spring-javaformat:apply
#RUN ./mvnw spring-javaformat:apply
RUN mvn package -DfinalName=devices-service

FROM openjdk:11

EXPOSE 9090

WORKDIR /app

COPY --from=build-env /app/target/devices-service-0.0.1-SNAPSHOT.jar ./devices-service-0.0.1-SNAPSHOT.jar
CMD ["/usr/bin/java", "-jar", "/app/devices-service-0.0.1-SNAPSHOT.jar"]
```




## Troubleshoot

stop Docker Desktop
stop WSL (wsl --shutdown)
unregister the docker-desktop distro (which contains binaries, but no data) with wsl --unregister docker-desktop
restart Docker Desktop
