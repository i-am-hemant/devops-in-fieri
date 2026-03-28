# 12 - Helm

## Why Helm
Helm is the package manager for Kubernetes. You'll use it to install third-party tools (Prometheus, Nginx Ingress, cert-manager) and to template your own applications.

## What to Learn (Week 1)

### Fundamentals
- [ ] Charts — directory structure, `Chart.yaml`, `values.yaml`
- [ ] Templates — Go templating, `{{ .Values.x }}`, `{{ .Release.Name }}`
- [ ] Template functions — `default`, `quote`, `indent`, `toYaml`, `tpl`
- [ ] Flow control — `if/else`, `range`, `with`
- [ ] Named templates — `_helpers.tpl`, `define`, `include`
- [ ] Installing charts — `helm install`, `helm upgrade`, `helm rollback`
- [ ] Helm repos — adding, searching, pulling charts
- [ ] `values.yaml` — overriding defaults, multiple values files per environment

### Intermediate
- [ ] Chart dependencies — subcharts, `Chart.lock`
- [ ] Hooks — pre-install, post-install, pre-upgrade (database migrations)
- [ ] Tests — `helm test`, connection tests
- [ ] `helm template` — render manifests locally for debugging
- [ ] `helm diff` plugin — preview changes before upgrade
- [ ] Chart versioning and release management
- [ ] OCI registry for Helm charts (store in ECR/GHCR)

### Production Patterns
- [ ] Library charts — shared templates across multiple services
- [ ] Umbrella charts — one chart to deploy the whole stack
- [ ] Helmfile — declarative Helm releases
- [ ] Values management per environment (dev/staging/prod)
- [ ] Helm in CI/CD — lint, template, diff, upgrade

## Hands-On Project

**Create a Helm chart for your microservices application:**

1. Base chart for a generic microservice (configurable image, ports, resources, env vars)
2. Per-service values files that customize the base chart
3. Umbrella chart that deploys all services together
4. Hooks for database migrations on upgrade
5. Multiple environments via values files: `values-dev.yaml`, `values-prod.yaml`
6. Push chart to GHCR as OCI artifact
7. Install third-party charts: Prometheus stack, Nginx Ingress, cert-manager
8. Helmfile to manage all releases declaratively

## Validation
You're done when you can:
- Write a Helm chart from scratch
- Debug template rendering issues
- Manage a fleet of Helm releases across environments
- Explain when to use Helm vs Kustomize (and when to use both)
