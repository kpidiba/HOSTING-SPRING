# HOSTING ON RENDER.COM

### RESSOURCES

[Render · The Easiest Cloud For All Your Apps](https://dashboard.render.com/create?type=web) 

https://hostingtutorials.dev/blog/free-spring-boot-host-with-render (TOP)

https://javawhizz.com/2023/03/host-a-spring-boot-application-for-free-on-render

### STEPS

- package your application with **Maven** run: `mvn clean package`

- test the jar

```
java -jar target/demo-0.0.1-SNAPSHOT.jar
```

- ## Create a Dockerfile
  
  Create a file 
  named Dockerfile in the project root. Copy and paste the following 
  Docker commands into the file. This will be used to create the Docker 
  image, that we are going to deploy on Render.
  
  Maven:
  
  Dockerfile
  
  ```Dockerfile
  FROM eclipse-temurin:17-jdk-alpine
  VOLUME /tmp
  COPY target/*.jar app.jar
  ENTRYPOINT ["java","-jar","/app.jar"]
  ```

- **BUILDING DOCKER IMAGE** (use vs code docker extension)

```docker
docker build -t demo .
```

- **SEARCH THE IMAGE** 

```docker
docker images
```

- **TAG THE IMAGE**

```docker
docker tag demo YOUR-USER-NAME/testsbapp
```

- **PUSH THE IMAGE** 

```docker
docker push YOUR-USER-NAME/testsbapp
```

- **PUT THE NAME LIKE THIS**

```json
docker.io/kbrightcoder/rest-api:latest
```

## Deploying on Render

Once your image is up on docker hub we'll have to go to our account on Render and enable a setting in our profile called `Early Access -> Deploy from external registries -> Enable`

This will allow us to be able to deploy the public docker image that we uploaded to Docker hub.

After that press on the `New +` button on the top and choose Web Service. We want to choose the `Deploy an existing image from a registry`

### SELECT THE IMAGE

- It' s finish

### RUN AN IMAGE

```ts
docker run -p 8080:8080 spring-boot-render
```

### FREE MYSQL HOSTING

- https://www.freemysqlhosting.net/

- https://db4free.net 

### MYSQL DB4FREE HOSTING TEST

- go to [GitHub - kpidiba/SPRING-BOOT](https://github.com/kpidiba/SPRING-BOOT) 

- branch hosting

- database configuration need: username,password,server name that will replace localhost with his port

- example

```xml
spring.jpa.hibernate.ddl-auto=update
spring.datasource.url=jdbc:mysql://db4free.net:3306/hosting1_1
spring.datasource.username=root123_1
spring.datasource.password=;Q233e;5mZWGSfT
spring.datasource.driver-class-name =com.mysql.cj.jdbc.Driver
spring.jpa.database-platform = org.hibernate.dialect.MySQL5Dialect
spring.jpa.generate-ddl=true
```

### DATABASE CONFIGURATIONS

### SPRING BOOT HOSTING

- DigitalOcean and Hetzner (Spring boot/React/postgre)

- Amazon lightsail (spring boot +Thymeleaf)

- Heroku

- https://www.dailyrazor.com/java-hosting/ 
