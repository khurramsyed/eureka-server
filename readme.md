# Spring Cloud Eureka Server Example

## How to Run the server 

In order to run applications 

vm parameter -Dspring.profiles.active should be set to 
 primary, secondary or tertiary using:
 
```-Dspring.profiles.active=primary```
 

## Eureaka Settings 

* Using application.yml *

```
---
spring:
 profiles: primary
 application:
  name: eureka-server-clustered
server:
 port: 8010
eureka:
 client:
  serviceUrl:
   defaultZone: http://localhost:8011/eureka/,http://localhost:8012/eureka/

---
spring:
 profiles: secondary
 application:
  name: eureka-server-clustered
server:
  port: 8011
eureka:
 client:
  serviceUrl:
   defaultZone: http://localhost:8012/eureka/,http://localhost:8010/eureka/
---
spring:
  profiles: tertiary
  application:
    name: eureka-server-clustered
server:
  port: 8012
eureka:
 instance:
  client:
   serviceUrl:
    defaultZone: http://localhost:8010/eureka/,http://localhost:8011/eureka/
    
```

## References 

* https://concourse.ci/docker-repository.html - Installing Concourse using Docker-compose
* https://concourse.ci/hello-world.html - Sample Hello World Example
* https://github.com/concourse/concourse
* https://github.com/nitram509/concourse-java-maven-test-prj

