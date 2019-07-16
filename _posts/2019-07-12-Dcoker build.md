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

* Do not use cache when building the image [--no-cache]  
```
docker build --no-cache --target stage1 -t harbor.sonicwall.cn:4433/captureatp-taf/taf:$(VERSION) .
```
使用了--no-cache,再build的时候，每一层的镜像ID会不同

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
* Run a command in a new container    
* -d Run container in background and print container ID.  
* -p 指定端口映射，格式为：宿主端口：容器端口  
* --name="nginx-lb"： 为容器指定一个名字  
```
 docker run -d -p 80:80 --name webserver 6502b237ddd1

```
If you visit via host ip like:http://10.103.64.133:80, It will display:  
[NGINX Server](http://10.103.64.133/)  
