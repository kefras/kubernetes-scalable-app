# Kubernetes Scalable Cluster Blueprint

A production-ready declarative orchestration blueprint designed to establish high-availability microservice replication tracking. This project implements native Kubernetes manifests to handle automated container self-healing, isolated environment constraints, decoupled resource configuration, and elastic internal load balancing.

## 🏗️ Cluster Architecture



               [ External Public Traffic Entry ]
                              │
                              ▼
                  ┌───────────────────────────┐
                  │    K8s Service Layer      │
                  │   (NodePort: 30080)       │
                  └─────────────┬─────────────┘
                                │
      ┌───────────── ───────────┼────────────────────────┐
      │ Distributed Load        │ Distributed Load       │ Distributed Load
      ▼                         ▼                        ▼
 ┌────────────────────────┐┌────────────────────────┐┌────────────────────────┐
 │     Pod Replica 1      ││     Pod Replica 2      ││     Pod Replica 3      │
 │ ┌────────────────────┐ ││ ┌────────────────────┐ ││ ┌────────────────────┐ │
 │ │ scalable-web:nginx │ ││ │ scalable-web:nginx │ ││ │ scalable-web:nginx │ │
 │ └────────────────────┘ ││ └────────────────────┘ ││ └────────────────────┘ │
 └────────────────────────┘└────────────────────────┘└────────────────────────┘






> 💡 **📍 ARCHITECTURE DIAGRAM INSERTION POINT**
> Create a folder named `docs/` at the root of this repository and save your visual Kubernetes cluster network layout schematic (e.g., `k8s-cluster.png`) inside it. Replace this quote block with your active asset reference link:
<p align="center">
  <img src="./kubernetes-scalable-app/kubernetes-scalable-app diagram.png" alt="Architecture Diagram" width="650">
</p>

---

## ⚡ Key Manifest Engineering Components

* **Elastic Replication Engine (`Deployment`):** Declares a highly available 3-Pod state constraint strategy. It features native structural self-healing, automatically spinning up fresh container replicas if any node or pod encounters a runtime crash.
* **Dynamic Traffic Abstractions (`Service`):** Exposes internal network workloads using standardized `NodePort` mapping arrays, distributing traffic evenly down into the underlying replica pods.
* **Decoupled Resource Mappings:** Configured with specific resource constraints (`requests` and `limits`) to guard the master control plane against CPU throttling and Out-Of-Memory (OOM) errors.

## 🛠️ Technology Stack

* **Orchestration Engine:** Kubernetes Core (K8s API v1)
* **Local Cluster Control Plane:** Minikube / K3s Engine
* **Core Runtimes:** Containerd / Docker Runtime Daemon
* **Networking Layer:** CoreDNS, IPVS Load Balancing Engines
