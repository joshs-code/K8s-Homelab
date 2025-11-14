# Kubernetes Homelab: Dell Lattidue Laptop & Datto NFS Storage

![Kubernetes](https://img.shields.io/badge/Kubernetes-v1.31.14-blue?logo=kubernetes)
![Ubuntu](https://img.shields.io/badge/Ubuntu-25.04-orange?logo=ubuntu)
![Calico](https://img.shields.io/badge/CNI-Calico-green)
![Helm](https://img.shields.io/badge/Helm-v3.15.4-helm)
![Pi-hole](https://img.shields.io/badge/Pi--hole-Persistent-success)
![GitOps](https://img.shields.io/badge/GitOps-Ready-blue?logo=git)

> **A production-grade 2-node Kubernetes cluster running Pi-hole with full data persistence on a 1.6TB Datto disk via NFS.**  
> **Hardware**: Dell Latitude (control plane) + Datto Alto 3 (worker + storage)  
> **Goal**: Learning more about Kubernetes and set up a network-wide ad blocking that survives reboots, upgrades, and node failures — **with GitOps**.

---
## Architecture Diagram

```text
Your Laptop
     │
     │ kubectl
     ▼
┌─────────────────┐
│ ubuntu1 (Dell)  │ ← Control Plane (tainted)
│                 │    • No user workloads
└─────────────────┘
          │
          │ Calico CNI
          ▼
┌─────────────────┐
│ ubuntu2 (Datto) │ ← Worker + Storage
│                 │    • Pi-hole Pod
│ 1.6TB NFS       │    • /mnt/datastore
└─────────────────┘
          │
          │ NFS Mount
          ▼
┌─────────────────┐
│ Pi-hole Web UI  │ ← http://<node-ip>:30080/admin
└─────────────────┘
```

## Built With

- **Kubernetes** — `kubeadm`, `kubectl`, `kubelet`
- **Helm** — Declarative deployments
- **Calico** — Pod networking
- **LVM + NFS** — Enterprise-grade storage
- **Git + GitHub** — GitOps foundation

## Next Steps

- [ ] Add **Prometheus + Grafana** monitoring
- [ ] Deploy **Kubernetes Dashboard**
- [ ] Deploy **Invidious**
- [ ] Deploy **Jellyfin**
- [ ] Set up **Ingress-NGINX + cert-manager + TLS**
- [ ] Automate with **ArgoCD** (full GitOps)
