# maven-spring-boot-hibernate
Simple spring boot hibernate project using Dockerize as part of the docker-compose configuration. 

The problem of waiting for a database (for example) to be ready is really just a subset of a much larger problem of distributed systems. In production, your database could become unavailable or move hosts at any time. Your application needs to be resilient to these types of failures.

To handle this, design your application to attempt to re-establish a connection to the database after a failure. If the application retries the connection, it can eventually connect to the database.

The best solution is to perform this check in your application code, both at startup and whenever a connection is lost for any reason. However, if you don’t need this level of resilience, you can work around the problem with a wrapper script:

Dockerize is used to define dependency between containers, in this case, the spring boot app will wait until the mysql service were available.

### links of interest:

* https://github.com/jwilder/dockerize
* http://jasonwilder.com/blog/2014/10/13/a-simple-way-to-dockerize-applications/
* https://docs.docker.com/compose/startup-order/

## Start up with Docker

this approach will allow us to work through a container without the continuous 
build of the image when no new dependencies where added to the pom.xml file. Ap 


in a terminal over **/maven-spring-boot-hibernate**:

    docker build . -t maven-spring-boot-hibernate:latest
    
once build finish, remove risk-manager-backend container if already exists in your local environment.

    docker run --rm -p 8080:8080 maven-spring-boot-hibernate

## start up with docker-compose and Dockerize

in a terminal over **/maven-spring-boot-hibernate**:

    docker-compose up
    
## service health for internal environment purposes

    http://localhost:8080/actuator/health    
