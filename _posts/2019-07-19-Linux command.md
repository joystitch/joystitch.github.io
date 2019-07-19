---
title: Linux command
layout: post
tags: linux
categories: linux
---
### sudo

* sudo -S,  --stdin  read password from standard input.  
```
echo 'password' | sudo -S /opt/sync/sync_jenkins.sh  
echo 'build' | sudo -S docker exec -i taf-dev taf run -t [DEV-7]
```

* sudo -s, --shell  run shell as the target; a command may also be specified.