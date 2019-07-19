---
title: How to create SSH Username with private key
layout: post
tags: jenkins
categories: jenkins
---
1. Go to Gitlab, User -> Setting -> SSH Keys -> generate ssh keys.(http://10.103.239.81/profile/keys)  

2. Using linux to generate a new SSH key pair.
```
ssh-keygen -t rsa -C "your.email@example.com" -b 4096
```
no passphrase, public key and private key will be saved in ~/.ssh/id_rsa.pub.

3. Copy private key from id_rsa.pub. to Key under SSH Keys page and save.  

4. Go to Jenkins -> Credentials ->Global Credentials -> Add credentials. 
  __Kind__: SSH Username with private key
  __Username__: Gitlab's username
  __Private key__: Copy the private key from linux(~/.ssh/id_rsa) to Key
  __Passphrase__: no passphrase
  __Description__: Give a description to let user easy to recognized.
  Save the configuraion.
  
5. When we create a pipeline, Repository URL should be ssh format:
```
gitlab@10.103.239.81:TAF/cheetah.git
```  
Credentaial: the SSH key created before.