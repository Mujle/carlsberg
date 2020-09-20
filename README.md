# A quick introduction to the project
This is a project that mimicks a Carlsberg warehouse server written with a
microservice architecture pattern. The server itself started out as a playground during
quarantine and ended as a means for learning Spring Cloud, Spring Security, JWT etc.
That being said, I am aware that most of the technologies used were somewhat
„forced“ into the project.

# Project structure
Back-end was divided into five independant services with a structure of:
![alt text](https://i.imgur.com/UCGX32B.png)

## api-gateway-service
Used as a gateway to all the other services. I implemented Spring Security into this
service with JWT protection. Client load balancing is also done using api-gateway-
service.
After all the services have been started you can check out rest call documentation on:
http://localhost:8024/swagger-ui/

Github repository link: [api-gateway-service](https://github.com/Mujle/api-gateway-service)

## discovery-service
Purpose of this service is to list all the available services and their instances so that
api-gateway-service could do its load balancing. It was written using Netflix Eureka.

Github repository link: [discovery-service](https://github.com/Mujle/discovery-service)

## configuration-service
This service is used as a confguration distributor for api-gateway-service, repository-
service and user-service.

Github repository link: [configuration-service](https://github.com/Mujle/configuration-service)

## repository-service
Used for all the repository based rest calls. It is connected to a mysql database
„carlsberg“.
After all the services have been started you can check out rest call documentation on:
http://localhost:8028/swagger-ui/

Github repository link: [repository-service](https://github.com/Mujle/repository-service)


## user-service
Currently has a single usage of returning user info used for JWT verification. All the
user related functionality like „singn up“ or „logn in“ is meant to be written here in
future versions of the service. It is connected to a mysql database „user“.
http://localhost:8025/swagger-ui/

Github repository link: [user-service](https://github.com/Mujle/user-service)

# Database structures

### Carlsberg – used by repository-service

![alt text](https://i.imgur.com/V4OAWjM.png)

### User – used by user-service

![alt text](https://i.imgur.com/SjwoWYk.png)
