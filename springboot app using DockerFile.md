# deployment_portability-microservices

<h2>🛠️ Running Spring boot app using Dockerfile</h2>

<p>1. Create build of the microservice as jar</p>

```
mvn clean install 
```

<p>2. Create Dockerfile at the app directory add commands</p>

```
#Start with a base image containing Java runtime
FROM openjdk:17-jdk-slim

#Information around who maintains the image
MAINTAINER eazybytes.com

# Add the application's jar to the image
COPY target/accounts-0.0.1-SNAPSHOT.jar accounts-0.0.1-SNAPSHOT.jar

# execute the application
ENTRYPOINT ["java", "-jar", "accounts-0.0.1-SNAPSHOT.jar"]
```
<p>3. Execute docker command from the location where docker file is present, to create the image of the jar</p>

```
docker build .-t <account-name>/<image-name> 
```

<p>4. Execute docker command, to start a container with the image created on previous step</p>

```
docker run -d -p 8080:8080 <image-name>
```
