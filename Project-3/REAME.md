# 🚀 Edureka Webpage Deployment using Kubernetes DaemonSet (No Service)

This project demonstrates how to deploy a static Edureka webpage using a **Kubernetes DaemonSet** — without exposing it via a Kubernetes Service. Each node in your cluster will run exactly one pod containing the static web content.

---

## 🐳 Step 1: Clone the Repository

```
git clone https://github.com/edurekacontent/dockerContent
cd dockerContent
cd 'Case-study app'
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

This YAML file defines one Kubernetes objects:


**DaemonSet**: in Kubernetes ensures that a specific pod runs on every node (or a subset of nodes) in the cluster.


Create a file web-daemonset.yaml with the following content:

```
appVersion: apps/v1
kind: DaemontSet
metadata:
  name: edureka-web-daemontset
  labels:
    app: edureka-web
spec:
  selector:
    matchLabels:
      app: edureka-web
  template:
    metadata:
      labels:
        app: edureka-web
    spec:
      containers:
      - name: edureka-web
        image: edmundo1986/edureka-webpage:latest
        ports:
        - containerPort: 80

``

🧹 Cleanup
```
kubectl delete -f web-daemonset.yaml

```
