---
title: Writing a docker compose file
layout: post
tags: docker
categories: docker
---
Compose is a tool for defining and running multi-container Docker applications. With a YAML file to configure your application's service. Then, with a single command, you create and strat all the services from your configution.    
**-- FROM https://docs.docker.com/compose/**

* Using Compose is basically a three-step process:

1.  Define you app's environment with a ```Dockerfile```, So it can be reproduced anywhere.
2.  Define the service that make up yout app in ```docker-compose.yml``` So they can be run together in an isolated environment.
3. Run ```docker-compose up``` and Compose strats and run your entire app.

```bash
version: '3.6'
services:
  test-dev:
    image: harbor.***.com:4433/*/*:latest
    deploy:
      restart_policy:
          condition: on-failure
      placement:
          constraints: [node.role == manager]
      resources:
        limit:
          cpus: "2"
          memory: 4G
    network:
      - ol0
    volumes:
      - /opt/test/test:/opt/test
      - /opt/test/data/test_data:/opt/test_bck
      - /opt/test/filesets:/opt/filesets
      - /opt/test/test_internal:/opt/test_internal
      - /opt/test/samples:/opt/samples
    command:  env FLASK_APP=cheetah flask run
    
networks:
  ol0:
    external: true
    name: ol0
```

* deploy:  
Specify configuration related to the deployment and running of services.This 
only takes effect when deploying to a swarm with docker stack deploy.  
1. ```restart_policy```: configures if and how to restart containers when they exit.  
    _on-failure_: restart the container when it exit unnormally,(status code is not 0)  
2. ```placement```: Specify placement of constraints and preferences.  
    _constraints_: you can limit the set of nodes where a task can be scheduled
     by defining constraint expressions.
3. ```resource```: configures resource constraints
    ```test_dev``` is constrained to use no more than 4G memory and 2 CPU.