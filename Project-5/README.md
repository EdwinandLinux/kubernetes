# 📦 Kubernetes StatefulSet Deployment

This project demonstrates how to deploy a **StatefulSet** in Kubernetes using NGINX as an example. It includes a **headless service** and a **StatefulSet** with persistent volumes for each pod. This is ideal for stateful applications like databases, queues, and storage engines.

---

## 📁 Project Structure

Project-5/
├── headless-service.yaml # Headless service for stable network identity
├── nginx-statefulset.yaml # StatefulSet definition with volume claims
└── README.md # Project documentation


---

## 🚀 What is a StatefulSet?

A StatefulSet is a Kubernetes resource used to manage stateful applications. Unlike Deployments, it provides:

- **Stable pod names and identities**
- **Persistent storage linked to each pod**
- **Ordered startup, scaling, and deletion**

---

## ⚙️ Requirements

- A running Kubernetes cluster (Minikube, k3s, EKS, etc.)
- `kubectl` CLI installed and configured
- A default StorageClass available in your cluster

---

## 🛠️ Deployment Steps

1. Apply the headless service
```
kubectl apply -f headless-service.yaml

```

2. Deploy the StatefulSet

```
kubectl apply -f nginx-statefulset.yaml

```
📌 What Gets Deployed?

1. A headless service named nginx-headless for DNS-based pod resolution.

2. A StatefulSet named nginx with 3 replicas.

3. Each pod gets:

  1. A persistent volume

  2. A stable network identity like:
    ```
    nginx-0.nginx-headless.default.svc.cluster.local
    ```

🔍 Verifying the Deployment
Run the following to check pod status:
```
kubectl get statefulsets
kubectl get pods -l app=nginx
kubectl describe pod nginx-0
```

To connect to a pod:
```
kubectl exec -it nginx-0 -- /bin/bash

```
📚 Useful Commands

```
# Scale up/down
kubectl scale statefulset nginx --replicas=5

# Delete everything
kubectl delete -f nginx-statefulset.yaml
kubectl delete -f headless-service.yaml

```

📦 Use Cases for StatefulSets

1. Databases: PostgreSQL, MySQL, MongoDB

2. Messaging Queues: Kafka, RabbitMQ

3. Object Storage: MinIO, Ceph

🧹 Cleanup
```
kubectl delete -f .

```

⚠️ PVCs created by StatefulSets are not deleted automatically. You must remove them manually if needed:
```
kubectl delete pvc -l app=nginx

```