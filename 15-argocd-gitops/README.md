# 15 - ArgoCD / GitOps

## Why GitOps
GitOps means Git is the single source of truth for your infrastructure and applications. ArgoCD watches your Git repo and syncs your cluster to match. No more `kubectl apply` from laptops.

## What to Learn (Week 1)

### GitOps Principles
- [ ] Declarative — describe desired state, not imperative steps
- [ ] Versioned — everything in Git, full audit trail
- [ ] Automated — changes applied automatically from Git
- [ ] Self-healing — drift detected and corrected

### ArgoCD Core
- [ ] Architecture — API server, repo server, application controller, Redis
- [ ] Applications — source (Git repo), destination (K8s cluster/namespace)
- [ ] Sync policies — manual, automated, self-heal, prune
- [ ] Sync waves and hooks — control deployment order
- [ ] Health checks — how ArgoCD determines if resources are healthy
- [ ] App of Apps pattern — managing ArgoCD apps with ArgoCD
- [ ] ApplicationSets — generate applications from templates (Git generator, cluster generator)

### Deployment Strategies with ArgoCD
- [ ] Rolling updates — default K8s strategy via ArgoCD
- [ ] Blue/Green — Argo Rollouts
- [ ] Canary — Argo Rollouts with analysis
- [ ] Progressive delivery — automated rollback on bad metrics

### Operations
- [ ] Multi-cluster management
- [ ] RBAC — projects, roles, SSO integration
- [ ] Secret management — ArgoCD + Vault (sealed secrets, external secrets)
- [ ] Notifications — Slack, GitHub status updates
- [ ] Disaster recovery — backup/restore ArgoCD itself

## Hands-On Project

**Implement full GitOps for your microservices:**

1. Repo structure:
   ```
   app-manifests/
     base/
       service-a/
       service-b/
       service-c/
     overlays/
       dev/
       staging/
       prod/
   argocd/
     apps/          # ArgoCD Application manifests
     projects/      # ArgoCD Projects
     appsets/       # ApplicationSets
   ```
2. ArgoCD deployed via Helm, managed by itself (bootstrapping)
3. App of Apps pattern — one root app manages all other apps
4. ApplicationSets for automatic app creation per service per environment
5. CI pipeline (GHA): build → push image → update image tag in manifests repo → ArgoCD syncs
6. Argo Rollouts for canary deployment of one service:
   - Deploy to 10% → check Prometheus metrics → promote to 50% → promote to 100%
   - Automatic rollback if error rate exceeds threshold
7. Slack notifications for sync status
8. RBAC: dev team can sync dev, only ops can sync prod

## Validation
You're done when you can:
- Set up GitOps from scratch for a multi-service, multi-environment setup
- Explain the difference between push-based and pull-based deployments
- Implement canary deployments with automated analysis
- Recover from a failed deployment using Git revert
