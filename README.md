# tutorial_docker_n_kubernetes
Tutorial for devs of the TinyAIoT project group.
[TOC]
# Introduction to Docker and Kubernetes
## Target audience: 
This tutorial is for developers who want to gain hands-on experience with Docker and Kubernetes.

## Prerequisites:
* 2 CPUs or more
* 2GB of free memory
* 20GB of free disk space
* Internet connection
Note: This tutorial is an introduction and covers basic concepts. For more information, refer to the official Docker and Kubernetes documentation.
## Installation instructions
* download latest docker desktop version
    * [Mac](https://docs.docker.com/desktop/install/mac-install/)   
    * [Windows](https://docs.docker.com/desktop/install/windows-install/)   


# 1. Docker Basics
## What is Docker?

Docker is a platform for containerizing applications. Containers are lightweight, portable units that include everything an application needs to run.

### Creating a Docker image:

Create a Dockerfile that describes the image configuration.
Run docker build to build the image.
Run the container with docker run.
Example:

### Dockerfile
```python
FROM python:3.9

WORKDIR /app

COPY requirements.txt .

RUN pip install -r requirements.txt

COPY . .

CMD ["python", "app.py"]
```
### Build the image
`docker build -t my-app .`

### Run the container
`docker run -it --rm my-app`
## Further information:
Docker documentation: https://docs.docker.com/get-started/
Docker Hub: https://hub.docker.com/

# 2. Kubernetes Basics
### What is Kubernetes?

Kubernetes is an open-source platform for container orchestration. It automates the deployment, scaling, and management of containerized applications across multiple servers.

### Basic Kubernetes concepts:

* **Pod:** A pod is the smallest unit managed by Kubernetes. It can contain one or more containers.
* **Deployment:** A deployment defines a desired number of pods and ensures that this number is always available.
* **Service:** A service abstracts a group of pods and provides a single access point for clients.
* **Example:**

```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-app
spec:
  replicas: 3
  selector:
    matchLabels:
      app: my-app
  template:
    metadata:
      labels:
        app: my-app
    spec:
      containers:
      - name: my-app
        image: my-app
        ports:
        - containerPort: 80
apiVersion: v1
kind: Service
metadata:
  name: my-app
spec:
  selector:
    matchLabels:
      app: my-app
  ports:
  - protocol: TCP
    port: 80
    targetPort: 80
```
## Further information:

Kubernetes documentation: https://kubernetes.io/docs/home/
Kubernetes Tutorials: https://kubernetes.io/docs/tutorials/
# 3.
