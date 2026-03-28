# API Gateway

## Run locally

1. Build
   mvn clean package
2. Run
   mvn spring-boot:run

## Endpoints

- Health: http://localhost:7000/actuator/health
- OpenAPI: http://localhost:7000/v3/api-docs

## Notes

- JWT validation is handled by a global filter for non-public routes.
- Config import is optional from Config Server.
- Route definitions can be overridden from config-server/config-repo.