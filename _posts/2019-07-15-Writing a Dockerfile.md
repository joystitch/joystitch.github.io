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