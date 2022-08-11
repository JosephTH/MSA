## MSA Components

### Clients

- Web App
- Mobile App
- Chatbot

### Container Host

- docker
- API Gateway
  - Clients <-> API Gateway <-> Microservices
- Authentication Service
  - Provides access token for microservice
- Event Bus
  - Microservices <-> Event Bus

## Microservices as RESTful APIs

> is based on an architectural style known as REST

### Why RESTful APIs

- Simplicity: It is easy to understand since HTTP verbs are based on CRUD
- It is designed to be stateless and separates the concerns of the client and the server
- REST reads can be cached for better performance and scalability
- It supports many data formats

## API Gateway

<img src="https://docs.microsoft.com/ko-kr/azure/architecture/microservices/images/gateway.png" width="70%">

### Why API Gayeway

**Having to keep track of multiple microservice endpoints complicates client integration  
especially when microservices are moved.**

- Client could make the same request without having to know that services were moved or upgraded
- It provides load balancing and failure detection
- Services don't have to handle their own security concerns, including SSL termination and authentication

## Event Bus

## CQRS

Command <-> Query  
Read > Write  
Tables are different between command and query  

## Event Sourcing  

## Saga Pattern  

distributed transaction  
ACID  

### saga

#### Choreography-Based Saga

#### Orchestration-Based Saga

## Success Factors

### Logging

- Exceptions
- All requests and responses that are made to a microservice including the HTTP code
- Microservice response times
- Events that are published to the event bus
- All login / access token (JWT) requests that are made by client applications

### Monitoring & Alerting

- Uptime of microservices
- The average response time of each microservice
- Resource consumption of each microservice
- The success/failure ratio of each microservice
- Access frequency of clients requests
- Infrastructure dependencies

### Documentation

- API Documentation
  - Expected JSON request and response schemas
  - Catalog
- Design Documentation
  - Deployment view of the architecture
  - Activity diagram to illustrate the business logic of each service
- Dependencies
  - For scalability
  - ....
- Network and port allocations

## Frameworks

1. Spring Boot
2. .Net Core(ASP.NET Core)
3. Grails
4. Eclipse Vert.x
5. Helidon
6. FSL (Fresh Squeezed Limonade)
7. Moleculer

## Container Technologies

1. Docker
2. CoreOS' rkt
3. LXC Linux Containers
4. OpenVZ
5. containerd

## Orchestration Engines

1. Kubernetes
2. Docker Swarm
3. OpenShift
4. Cloud Foundry's Diego
5. CoreOS Fleet
6. Mesosphere Marathon
7. Amazon ECS
8. Azure Kubernetes Service

## Service Discovery

1. Consul
2. Apache Zookeeper
3. Etcd
4. Eureka
5. SmartStack
6. SkyDNS
7. Vyne
8. Bajer Street

## API Gateways

1. Kong
2. Ambassador
3. Ocelot
4. Tyk
5. Amazon AWS API Gateway
6. Azure Application Gateway
7. Spring Cloud Gateway
8. KrakenD

## Event Bus Tools & Technologies

1. Apache Kafka
2. RabbitMQ
3. Azure Service Bus
4. Amazon Simple Queue Service (SQS)
5. Google Cloud Pub/Sub

## Logging Tools

1. Fluentd
2. Graylog
3. Kibana
4. Logstash
5. Bunyan
6. Suro

## Monitoring Tools

1. Grafana
2. Prometheus
3. cAdvisor
4. Riemann
5. Spigo
6. Sensu
7. Sysdig Monitor

## Documentation Tools

1. Swagger UI
2. Apiary
3. Readme.io
4. Slate
5. Gelato
6. Aglio
7. LucyBot's DocGen

## Testing Tools

1. Postman
2. Hoverfly
3. Pact
4. Gatling
5. REST-Assured
6. Citrus Framework

## Converting a Monolithic Application Into Microservices

## Recommandations
- Building Microservices by Sam Newman
- ...