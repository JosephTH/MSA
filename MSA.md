# Microservice Architecture

## MSA Components

### Clients

- Web App
- Mobile App
- Chatbot

### Container Host

- docker
- API Gateway
  - Clients <-> API Gateway <-> Microservice
- Authentication Service
  - Provides access token for microservice
- Event Bus
  - Microservice <-> Event Bus

## Microservices as RESTful APIs

> which is based on an architectural style known as REST

### Why RESTful APIs

- **Simplicity**: It is easy to understand since HTTP verbs are based on CRUD
- It is designed to be stateless and separates the concerns of the client and the server
- REST reads can be cached for better performance and scalability
- It supports many data formats

## API Gateway

![API_Gateway](./image/gateway.png)

### Why do we use API Gateway

**Having to keep track of multiple microservice endpoints complicates client integration  
especially when microservices are moved.**

- Client could make the same request without having to know that services were moved or upgraded
- It provides load balancing and failure detection
- Services don't have to handle their own security concerns, including SSL termination and authentication

## Event Bus
![Event_Bus](./image/gateway.png)<sup id="a1">[1](#f1)</sup>



An event bus can be classified as the backbone of a decoupled microservices architecture. It allows microservices to communicate with each other without having to know about each other.  

This type of communication is based on the Publish/Subscribe pattern, which is similar to the Observer Pattern. However, with the Observer Pattern the publisher or observable broadcasts changes directly to its subscribers or observers. Whereas with the Publish/Subscribe pattern, **the Event Bus takes up the role of the middleman and sits between the publisher and subscriber.**  

In this way, microservices that publish events to the event bus, does not have to know what other microservices want to do with the published events, it only need to make sure that it is available on the event bus for consumption.



## CQRS(Command Query Responsibility Segregation)

![cqrs](./image/cqrs.png)<sup id="a2">[2](#f2)</sup>

- **Command**: Operations that alters the state of an object or entity.(Write, CUD)
- **Queries**: Operations that return the state of an object or entity.(Read, R)

### Why do we need CQRS

- Generally, data is more frequently queried than altered.
- Separating commands and queries allows us to iptimise each for high performance.
- Executing command and query operations on the same model could cause data contention.

## Event Sourcing  

**Event Sourcing** defines an approach where all the changes that are made to an object or entity, are stored as **a sequence of immutable events to an event store**, as opposed to storing just the current state.

- The event store provides a complete log of every state change, effectively creating an audit trail of the entire system
- The state of any object can be recreated by replaying the event store

## Saga Pattern  

- The Saga Pattern is a design pattern that provides a solution for implementing transactions in the form of sagas that span across two or more microserivces. It is a way to manage data consistency across microservices in distributed transaction scenarios.
- A saga is a sequence of transactions that updates each service and publishes a message or event to trigger the next transaction step. If a step fails, the saga executes compensating transactions that counteract the preceding transactions.

![saga](./image/saga.png)<sup id="a3">[3](#f3)</sup>

### Choreography-Based Saga

![saga_choreography](image/saga_choreography.png)<sup id="a4">[4](#f4)</sup>

### Orchestration-Based Saga

- A single orchestrator (arranger) manages all the transactions and directs services to execute local transactions.

![saga_orchestrator](image/saga_orchestrator.png)<sup id="a5">[5](#f5)</sup>
ACID  

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

## References

<b id="f1">1</b> [microsoft_gateway](https://docs.microsoft.com/ko-kr/azure/architecture/microservices/design/gateway) [↩](#a1)  
<b id="f2">2</b> [modernization-data-persistence/cqrs-pattern.html](https://docs.aws.amazon.com/ko_kr/prescriptive-guidance/latest/modernization-data-persistence/cqrs-pattern.html)  [↩](#a2)  
<b id="f3">3</b> [azure_saga](https://docs.microsoft.com/en-us/azure/architecture/reference-architectures/saga/saga) [↩](#a3)  
<b id="f4">4</b> Microservices Patterns with Examples in Java [↩](#a4)  
<b id="f5">5</b> Microservices Patterns with Examples in Java [↩](#a5)