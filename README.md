[![integration](https://github.com/to4kin/webapp/actions/workflows/integration.yml/badge.svg?branch=master)](https://github.com/to4kin/webapp/actions/workflows/integration.yml)
[![GitHub release](https://img.shields.io/github/release/to4kin/webapp.svg)](https://GitHub.com/to4kin/webapp/releases/)

# WebApp

Service accept file by curl command or via simple UI and store it on disk.

[![GitHub](https://badgen.net/badge/icon/github?icon=github&label)](https://github.com/to4kin/webapp)  
[![Docker](https://badgen.net/badge/icon/docker?icon=docker&label)](https://hub.docker.com/repository/docker/to4kin/webapp)

## Precondition

* Java 11 (Zulu)

### Usage with Docker

Default locations for uploads is `/app/upload`

```bash
docker run -it --rm -p 8000:8000 -v `pwd`/upload:/app/upload --name webapp to4kin/webapp:latest
```

### Usage

```bash
java -jar build/libs/webapp-<APP_VERSION>.jar
```

### Config file

```properties
server.port=8000

spring.servlet.multipart.max-file-size=10MB
spring.servlet.multipart.max-request-size=10MB

storage.uploadFolder=upload
```
