# API Gateway Microservice
## Overview
### The API Gateway Microservice is built using Spring Cloud Gateway to manage and route API requests efficiently. It provides features like request routing, global filtering, and header manipulation. This service acts as a single entry point for clients and forwards requests to appropriate microservices.

## Features

    -> Dynamic Routing: Routes requests to the corresponding microservices.
    -> Request Modification: Adds headers and parameters to requests.
    -> Path Rewriting: Supports URL rewriting for better API organization.
    -> Global Logging: Logs incoming requests for better traceability.
    -> Load Balancing: Uses service discovery to balance requests across multiple instances.

## API Gateway Routes

    The ApiGatewayConfiguration.java defines various API routes:

    Path                            Destination                 Features

    /get                            http://httpbin.org:80       Adds a custom header and parameter

    /currency-exchange/**           lb://currency-exchange      Routes to the Currency Exchange Service

    /currency-conversion/**         lb://currency-conversion    Routes to the Currency Conversion Service

    /currency-conversion-feign/**   lb://currency-conversion    Uses Feign Client for communication

    /currency-conversion-new/**     lb://currency-conversion    Rewrites URL paths dynamically

## Global Filters

    -> Logging Filter (LoggingFilter.java): Logs all incoming requests and their paths.

    -> Security & Authentication Filters (Future Scope): Can be added here.

## Configuration (application.properties)

    -> Ensure the service discovery and load balancing work by configuring Eureka Server:
    spring.application.name=api-gateway
    server.port=8765

    -> Enable Service Discovery
    eureka.client.service-url.defaultZone=http://localhost:8761/eureka/

## Eureka Server in Spring Boot

    -> Eureka Server is a core component of Spring Cloud Netflix that provides service discovery functionality for microservices. 
    -> It allows services to register themselves and discover other services dynamically.

### 🚀 Features

    -> Service Discovery: Automatically registers and locates services.
    -> Load Balancing: Works with Ribbon for distributing requests.
    -> Fault Tolerance: Ensures high availability of services.
    -> Scalability: Supports dynamic scaling of microservices.
    -> Note: The default port for Eureka Server is 8761.
    -> Once the server is up, you can access the Eureka Dashboard at:
    🔗 http://localhost:8761/
