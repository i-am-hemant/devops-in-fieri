# 19 - Capstone Project

## The Goal
Build a production-grade platform from scratch that ties everything together. This is your portfolio piece — the thing you point to in interviews.

## Architecture

```
                                    ┌─────────────┐
                                    │   Route 53   │
                                    │   (DNS)      │
                                    └──────┬───────┘
                                           │
                                    ┌──────┴───────┐
                                    │  CloudFront   │
                                    │  (CDN)        │
                                    └──────┬───────┘
                                           │
                                    ┌──────┴───────┐
                                    │  ALB/Ingress  │
                                    └──────┬───────┘
                                           │
                              ┌────────────┼────────────┐
                              │            │            │
                        ┌─────┴─────┐ ┌───┴───┐ ┌─────┴─────┐
                        │ Service A │ │Svc B  │ │ Service C │
                        │ (API)     │ │(Worker)│ │(Frontend) │
                        └─────┬─────┘ └───┬───┘ └───────────┘
                              │            │
                    ┌─────────┼────────────┤
                    │         │            │
              ┌─────┴───┐ ┌──┴──┐  ┌──────┴──────┐
              │ Postgres │ │Redis│  │ SQS/RabbitMQ│
              └─────────┘ └─────┘  └─────────────┘
```

## What to Build

### Application (reuse from earlier sections)
- Python API service (REST endpoints)
- Python worker service (processes queue messages)
- Simple frontend (static site or basic React/Vue)

### Infrastructure (all Terraform)
- [ ] AWS VPC — public/private subnets, NAT Gateway, 2 AZs
- [ ] EKS cluster — managed node groups, Karpenter for autoscaling
- [ ] RDS Postgres — Multi-AZ, encrypted, automated backups
- [ ] ElastiCache Redis
- [ ] SQS queues
- [ ] S3 for static assets + CloudFront CDN
- [ ] Route 53 domain
- [ ] ACM certificates

### Configuration (Ansible)
- [ ] Bastion host configuration
- [ ] Any EC2-based workloads

### Kubernetes (Helm + Kustomize)
- [ ] Deployments for all services
- [ ] HPA with custom metrics
- [ ] Network policies
- [ ] RBAC for teams
- [ ] Ingress with TLS (cert-manager)
- [ ] External Secrets Operator (Vault → K8s)

### CI/CD (GHA + ArgoCD)
- [ ] GHA: lint → test → build → push image → update manifests
- [ ] ArgoCD: detect manifest changes → sync to cluster
- [ ] Argo Rollouts: canary deployment for API service
- [ ] Environments: dev → staging → prod with approval gates

### Secrets (Vault)
- [ ] Vault on K8s (Helm, HA mode)
- [ ] Database credentials (dynamic)
- [ ] API keys and config
- [ ] TLS certificates (PKI engine)

### Observability
- [ ] Prometheus + Grafana (metrics)
- [ ] Loki + Promtail (logs)
- [ ] Alertmanager → Slack
- [ ] Custom dashboards per service
- [ ] SLO dashboards

### Artifact Management
- [ ] All Docker images in Artifactory or ECR
- [ ] Helm charts in OCI registry
- [ ] Vulnerability scanning on push

## Definition of Done

Your capstone is complete when:

1. **Everything is code** — zero manual steps except initial bootstrap
2. **A new developer** can clone the repos, run `terraform apply`, and have the full platform running
3. **A code change** automatically flows: commit → test → build → push → deploy (canary) → monitor
4. **A failure** triggers alerts, is visible in dashboards, and has a runbook
5. **Security** — mTLS between services, no hardcoded secrets, RBAC enforced, images scanned
6. **You can explain** every component, why it's there, and what happens if it fails

## Repository Structure

```
capstone/
  infrastructure/          # Terraform
    modules/
    environments/
  kubernetes/              # K8s manifests
    base/
    overlays/
  argocd/                  # ArgoCD apps
  ansible/                 # Configuration
  services/                # Application code
    api/
    worker/
    frontend/
  .github/workflows/       # CI/CD
  docs/
    architecture.md
    runbooks/
```

This is your DevOps portfolio. Make it excellent.
