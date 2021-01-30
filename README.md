# Docker_Spring_Demo
A docker containerised spring boot application 

Reference  [Spring Boot Docs][1] .

[1]: https://spring.io/guides/gs/spring-boot-docker/ "Spring boot docs"


##Steps
* Create a sample Spring Boot Application using ide like intellij
* Run it locally and check every if everything is fine
* Now build it using following command
```
 sudo ./mvnw package && java -jar target/gs-spring-boot-docker-0.1.0.jar  
```
* if you are getting error 
```
Error: Unable to access jarfile target/gs-spring-boot-docker-0.1.0.jar
```
go to target folder(cd /target) and Run 
``` java -jar docker_demo-0.0.1-SNAPSHOT.jar ```

your application will run

### Now time to Dockerize

* create a file name Dockerfile in your project folder(where pom.xml) and write following command
``` 
FROM openjdk:8-jdk-alpine
ARG JAR_FILE=target/*.jar
COPY ${JAR_FILE} app.jar
ENTRYPOINT ["java","-jar","/app.jar"]
```
* Now Run ``` docker build -t springio/gs-spring-boot-docker . ```

* check if your image created by  ``` docker images ```
* Run your image by ``` docker run -p 8080:8080 springio/gs-spring-boot-docker ```
* Your docker image is running :)


P.S - Markdown cheat code https://wordpress.com/support/markdown-quick-reference/


 
