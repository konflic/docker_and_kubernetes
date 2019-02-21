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

To run this compose file use:

```
docker-compose up
```

If you have made changes in configuration or files you'll need to *rebuild* and run this compose file use:

```
docker-compose up --build
```

If you want to run container in background use:

```
docker-compose up -d
```

In oeder to stop all containers use:

```
docker-compose down
```

### 2) Restart policy for containers

```yml
version: '3'

services:
    redis-server:
        image: 'redis'
    node-app:
        restart: always
        build: .
        ports:
            - "4001:8081"
```

Another options for restart are:

```
restart: "no"
restart: always
restart: on-failure
restart: unless-stopped
```

### 3) Monitor changes on the fly

If we need to monitor the changes of files on the fly, we should use:

```
docker run -p 3000:3000 -v /app/node_modules -v $(pwd):/app/ <container-id>
```

Here the node_modules folder does not exist in the source folders, without it there will be an error as the node_modules folder will be overwritten by mapping ```-v $(pwd):/app/```

### 4) Wrapping react app project in docker-compose.yml

```yml
version: '3'
services:
  web: # the name of the container
    build:
      context: . # the root directory is the same as docker-compose location
      dockerfile: Dockerfile.dev # Dockerfile with custom name
    ports:
      - "3000:3000" # link the ports of the container
    volumes: 
      - /app/node_modules # just use the node_modules and do not track its cahnges
      - .:/app # link files in the root folder to the files in the /app folder
```

The Dockerfile.dev is the following:

```Dockerfile
FROM node:alpine

WORKDIR '/app'

COPY package.json .
RUN npm install

COPY . . # we actually don't need this as we link files, but it is better to use this line if well deply it to the production environment for example, just not to forget it.

CMD ["npm", "run", "start"]
```

### 5) How to execute sests

Easy: ```docker run -it 296c9c15bd38 npm run test```, but this does not allow us to update tests automatically.

The second way is to:
1) run ```docker-compose up```
2) find the container id with ```docker ps```
3) use in separate terminal ```sudo exec -it <container-id> npm run test```

[Back to contents](/README.md)
