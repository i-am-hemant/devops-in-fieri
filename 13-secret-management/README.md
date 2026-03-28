# 13 - Secret Management (HashiCorp Vault)

## Why Vault
Secrets in environment variables, config files, or K8s Secrets (base64 is NOT encryption) are a security risk. Vault is the industry standard for centralized secret management.

## What to Learn (Week 1)

### Core Concepts
- [ ] Architecture — server, storage backend, seal/unseal, root token
- [ ] Secrets engines — KV (v1, v2), AWS, database, PKI
- [ ] Authentication methods — token, AppRole, Kubernetes, OIDC, AWS IAM
- [ ] Policies — HCL format, path-based permissions, capabilities
- [ ] Leases — dynamic secrets with TTL, renewal, revocation
- [ ] Audit logging — every access logged

### Practical Usage
- [ ] KV secrets engine — CRUD operations, versioning, soft delete
- [ ] Dynamic database credentials — Vault creates/revokes DB users on demand
- [ ] AWS secrets engine — temporary IAM credentials
- [ ] PKI secrets engine — internal CA, auto-rotating TLS certificates
- [ ] Transit engine — encryption as a service (encrypt data without exposing keys)
- [ ] AppRole auth — for CI/CD pipelines and applications

### Kubernetes Integration
- [ ] Vault Agent Injector — sidecar that injects secrets into pods
- [ ] External Secrets Operator — sync Vault secrets to K8s Secrets
- [ ] CSI provider — mount secrets as volumes
- [ ] Vault auth via Kubernetes ServiceAccounts

### Operations
- [ ] Auto-unseal with AWS KMS
- [ ] High availability setup
- [ ] Backup and recovery
- [ ] Secret rotation strategies
- [ ] Vault in CI/CD — how GHA/pipelines authenticate and fetch secrets

## Hands-On Project

**Set up Vault for your Kubernetes cluster:**

1. Deploy Vault on K8s using Helm (HA mode with Raft storage)
2. Configure auto-unseal with AWS KMS
3. Set up auth methods: Kubernetes (for pods), AppRole (for CI/CD)
4. KV engine for application config secrets
5. Database engine for dynamic Postgres credentials
6. PKI engine for internal mTLS certificates
7. External Secrets Operator syncing secrets to K8s
8. GHA pipeline that authenticates to Vault and deploys with secrets
9. Audit logging enabled and forwarded to your monitoring stack

## Validation
You're done when you can:
- Deploy and configure Vault from scratch
- Explain dynamic secrets and why they're better than static ones
- Integrate Vault with Kubernetes and CI/CD pipelines
- Set up a PKI infrastructure with auto-rotating certificates
