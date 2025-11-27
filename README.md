# mesh-ml-lab

A local, cloud-like platform for experimenting with **service mesh**, **Go-based ML inference**, **observability**, and **data analytics** — all running on your Mac using k3d, Helm, GitOps, and Terraform.

This repo is structured as a real mini-platform project:
- Kubernetes ⚙️ (k3d)
- Service Mesh 🔗 (Istio or Linkerd)
- Go ML Service 🧠 (logistic regression / ONNX-ready)
- Observability 📈 (Prometheus, Grafana, Loki, Tempo)
- Data Pipeline 🗃️ (MinIO + DuckDB ETL)
- GitOps 🚀 (Argo CD or Flux)
- Infra as Code 🏗️ (Terraform + LocalStack)

Think of this as a **tiny AWS clone** for learning service mesh, ML inference, and analytics — **without cloud costs**.

---

## 🚀 Quickstart

### Prerequisites (macOS)

Install tools using Homebrew:

    brew install k3d kubectl helm gh
    brew install minio/stable/mc duckdb   # optional
    gh auth login

### Bootstrap the cluster

    make cluster-up

### Deploy the hello-world service

    make deploy-hello

### Verify the app

    kubectl get pods -n apps
    kubectl port-forward svc/hello-world 8080:80 -n apps
    curl localhost:8080

---

## 🧱 Project Structure (initial)

```
mesh-ml-lab/
  docs/
    architecture.md
    milestones.md
  infra/
    k8s/
    helm/
    terraform/
  platform/
    cluster-bootstrap/
    gitops/
  services/
    ml-service/
    analytics-api/
    event-generator/
    frontend/
  ops/
    grafana-dashboards/
    alerts/
  scripts/
    create-m1-issues.sh
    create-extra-labels.sh
  .github/
    workflows/
```

---

## 🧩 Roadmap (Milestones)

This project is built in progressive milestones, each representing a working platform feature:

1. **M1 – Local Cluster & Hello World Platform**  
2. **M2 – Observability Stack (Metrics/Logs/Traces)**  
3. **M3 – ML Inference Service in Go**  
4. **M4 – Service Mesh Integration & Traffic Control**  
5. **M5 – Data & Analytics Pipeline (MinIO + DuckDB)**  
6. **M6 – GitOps & IaC (Terraform + LocalStack)**  
7. **M7 – Dashboards, Fault Injection, and Demo Scenarios**

All milestones and issues are tracked via GitHub milestones and labels.

---

## 🛠 Makefile Tasks (initial)

| Make Target          | Description                          |
|----------------------|--------------------------------------|
| `make cluster-up`    | Spin up the k3d cluster              |
| `make cluster-down`  | Delete the cluster                   |
| `make deploy-hello`  | Deploy the hello-world example       |

---

## 📦 Tech Stack Summary

| Area            | Tools                                   |
|-----------------|------------------------------------------|
| Kubernetes      | k3d, kubectl, Helm                       |
| Service Mesh    | Istio or Linkerd                         |
| ML Inference    | Go (logistic regression / ONNX-ready)    |
| Observability   | Prometheus, Grafana, Loki, Tempo         |
| Data Pipeline   | MinIO (S3), DuckDB                       |
| GitOps          | Argo CD or Flux                          |
| IaC             | Terraform + LocalStack                   |
| CI/CD           | GitHub Actions                           |

---

## 🤝 Contributing

This repo uses a structured label taxonomy:

- `area:*` — subsystem (mesh, observability, ml-service, terraform, etc.)
- `kind:*` — task type (feature, task, bug, refactor)
- `priority:*` — backlog planning
- `status:*` — workflow state

Good first issues are tagged with **`good first issue`**.

---

## 📄 License

MIT License

---

Happy hacking ⚡  
This project is designed to help you build real platform engineering, ML inference, analytics, and service mesh skills — all **locally**.