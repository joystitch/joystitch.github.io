---
title: Docker command
layout: post
categories: Docker
tags: docker
---
### docker build

* Build an image from a Dockerfile  


    docker build [option] PATH | URL | - 

* Specify target build stage [--target]

When building a Dockerfile with multiple build stages, --target can be used to specify an intermediate build stage by name as a final stage for the resulting image.Commadn after the target stage will be skipped.

    FROM debian AS build-env
    ...
    FROM alpine AS production-env  
    ...
    

    $ docker build --target build-env

* --tag,-t


Name and optionally a tag in the 'name:tag' format

    sudo docker build --target stage2 -t harbor.sonicwall.cn:4433/captureatp-taf/taf:${Version} .

    sudo docker build -t myimage:latest .

### docker tag

* Create a tag TARGET_IMAGE that refers to SOURCE_IMAGE
   
```
$docker tag SOURCE_IMAGE[:TAG] TARGET_IMAGE[:TAG]
```

### docker run
