# 11 - Kubernetes (Deep)

## Why K8s Gets 4 Weeks
Kubernetes is the most important technology on this list. It's complex, but it's the industry standard for running anything in production. Every DevOps job posting requires it.

## What to Learn

### Architecture & Core Concepts (Week 1)
- [ ] Control plane — API server, etcd, scheduler, controller manager
- [ ] Worker nodes — kubelet, kube-proxy, container runtime
- [ ] Pods — why pods not containers, multi-container pods, init containers, sidecar containers
- [ ] ReplicaSets — desired state, reconciliation loop
- [ ] Deployments — rolling updates, rollback, revision history
- [ ] Namespaces — resource isolation, not security isolation
- [ ] Labels and selectors — how K8s connects everything
- [ ] Annotations — metadata for tools

### Services & Networking (Week 1)
- [ ] ClusterIP — internal service discovery
- [ ] NodePort — expose on node ports
- [ ] LoadBalancer — cloud provider integration
- [ ] Headless services — for StatefulSets
- [ ] Ingress — routing external traffic, Nginx Ingress Controller
- [ ] Network Policies — restrict pod-to-pod communication
- [ ] CoreDNS — how service discovery works (`service.namespace.svc.cluster.local`)
- [ ] CNI plugins — Calico, Cilium (know they exist, what they do)

### Storage (Week 2)
- [ ] Volumes — emptyDir, hostPath
- [ ] PersistentVolumes (PV) and PersistentVolumeClaims (PVC)
- [ ] StorageClasses — dynamic provisioning
- [ ] StatefulSets — for databases, stable network identity, ordered deployment
- [ ] ConfigMaps — non-sensitive configuration
- [ ] Secrets — sensitive data (know they're base64, not encrypted by default)

### Workloads (Week 2)
- [ ] DaemonSets — one pod per node (monitoring agents, log collectors)
- [ ] Jobs and CronJobs — batch processing
- [ ] Horizontal Pod Autoscaler (HPA) — scale on CPU/memory/custom metrics
- [ ] Vertical Pod Autoscaler (VPA) — right-sizing requests
- [ ] Pod Disruption Budgets — safe maintenance
- [ ] Resource requests and limits — how scheduling works, QoS classes
- [ ] Probes — liveness, readiness, startup probes

### Security (Week 3)
- [ ] RBAC — Roles, ClusterRoles, RoleBindings, ServiceAccounts
- [ ] Pod Security Standards — restricted, baseline, privileged
- [ ] Security contexts — runAsNonRoot, readOnlyRootFilesystem, capabilities
- [ ] Network Policies for microsegmentation
- [ ] Secrets encryption at rest
- [ ] Image pull policies and private registries

### Operations (Week 3)
- [ ] `kubectl` mastery — get, describe, logs, exec, port-forward, top, explain
- [ ] Debugging — CrashLoopBackOff, ImagePullBackOff, Pending pods, OOMKilled
- [ ] Cluster upgrades — how to do it safely
- [ ] etcd backup and restore
- [ ] Resource quotas and limit ranges
- [ ] Priority classes and preemption

### Production Patterns (Week 4)
- [ ] EKS — managed K8s on AWS, node groups, Fargate profiles
- [ ] Cluster autoscaler and Karpenter
- [ ] ExternalDNS — automatic DNS records from Ingress
- [ ] cert-manager — automatic TLS certificates
- [ ] External Secrets Operator — sync from Vault/AWS Secrets Manager
- [ ] Kustomize — patching manifests for different environments
- [ ] Multi-cluster strategies

## Hands-On Project

**Deploy a complete microservices application to Kubernetes:**

1. Set up a local cluster with `kind` or `minikube`, then an EKS cluster
2. Deploy 3+ microservices with:
   - Deployments with proper resource requests/limits
   - Services (ClusterIP for internal, LoadBalancer for API)
   - Ingress with TLS (cert-manager + Let's Encrypt)
   - ConfigMaps and Secrets
   - HPA based on CPU and custom metrics
   - Network Policies (services can only talk to what they need)
   - RBAC (dev team can read pods, ops team can manage deployments)
3. StatefulSet for Postgres with PVCs
4. CronJob for database backups
5. DaemonSet for log collection (Promtail)
6. Pod Disruption Budgets for safe updates
7. Kustomize overlays for dev/staging/prod
8. Debug exercise: intentionally break things (bad image, OOM, wrong selectors) and fix them

## Validation
You're done when you can:
- Write K8s manifests from memory for any common workload
- Debug a pod stuck in CrashLoopBackOff in under 5 minutes
- Design a K8s architecture for a production microservices application
- Explain how a request flows from the internet to a pod
- Set up EKS with all production essentials (autoscaling, TLS, RBAC, monitoring)
