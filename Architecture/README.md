# 🧠 Kubernetes Architecture: Key Terms & Concepts

This document provides definitions and explanations of essential components in a Kubernetes (K8s) architecture. Whether you're preparing for the CKA exam or building your own cluster, understanding these terms is foundational.

---

## 📦 Core Components

### ⛵ kube-apiserver
The front-end for the Kubernetes control plane. All requests (kubectl, UI, controllers) go through it. It validates and configures data for API objects like pods, services, and deployments.

### 🧠 etcd
A consistent and highly-available key-value store used as Kubernetes’ backing store for all cluster data. It is the single source of truth.

### 🏗️ kube-scheduler
Assigns Pods to available nodes based on resource requirements, affinity rules, taints, and tolerations.

### 👮 kube-controller-manager
Runs controller processes (e.g., node controller, replication controller, endpoints controller). These controllers watch the state of the cluster and make changes to reach the desired state.

### 👁️ cloud-controller-manager
Lets cloud providers integrate with Kubernetes. It abstracts cloud-specific logic for managing load balancers, volumes, and nodes.

---

## 🖥️ Node Components

### 👷 kubelet
An agent that runs on each node and ensures containers are running as expected. It communicates with the API server.

### 🧠 kube-proxy
Manages network rules on each node. Implements service discovery and routing by handling the networking for Pods using iptables or IPVS.

### 🧱 Container Runtime
The software responsible for running containers. Supported runtimes include containerd, CRI-O, and (historically) Docker.

---

## 🧬 Kubernetes Workload Objects

### 📦 Pod
The smallest and simplest unit in the Kubernetes object model. A Pod represents a single instance of a running process in your cluster and can contain one or more tightly coupled containers that share networking and storage.

---

## 🛠️ Additional Concepts

### 📡 CNI (Container Network Interface)
Handles Pod-to-Pod networking and network policies. Examples: Calico, Flannel, Cilium.

### 💾 CSI (Container Storage Interface)
Manages persistent storage in Kubernetes. Allows dynamic provisioning and attachment of volumes. Examples: Rook, Portworx.

### 📦 CRI (Container Runtime Interface)
Defines how the kubelet talks to the container runtime. It supports modularity in container runtimes.

### ⚙️ Controller
A control loop that watches the state of your cluster and makes changes to move the current state toward the desired state. Examples: ReplicaSet controller, StatefulSet controller.

---

## 📜 Custom Resources

### 🔧 Custom Resource Definitions (CRDs)
Enable you to extend the Kubernetes API. CRDs define new types of resources that your cluster can understand.

### 🤖 Operators
Combine CRDs and controllers to automate the management of complex applications. Example: etcd Operator, Prometheus Operator.

---

## 🛡️ RBAC (Role-Based Access Control)

- Role: Defines a set of permissions within a namespace.
- ClusterRole: Defines permissions cluster-wide.
- RoleBinding / ClusterRoleBinding: Assigns a Role to a user/group/service account.

---
