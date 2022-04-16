## Spring Microservices in Action - Second Edition. Chapter 8

# Introduction
Welcome to Spring Microservices in Action, Chapter 8.  Chapter 8 introduces the concept of a API gateway. API gateways are using to enforce consistent policies and actions on all service calls. With this chapter we are going to introduce Spring Cloud Gateway.

1.  A Spring Cloud Config server that is deployed as Docker container and can manage a services configuration information using a file system/ classpath or GitHub-based repository.
2. A Eureka server running as a Spring-Cloud based service. This service will allow multiple service instances to register with it. Clients that need to call a service will use Eureka to lookup the physical location of the target service.
3. A API Gateway. All of our microservices can be routed through the gateway and have pre, response and post policies enforced on the calls.
4.  A organization service that will manage organization data used within Ostock.
5.  A licensing service that will manage licensing data used within Ostock.
6.  A Postgres SQL database used to hold the data.

## Initial Configuration
1.	Apache Maven (http://maven.apache.org)  All of the code examples in this book have been compiled with Java version 11.
2.	Git Client (http://git-scm.com)
3.  Docker(https://www.docker.com/products/docker-desktop)


## How To Use

To clone and run this application, you'll need [Git](https://git-scm.com), [Maven](https://maven.apache.org/), [Java 11](https://www.oracle.com/technetwork/java/javase/downloads/jdk11-downloads-5066655.html). From your command line:

```bash
# Clone this repository
$ git clone https://github.com/aquariusmaster/microservices

# Go into the repository, by changing to the directory where you have downloaded the 
# chapter 8 source code and select whether you want the initial or final configuration
$ cd microservices

# To build the code examples for Chapter 8 as a docker image, open a command-line 
# window and execute the following command:
$ ./mvnw clean package docker:build

# Now we are going to use docker-compose to start the actual image.  To start the docker image, stay in the directory containing  your chapter 8 source code and  Run the following command: 
$ docker-compose -f docker/docker-compose.yml up -d

# Test the application by visiting 
$ curl http://localhost:8072/organization-service/v1/organization/e6a625cc-718b-48c2-ac76-1dfdff9a531e
$ curl http://localhost:8072/actuator/gateway/routes
```

# The build command

Will execute the [fabric8io/docker-maven-plugin](https://github.com/fabric8io/docker-maven-plugin) defined in the pom.xml file.  

 Running the above command at the root of the project directory will build all of the projects.  If everything builds successfully you should see a message indicating that the build was successful.

# The Run command

This command will run our services using the docker-compose.yml file located in the /docker directory. 

If everything starts correctly you should see a bunch of Spring Boot information fly by on standard out.  At this point all of the services needed for the chapter code examples will be running.

# Database
You can find the database script as well in the docker directory.

### Contributing
Feel free to file an issue if it doesn't work for your code sample. Thanks.
