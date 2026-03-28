# 06 - Docker (Deep)

## Why Deep Docker
You'll use Docker every single day. Shallow Docker knowledge ("I can write a Dockerfile") isn't enough. You need to understand networking, storage, security, and optimization.

## What to Learn

### Core Concepts (Week 1)
- [ ] How containers actually work — namespaces, cgroups, union filesystems
- [ ] Images vs containers vs volumes vs networks
- [ ] Docker daemon architecture — client, daemon, containerd, runc
- [ ] Image layers — how they work, why order matters in Dockerfiles
- [ ] Docker registries — Docker Hub, ECR, GHCR, self-hosted

### Dockerfile Mastery (Week 1)
- [ ] Multi-stage builds — separate build and runtime stages
- [ ] Layer caching — optimize for fast rebuilds
- [ ] `.dockerignore` — keep images small
- [ ] Base image selection — `alpine` vs `slim` vs `distroless` vs `scratch`
- [ ] Non-root users — never run as root in production
- [ ] `ENTRYPOINT` vs `CMD` — know the difference
- [ ] `COPY` vs `ADD` — almost always use COPY
- [ ] Build args vs environment variables
- [ ] Health checks in Dockerfiles
- [ ] Image scanning — `docker scout`, `trivy`

### Docker Networking (Week 1)
- [ ] Bridge, host, none, overlay networks
- [ ] Container-to-container communication
- [ ] Port mapping — publish vs expose
- [ ] DNS resolution between containers
- [ ] Network isolation

### Docker Compose (Week 2)
- [ ] Multi-service applications
- [ ] Service dependencies and health checks
- [ ] Named volumes and bind mounts
- [ ] Environment files
- [ ] Profiles for different environments
- [ ] Override files (`docker-compose.override.yml`)
- [ ] Networking between services

### Docker in Production (Week 2)
- [ ] Resource limits — memory, CPU
- [ ] Logging drivers — json-file, syslog, fluentd
- [ ] Restart policies
- [ ] Docker security — read-only filesystems, dropped capabilities, seccomp profiles
- [ ] Image size optimization — getting images under 50MB
- [ ] BuildKit features — cache mounts, secret mounts, SSH forwarding

## Hands-On Project

**Containerize a microservices application from scratch:**

1. Build a 3-service app: API (Python), Worker (Python), Frontend (Node)
2. Each service has an optimized multi-stage Dockerfile (< 100MB final image)
3. Docker Compose for local development with:
   - Hot reloading (bind mounts)
   - Postgres + Redis as dependencies
   - Health checks on all services
   - Network isolation (frontend can't reach DB directly)
4. Separate production Compose file with:
   - Resource limits
   - Non-root users
   - Read-only filesystems
   - Proper logging
5. CI pipeline (GHA) that builds, scans, and pushes images to GHCR
6. Write a script that builds all images and reports: image sizes, layer counts, vulnerability scan results

## Validation
You're done when you can:
- Write a multi-stage Dockerfile from memory
- Debug container networking issues with `docker exec` and `nsenter`
- Explain how containers differ from VMs at the kernel level
- Optimize any Dockerfile to under 100MB
- Set up a full development environment with Docker Compose in 30 minutes
