
# TUI Backend Technical Test 

## Overview
This application, built on the Spring framework, facilitates the management of pilot orders via a REST API.

## Functionalities
The system supports the following operations:
- Registration of a client user.
- Placement of a pilot order.
- Modification of a pilot order.
- User login using credentials.
- Retrieval of orders based on customer information.

# Utilizing the API
### Documentation
You can access the Swagger API documentation by default at [http://localhost:8080/swagger-ui/index.html](http://localhost:8080/swagger-ui/index.html)

The H2 console is accessible at [http://localhost:8080/h2-console/](http://localhost:8080/h2-console/)

### Considerations
Upon user creation, a client identifier is generated.

To place an order, provide your client identifier.

Upon order creation, an order identifier is provided.

To update an order, the order identifier is required.

The search operation is secured using a JWT Bearer Token.

Be sure to create a user and log in to obtain your token.

When using Swagger, input the token via the "Authorize" button.

For direct server requests, include the token in the header `Authorization: Bearer {token}`

### Sample cURL Command

Execute a cURL POST request to create an order for a client with identifier 1:

bash
curl "localhost:8080/api/order" -H 'Content-Type: application/json' -X POST -d '{"client":{"clientId":1}, "deliveryAddress":{"street":"Via mimose","postcode":"80145","city":"Roma","country":"Italy"}, "pilotes":15}'
Project Details
The project has undergone testing with both JDK 8 and JDK 11.

It is a Spring Boot application employing Apache Maven.

Swagger API documentation is integrated into the project.

Development took place using "IntelliJ IDEA Community" IDE.

The project utilizes an H2 in-memory database and employs the Hibernate dialect to define database relationships.

The codebase includes tests at all levels, achieving a coverage exceeding 80%.

A Dockerfile is provided for containerization.

Lombok is employed in the project.

### Commands

### Docker for Local Development:

cd backend-technical-test-v2-master

mvn clean package

docker build --tag=pilotes-server:latest .

docker run -p8887:8888 pilotes-server:latest

### Maven

mvn clean test

mvn spring-boot:run