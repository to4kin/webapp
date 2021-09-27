[![integration](https://github.com/to4kin/webapp/actions/workflows/integration.yml/badge.svg?branch=master)](https://github.com/to4kin/webapp/actions/workflows/integration.yml)

# WebApp

Service accept file by curl command or via simple UI and store it on disk.

[Docker Hub](https://github.com/to4kin/webapp)

## Precondition

* Java 11 (Zulu)

### Usage Java

```bash
java -jar build/libs/webapp-<APP_VERSION>.jar
```

### Usage Docker

Default locations for uploads is `/app/upload`

```bash
docker run -it --rm -p 8000:8000 -v `pwd`/upload:/app/upload --name webapp to4kin/webapp:latest
```

### Config file

```properties
server.port=8000

spring.servlet.multipart.max-file-size=10MB
spring.servlet.multipart.max-request-size=10MB

storage.uploadFolder=upload
```
