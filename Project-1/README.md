 Project-1: # Kubernetes Pod Creation 

This project demonstrates how to create a simple **Kubernetes Pod** using a manifest file. It is intended for beginners looking to understand the core concepts of Kubernetes.

## 📌 Overview

A **Pod** is the smallest and simplest unit in the Kubernetes object model. It represents a single instance of a running process in your cluster.


---

## 🛠️ Prerequisites

- A working Kubernetes cluster (e.g., Minikube, kind, or a cloud provider)
- `kubectl` command-line tool installed and configured

---

## 📄 Pod Manifest Example

Here’s an example `pod.yaml` file that creates a simple Pod running an NGINX container:

```
apiVersion: v1
kind: Pod
metadata:
  name: nginx-pod
  labels:
    app: web
spec:
  containers:
    - name: nginx
      image: nginx:latest
      ports:
        - containerPort: 80
```
# 🚀 How to Deploy

1 . Apply the manifest using kubectl:

```
kubectl apply -f pod.yaml
```

 2 . Check Pod status:
 ```
kubectl get pods

 ```

 # 🧹 Cleanup

1 . To delete the Pod when you're done:


```
kubectl delete -f pod.yaml
```