---
title: Writing a Dockerfile
layout: post
categories: ''
tags: ''
---
Writing a Dockerfile is a more consistent and repeatable way to build your images.
```
FROM ubuntu:latest
MAINTAINER  Joy Xu
```
<u>FROM</u> command sets the base image for the rest of the instruction.  
<u>MAINTAINER</u> command tell who is the author of the generated images.  
In the /images folder:
```
$ docker build -t myimage:latest .

```
* -t is the Docker image tag, you can give a name to your image and a tag.
* The second parameter (.) sepecifies the location of the Dockerfile that we created. Since we created the Dockerfile in the same folder in which we are running the docker build, we specified the current dicrectory "." .  

<u>CMD</u> takes various forms and when it is used individually in the file without the ENTRYPOINT command, it take the following format:  
```
CMD ["executable","param1","param2"]
CMD ["date"]

ubuntu16@ubuntu16-virtual-machine:~/images$ docker run -it dc40747ac12e
Mon Jul 15 09:41:01 UTC 2019

```
<u>ENTRYPOINT</u> is used to specify the default app that you want to run. The CMD will then provide only the list of parameters to that ENTRYPOINT application.

```
FROM ubuntu:14.04
MAINTAINER Joy Xu
ENTRYPOINT  ["/bin/cat"]
CMD  ["/etc/passwd"]

ubuntu16@ubuntu16-virtual-machine:~/images$ docker run -it 42e7e81b52c9
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin
bin:x:2:2:bin:/bin:/usr/sbin/nologin
sys:x:3:3:sys:/dev:/usr/sbin/nologin
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/usr/sbin/nologin
man:x:6:12:man:/var/cache/man:/usr/sbin/nologin
lp:x:7:7:lp:/var/spool/lpd:/usr/sbin/nologin
mail:x:8:8:mail:/var/mail:/usr/sbin/nologin
news:x:9:9:news:/var/spool/news:/usr/sbin/nologin
uucp:x:10:10:uucp:/var/spool/uucp:/usr/sbin/nologin
proxy:x:13:13:proxy:/bin:/usr/sbin/nologin
www-data:x:33:33:www-data:/var/www:/usr/sbin/nologin
backup:x:34:34:backup:/var/backups:/usr/sbin/nologin
list:x:38:38:Mailing List Manager:/var/list:/usr/sbin/nologin
irc:x:39:39:ircd:/var/run/ircd:/usr/sbin/nologin
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/usr/sbin/nologin
nobody:x:65534:65534:nobody:/nonexistent:/usr/sbin/nologin
libuuid:x:100:101::/var/lib/libuuid:
syslog:x:101:104::/home/syslog:/bin/false

```
<u>RUN</u> instruction is used to execute any commands.  
```
FROM ubuntu:14.04
MAINTAINER Joy Xu
RUN apt-get update
RUN apt-get install -y nginx
ENTRYPOINT ["/usr/sbin/nginx","-g","daemon off;"]
EXPOSE 80

```

