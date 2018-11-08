# Building Custom Images Through Docker Server

This section includes notes from the third module, concernind custom docker images.

[Back to contents](/README.md)

1) Creating and using Dockerfile.

In order to create a container you should:
- Create a Docker file
- Fill it with instructions. For example: 
```Dockerfile
# Use and existing docker image
FROM alpine

# Download and install a dependencies
RUN apk add --update redis

# Tell the image what to do when it starts
# As a container
CMD ["redis-server"]
```
- From the root directory execute
```bash
docker build .
```
- Wait for the building process, and for the **id** of the container
```bash
...
Step 1/3 : FROM alpine
latest: Pulling from library/alpine
...
Step 2/3 : RUN apk add --update redis
...
(1/1) Installing redis (4.0.11-r0)
...
Step 3/3 : CMD ["redis-server"]
...
Successfully built 43c796baca98

```
