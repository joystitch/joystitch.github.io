---
title: How to build a docker image by using Dockerfile
layout: post
categories: Docker
tags: docker
---
## docker build

`docker build [option] PATH | URL | -`  
 

### Specify target build stage[--target]  
When building a Dockerfile with multiple build stages, --target can be used to specify an intermediate build stage by name as a final stage for the resulting image.Commadn after the target stage will be skipped.

    FROM debian AS build-env
    ...
    FROM alpine AS production-env  
    ...
    

    $ docker build --target build-env

### --tag, -t
Name and optionally a tag in the 'name:tag' format

    sudo docker build --target stage2 -t harbor.sonicwall.cn:4433/captureatp-taf/taf:${Version} .