# 16 - Artifact Management (Artifactory)

## Why Artifact Management
Production systems need a single source of truth for all built artifacts — Docker images, Helm charts, Python packages, binaries. Artifactory is the universal artifact repository.

## What to Learn (Week 1)

### Concepts
- [ ] What artifacts are — Docker images, Helm charts, npm packages, Python wheels, JARs, raw files
- [ ] Repository types — local (your artifacts), remote (proxy to public), virtual (unified view)
- [ ] Why a central artifact store matters — caching, security scanning, auditability, immutability

### JFrog Artifactory
- [ ] Setup — self-hosted vs SaaS, Docker installation
- [ ] Docker registry — push/pull images via Artifactory
- [ ] Helm chart repository
- [ ] Python (PyPI) repository
- [ ] Generic repositories for arbitrary files
- [ ] Access control — permissions, tokens, groups
- [ ] Cleanup policies — retention, removing old versions
- [ ] Build integration — connecting CI pipelines to Artifactory
- [ ] Xray — vulnerability scanning of artifacts
- [ ] Promotion — moving artifacts through stages (dev → staging → prod)

### CI/CD Integration
- [ ] GHA → build Docker image → push to Artifactory → deploy
- [ ] Caching dependencies through Artifactory remote repos (faster builds)
- [ ] Build info — tracking which commits produced which artifacts

## Hands-On Project

1. Deploy Artifactory (Docker or free cloud tier)
2. Set up repositories: Docker (local + remote proxy for Docker Hub), Helm, PyPI
3. CI pipeline pushes Docker images and Helm charts to Artifactory
4. Configure image scanning with Xray
5. Set up promotion: dev builds → promote to staging → promote to prod
6. ArgoCD pulls Helm charts from Artifactory
7. Cleanup policy: keep last 5 versions, delete untagged images after 7 days

## Validation
You're done when you can:
- Set up Artifactory as a universal artifact store
- Integrate it with CI/CD and deployment pipelines
- Explain artifact promotion and immutability
