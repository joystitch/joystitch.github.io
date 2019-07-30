---
title: How to access remote docker
layout: post
---
1. cd /lib/systemd/system

2. Edit docker.service

3. Modify the file:
```
   #ExecStart=/usr/bin/dockerd -H fd:// --iptables=false
ExecStart=/usr/bin/dockerd -H tcp://0.0.0.0:2375 -H unix:///var/run/docker.sock
```   

4. Restart the service  
```
systemctl daemon-reload && systemctl restart docker.service
```

5. Use a server to access

```
sudo docker -H 10.103.64.204 ps
```