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

    $ docker build -t myimage:latest .

* -t is the Docker image tag, you can give a name to your image and a tag.
* The second parameter (.) sepecifies the location of the Dockerfile that we created. Since we created the Dockerfile in the same filder in which we are running the docker build, we specified the current dicrectory "." .

    $ docker build -t myimage:latest .

