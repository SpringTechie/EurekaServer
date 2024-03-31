Create two Springboot application and add following dependancies.
In Client Application.
<dependency>
    <groupId>org.springframework.cloud</groupId>
    <artifactId>spring-cloud-starter-netflix-eureka-client</artifactId>
    <version>4.1.1</version>
</dependency>
In  Server application
<dependency>
    <groupId>org.springframework.cloud</groupId>
    <artifactId>spring-cloud-starter-netflix-eureka-server</artifactId>
    <version>4.1.1</version>
</dependency>

Add these configurations In server application.
spring.application.name=EurekaServerApplication
eureka.client.registerWithEureka = false
eureka.client.fetchRegistry = false
server.port = 8761

Add these configurations In client application.
spring.application.name=EurekaClientApplication
eureka.client.registerWithEureka = true
eureka.client.fetchRegistry = true
eureka.client.service-url.defaultZone: http://localhost:8761/eureka/

Now create another instance of Client application and run it by using below command

Now go to application folder and run this command,it will create the jar file of appliaction under the target folder: 
mvn clean package
Now run the appliaction using this command on diffrent port.
java -jar -Dserver.port=8081 EurekaClientApplication-0.0.1-SNAPSHOT.jar
