# 🚀 Kubernetes Deployment: Webpage from Edureka Repo

This project demonstrates how to deploy a  webpage using a **Dockerized webpage container** on a **Kubernetes cluster**. The website content is sourced from the [Edureka GitHub Repository](https://github.com/edurekacontent/dockerContent).


## 🔧 Prerequisites

- Docker Desktop installed and configured
- Kubernetes cluster (Minikube, Kind, EKS, GKE, etc.)
- `kubectl` configured to access your cluster
- Docker Hub account (or another registry)

---

## 🐳 Step 1: Clone the Repository

```
git clone https://github.com/edurekacontent/dockerContent
cd dockerContent
```

🏗️ Step 2: Build and Push Docker Image
Make sure the Dockerfile looks like this:

```
Dockerfile
FROM nginx:alpine
COPY . /usr/share/nginx/html
```
Build the image:
```
docker build -t edmundo1986/edureka-webpage:latest .

```
Push Docker Image:
```
docker push edmundo1986/edureka-webpage:latest
```
☸️ Step 3: Deploy on Kubernetes:

This YAML file defines two Kubernetes objects:


**Deployments**: Manage the lifecycle of one or more identical Pods, including scaling, updates, and rollbacks. 

**Services**: Provide a stable endpoint for accessing a set of Pods, abstracting away the underlying Pod details. 

Create a file web-deployment.yaml with the following content:

```
apiVerion: app/v1
kind: Deployment
metadata:
   name: edureka-web
```
