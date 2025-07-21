# 📦 Kubernetes Persistent Volumes and Claims Demo

This project demonstrates how to use **Persistent Volumes (PVs)** and **Persistent Volume Claims (PVCs)** in Kubernetes by deploying an **NGINX** pod that serves static content from a persistent storage volume.

---

## 📚 Table of Contents

- [📦 Project Overview](#-project-overview)
- [📁 File Structure](#-file-structure)
- [🔧 Prerequisites](#-prerequisites)
- [🚀 Deployment Instructions](#-deployment-instructions)
- [🧪 Testing](#-testing)
- [🧹 Cleanup](#-cleanup)
- [📝 License](#-license)

---

## 📦 Project Overview

We will:

1. Create a **PersistentVolume (PV)** backed by a `hostPath`.
2. Create a **PersistentVolumeClaim (PVC)** that requests storage.
3. Create a **ConfigMap** containing a custom `index.html`.
4. Deploy an **NGINX Pod** that:
   - Mounts the PVC to serve static HTML.
   - Injects the custom `index.html` using a ConfigMap.

---

## 📁 File Structure

Project-4/
├── configmap.yaml # Contains the HTML to serve
├── pod.yaml # Defines the NGINX pod and volume mounts
├── pvc.yaml # PersistentVolumeClaim requesting storage
├── pv.yaml # HostPath PersistentVolume
└── README.md # You're here!


---

## 🔧 Prerequisites

- Kubernetes cluster (Minikube, Kind, or real cluster)
- `kubectl` installed and configured

---

## 🚀 Deployment Instructions

> **Note:** These steps assume you're in the root of the project folder.

1. **Create the Persistent Volume**

```
kubectl apply -f pv.yaml
```

2. Create the Persistent Volume Claim
```
kubectl apply -f pvc.yaml

```
3. Create the ConfigMap with HTML

```
kubectl apply -f configmap.yaml
```

4. Deploy the NGINX Pod

```
kubectl apply -f pod.yaml

```

## Testing

1. Port Forward to Access the Pod

```
kubectl port-forward pod/nginx-pod 8080:80

```

2. Visit the Web Page

```
curl http://localhost:8080
```
✅ You should see:

```
<h1>Hello from Persistent Volume!</h1>

```
## Cleanup

```
kubectl delete -f pod.yaml
kubectl delete -f configmap.yaml
kubectl delete -f pvc.yaml
kubectl delete -f pv.yaml
```
