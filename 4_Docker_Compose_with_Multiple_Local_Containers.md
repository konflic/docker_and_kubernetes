# Docker Compose with Multiple Local Containers

[Back to contents](/README.md)

Compose is a tool for defining and running multi-container Docker applications. With Compose, you use a YAML file to configure your application’s services. Then, with a single command, you create and start all the services from your configuration.

[Documentations on docker-compose](https://docs.docker.com/compose/)

### 1) Creating and using docker-compose.yml

```yml
version: '3'

services:
    redis-server:
        image: 'redis'
    node-app:
        build: .
        ports:
            - "4001:8081"
```

This docker-compose.yml file specifies that we want to run two services. One is made of a *redis* image and another should be build of the Dockerfile found inside the same directory. Also we bind ports from container 8081 to local 4001  

To build and run this compose file use:

```docker-compose up```

[Back to contents](/README.md)
