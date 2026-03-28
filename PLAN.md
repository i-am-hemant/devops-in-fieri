# DevOps Learning Path

Practical, project-driven path from foundations to production-grade infrastructure.

## Structure

Each topic folder contains:
- `README.md` — what to learn, resources, and the hands-on project
- `notes/` — your notes as you learn
- `projects/` — your project code

## Path Overview

| # | Topic | Estimated Weeks | Priority |
|---|-------|-----------------|----------|
| 01 | Linux & Bash Scripting | 3 | Core |
| 02 | Networking Fundamentals | 2 | Core |
| 03 | Git (Deep) | 1 | Core |
| 04 | Python Scripting for DevOps | 3 | Core |
| 05 | Web Infrastructure (Nginx, Proxies, LB, Caching) | 2 | Core |
| 06 | Docker (Deep) | 2 | Core |
| 07 | AWS | 4 | Core |
| 08 | Terraform | 3 | Core |
| 09 | Ansible | 2 | Core |
| 10 | CI/CD Pipelines (GHA - Advanced) | 2 | Core |
| 11 | Kubernetes (Deep) | 4 | Core |
| 12 | Helm | 1 | Core |
| 13 | Secret Management (Vault) | 1 | Core |
| 14 | Monitoring & Logging (Prometheus, Grafana, Loki) | 2 | Core |
| 15 | ArgoCD / GitOps | 1 | Core |
| 16 | Artifact Management (Artifactory) | 1 | Nice-to-have |
| 17 | Service Mesh (Istio) | 1 | Nice-to-have |
| 18 | Cloud Design Patterns | 2 | Nice-to-have |

**Total estimate: ~36 weeks for core, ~40 weeks with nice-to-haves**

## Capstone Project

After completing the core path, build this end-to-end:

```
Code (Python microservices)
  → GitHub (PRs, branch protection)
    → GHA (lint, test, build Docker image, push to registry)
      → ArgoCD (detects new image, syncs to K8s)
        → Kubernetes (running on AWS EKS)
          → Prometheus + Grafana (monitoring)
            → Loki (log aggregation)
              → Terraform (all infra as code)
                → Vault (all secrets managed)
```

This is what a real production DevOps pipeline looks like.

## Progress Tracking

- [ ] 01 - Linux & Bash Scripting
- [ ] 02 - Networking Fundamentals
- [ ] 03 - Git (Deep)
- [ ] 04 - Python Scripting for DevOps
- [ ] 05 - Web Infrastructure
- [ ] 06 - Docker
- [ ] 07 - AWS
- [ ] 08 - Terraform
- [ ] 09 - Ansible
- [ ] 10 - CI/CD Pipelines
- [ ] 11 - Kubernetes
- [ ] 12 - Helm
- [ ] 13 - Secret Management
- [ ] 14 - Monitoring & Logging
- [ ] 15 - ArgoCD / GitOps
- [ ] 16 - Artifact Management
- [ ] 17 - Service Mesh
- [ ] 18 - Cloud Design Patterns
- [ ] Capstone Project
