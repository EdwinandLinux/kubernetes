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
