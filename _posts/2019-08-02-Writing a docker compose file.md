---
title: Writing a docker compose file
layout: post
tags: docker
categories: docker
---
Compose is a tool for defining and running multi-container Docker applications. With a YAML file to configure your application's service. Then, with a single command, you create and strat all the services from your configution.    
-- FROM https://docs.docker.com/compose/

* Using Compose is basically a three-step process:

1.  Define you app's environment with a ```Dockerfile```, So it can be reproduced anywhere.
2.  Define the service that make up yout app in ```docker-compose.yml``` So they can be run together in an isolated environment.
3. Run ```docker-compose up``` and Compose strats and run your entire app.