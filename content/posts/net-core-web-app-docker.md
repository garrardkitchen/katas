---
title: ".NET Core and Kubernetes"
date: 2020-04-27T16:30:11+01:00
tags: [.net core, redis, docker, kubernetes, kubectl, minikube, deployment, pod]
---

_Create a Redis Caching layer for above [net-core-web-app](posts/net-core-web-app).NET Core random name web application.  Have a TTL of 10 seconds.  Host in Docker container.  Create an Kubernetes deployment manifest. Refs: [deployment example](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/)_

**Requirements**:

1. Complete [net-core-web-app](posts/net-core-web-app)

2. Install Kubectl

3. Install Minikube to work with hyper-v driver

4. Set the docker environment to point the MiniKube local Kubernetes cluster

5. TBC

**Tech**:

- .NET Core 3.1
- Redis
- Docker
- Kubernetes
- Kubectl
- MiniKube

**References**

- [random name generator API](http://names.drycodes.com/10?combine=4)

**Hint 1**

- Use the [kubernetes-on-windows](http://blog.garrardkitchen.com/posts/kubernetes-on-windows/) post to help install and configure a local Kubernetes cluster

