# Docker Compose with Multiple Local Containers

Compose is a tool for defining and running multi-container Docker applications. With Compose, you use a YAML file to configure your application’s services. Then, with a single command, you create and start all the services from your configuration.

[Documentations](https://docs.docker.com/compose/)

[Back to contents](/README.md)

### 1) Creating and using docker-compose.yml

```docker-compose
version: '3'

services:
    redis-server:
        image: 'redis'
    node-app:
        build: .
        ports:
            - "4001:8081"
```

[Back to contents](/README.md)
