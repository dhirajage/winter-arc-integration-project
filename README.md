# 🚀 Winter Arc Integration Project: Deploy, Monitor & Recover

> **DevOps Winter Arc — Revision Week (Days 30–36 / 90)**  
> A 7-day end-to-end integration project connecting **Linux**, **Docker**, **Kubernetes (`kind`)**, and **AWS Cloud Architecture** using one shared application.

---

## 📌 Project Overview

- **Objective:** Build, deploy, monitor, break, and recover a single containerized web application across local Linux, Docker/Compose, and local Kubernetes (`kind`), then map it to a secure, production-ready AWS architecture.
- **Chosen Application:** Lightweight Node.js / Express Web App *(or Static Nginx Site)*
- **Application Endpoints:**
  - `GET /` — Main landing page
  - `GET /health` — Health check endpoint returning HTTP `200 OK`
- **Cost & Safety Rule:** Local-first execution (`Linux VM`, `Docker`, `kind`). AWS components remain conceptual/design-only to prevent unintended cloud charges.

---

## 📂 Repository Structure

```text
winter-arc-integration-project/
├── app/            # Application source code and configuration
├── linux/          # Systemd service files, permissions, networking, and log checks
├── docker/         # Dockerfile, .dockerignore, and docker-compose.yml
├── kubernetes/     # K8s manifests (Deployment, Service, ConfigMap, Probes)
├── aws-design/     # VPC, ALB, EC2/EKS, RDS, and IAM architecture documentation
├── docs/           # Runbooks, troubleshooting notes, and failure RCA reports
└── screenshots/    # Proof of execution, architecture diagrams, and terminal logs
```

---

## 🏗️ System Architecture

### 1. Local Execution (Linux Host & Docker)
```text
[User] ──▶ [Linux Host / Docker Container] ──▶ [Web App (:3000 / :80)]
```

### 2. Local Kubernetes Orchestration (`kind`)
```text
[User] ──▶ [K8s Service (NodePort / ClusterIP)] ──▶ [Deployment / Pods] ──▶ [App Container]
```

### 3. AWS Cloud Design *(Conceptual Architecture Only)*
```text
[Internet] ──▶ [Public ALB] ──▶ [Private App Tier (EC2 / EKS)] ──▶ [Private Database (RDS)]
                     │
              (VPC / Security Groups / IAM)
```

---

## 🗓️ 7-Day Execution Roadmap

| Day | Focus Area | Key Milestone | Status |
| :--- | :--- | :--- | :--- |
| **Day 30** | Kickoff & Planning | Select app, setup repo, draw architecture, build tracker | ✅ Completed |
| **Day 31** | Linux & Networking | Run app on Linux; inspect users, permissions, logs & ports | ⬜ Pending |
| **Day 32** | Docker | Build `Dockerfile`, enforce non-root user, verify health checks | ⬜ Pending |
| **Day 33** | Docker Compose | Multi-container stack, env variables, persistent volumes | ⬜ Pending |
| **Day 34** | Kubernetes (`kind`) | Deployments, Services, probes, scaling & rollbacks | ⬜ Pending |
| **Day 35** | AWS Design & Security | Map app to VPC, ALB, IAM, private subnets & RDS | ⬜ Pending |
| **Day 36** | Break/Fix & Demo | Inject failure, inspect logs, recover & document lessons | ⬜ Pending |

---

## 📊 Skill Revision Tracker

| Skill Domain | Core Topics Covered | Self-Assessment |
| :--- | :--- | :--- |
| **Linux** | CLI commands, `journalctl` logs, file permissions, ports (`ss`/`netstat`) | *[Confident / Need Practice / Need Help]* |
| **Docker** | Images, containers, non-root users, volumes, bridge networks, Compose | *[Confident / Need Practice / Need Help]* |
| **Kubernetes** | Deployments, Services, ConfigMaps, Liveness/Readiness probes, Rollouts | *[Confident / Need Practice / Need Help]* |
| **AWS** | IAM roles, VPC subnets, Security Groups, ALB, EC2/EKS, RDS | *[Confident / Need Practice / Need Help]* |

### 🎯 Top 3 Weak Areas Selected for Revision (Days 31–36)
1. *[Area 1 — e.g., Kubernetes Liveness & Readiness Probes]*
2. *[Area 2 — e.g., Docker Multi-Stage Builds & Non-Root Permissions]*
3. *[Area 3 — e.g., AWS VPC Private Subnet Routing & Security Groups]*

---

## 🧠 Day 30 Reflection & Interview Warm-Up

- **What I understand well:** *[Fill in your strengths, e.g., basic Linux file permissions, building Dockerfiles, and core EC2/VPC concepts.]*
- **What needs revision:** *[Fill in your gaps, e.g., Kubernetes Service networking, probe configurations, and rollbacks.]*

### Quick Concept Check
- **Image vs. Container:** An image is the read-only packaged template; a container is a running instance of that image.
- **Kubernetes Service:** Provides a stable network endpoint and DNS name to reach a dynamic set of Pods even as Pod IPs change.
- **Private AWS App Tier:** Reduces the attack surface by preventing direct internet access, forcing all inbound traffic through a controlled entry point like an Application Load Balancer (ALB).
- **Logs in Troubleshooting:** Logs provide timestamped evidence of application behavior, errors, and system events during a failure.

---

## 🛠️ Prerequisites
- Linux environment (Ubuntu VM / WSL2)
- Docker & Docker Compose
- `kubectl` & `kind` (Kubernetes in Docker)
- Git