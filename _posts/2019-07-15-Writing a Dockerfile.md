---
title: Writing a Dockerfile
layout: post
categories: ''
tags: ''
---
Writing a Dockerfile is a more consistent and repeatable way to build your images.

    FROM ubuntu:latest
    MAINTAINER  Joy Xu

  
<u>FROM</u> command sets the base image for the rest of the instruction.  
<u>MAINTAINER</u> command tell who is the author of the generated images.  
In the /images folder:
```
    $ docker build -t myimage:latest .
```
* -t is the Docker image tag, you can give a name to your image and a tag.
* The second parameter (.) sepecifies the location of the Dockerfile that we created. Since we created the Dockerfile in the same folder in which we are running the docker build, we specified the current dicrectory "." .  
```
    $ docker build -t myimage:latest .
```

<u>CMD</u> takes various forms and when it is used individually in the file without the ENTRYPOINT command, it take the following format:  
```
CMD ["executable","param1","param2"]
CMD ["date"]

ubuntu16@ubuntu16-virtual-machine:~/images$ docker run -it dc40747ac12e
Mon Jul 15 09:41:01 UTC 2019

```
<u>ENTRYPOINT</u> is used to specify the default app that you want to run. The CMD will then provide only the list of parameters to that ENTRYPOINT application.