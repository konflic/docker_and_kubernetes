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
