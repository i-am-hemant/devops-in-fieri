# 10 - CI/CD Pipelines (Advanced GHA)

## Why This Section
You already know GHA basics. This section is about building production-grade pipelines — the kind that handle monorepos, multi-environment deployments, and complex workflows.

## What to Learn

### Advanced GHA (Week 1)
- [ ] Reusable workflows — `workflow_call`, inputs, secrets, outputs
- [ ] Composite actions — building shared action libraries
- [ ] Matrix strategies — dynamic matrices, `include`/`exclude`
- [ ] Concurrency — `concurrency` groups, cancelling in-progress runs
- [ ] Environments — protection rules, required reviewers, wait timers
- [ ] OIDC — keyless auth to AWS/GCP (no more long-lived credentials)
- [ ] Self-hosted runners — setup, security implications, autoscaling
- [ ] Caching — dependency caching, Docker layer caching, custom cache keys
- [ ] Artifacts — passing data between jobs, retention policies
- [ ] `github-script` — inline JS for complex logic
- [ ] Path filters — only trigger on relevant file changes (monorepo patterns)

### Pipeline Patterns (Week 1)
- [ ] Trunk-based development pipeline — lint → test → build → deploy to staging → manual gate → deploy to prod
- [ ] GitOps pipeline — build → push image → update manifest → ArgoCD syncs
- [ ] Terraform pipeline — plan on PR → apply on merge
- [ ] Monorepo pipeline — detect changed services, only build/deploy affected ones
- [ ] Rollback pipeline — one-click rollback to previous version
- [ ] Canary deployment pipeline — deploy to 5% → monitor → promote or rollback

### Security in CI/CD (Week 2)
- [ ] Secret management — GitHub secrets, environment secrets, OIDC
- [ ] Supply chain security — pinning action versions by SHA, Dependabot
- [ ] SAST/DAST scanning in pipeline
- [ ] Container image scanning (Trivy, Snyk)
- [ ] SBOM generation
- [ ] Signed artifacts and images (cosign)
- [ ] Branch protection + required status checks

### Testing in CI (Week 2)
- [ ] Unit tests → integration tests → E2E tests (test pyramid)
- [ ] Parallel test execution
- [ ] Test result reporting (JUnit XML → PR comment)
- [ ] Code coverage gates
- [ ] Infrastructure tests (Terratest, Molecule)

## Hands-On Project

**Build a production-grade CI/CD system for a microservices monorepo:**

1. Monorepo with 3 services + shared libraries + Terraform
2. Path-based triggering — only build changed services
3. Shared reusable workflows for: lint, test, build-docker, deploy
4. Pipeline stages:
   - PR: lint → test → build → plan terraform → post results as PR comment
   - Merge to main: build → push to ECR → deploy to staging → smoke tests → manual approval → deploy to prod
5. OIDC auth to AWS (no stored credentials)
6. Docker layer caching for fast builds
7. Slack notifications on failure
8. Deployment tracking — tag releases, link to deployment in GHA

## Validation
You're done when you can:
- Design a CI/CD pipeline for any application architecture
- Build reusable workflows that a whole org can share
- Debug a failing pipeline without re-running it 10 times
- Implement secure, keyless deployments to AWS
- Handle monorepo CI efficiently
