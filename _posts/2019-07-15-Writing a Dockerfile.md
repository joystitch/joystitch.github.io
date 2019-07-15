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

    

    ubuntu16@ubuntu16-virtual-machine:~/images$ docker build -t myimage:latest .

    Sending build context to Docker daemon  2.048kB
    Step 1/2 : FROM ubuntu:14.04
    14.04: Pulling from library/ubuntu
    a7344f52cb74: Pull complete 
    515c9bb51536: Pull complete
    e1eabe0537eb: Pull complete 
    4701f1215c13: Pull complete 
    Digest: sha256:2f7c79927b346e436cc14c92bd4e5bd778c3bd7037f35bc639ac1589a7acfa90
    Status: Downloaded newer image for ubuntu:14.04
    ---> 2c5e00d77a67
    Step 2/2 : MAINTAINER Joy Xu
    ---> Running in 0435988a086f
    Removing intermediate container 0435988a086f
     ---> 4539b6eeaed9
    Successfully built 4539b6eeaed9
    Successfully tagged myimage:latest