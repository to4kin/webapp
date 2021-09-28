[![ci-build](https://github.com/to4kin/webapp/actions/workflows/ci-build.yml/badge.svg?branch=master)](https://github.com/to4kin/webapp/actions/workflows/ci-build.yml)
[![GitHub release](https://img.shields.io/github/release/to4kin/webapp.svg)](https://GitHub.com/to4kin/webapp/releases/)

# WebApp

Service accept file by curl command or via simple UI and store it on disk.

[![GitHub](https://badgen.net/badge/icon/github?icon=github&label)](https://github.com/to4kin/webapp)  
[![Docker](https://badgen.net/badge/icon/docker?icon=docker&label)](https://hub.docker.com/repository/docker/to4kin/webapp)

## Precondition

* Java 11 (Zulu)

### Start via Docker

Default locations for uploads is `/app/upload`

```bash
docker run -it --rm -p 8000:8000 -v `pwd`/upload:/app/upload --name webapp to4kin/webapp:latest
```

### Start via Docker-compose

Example stack.yml for webapp:

```yaml
version: '3.8'

services:

  webapp:
    image: to4kin/webapp:latest
    restart: always
    ports:
      - 8000:8000
    volumes:
      - upload-volume:/app/upload

  webapp-sidecar:
    image: to4kin/webapp-sidecar:latest
    restart: always
    ports:
      - 3000:3000
    volumes:
      - upload-volume:/upload

volumes:
  upload-volume:
```

### Start via java -jar

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
