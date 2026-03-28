# 17 - Service Mesh (Istio)

## Why Service Mesh
When you have 20+ microservices, managing traffic routing, mTLS, retries, and observability at the application level doesn't scale. A service mesh handles this at the infrastructure level.

## What to Learn (Week 1)

### Concepts
- [ ] What a service mesh does — traffic management, security, observability
- [ ] Sidecar pattern — Envoy proxy injected alongside every pod
- [ ] Data plane (Envoy proxies) vs control plane (Istiod)
- [ ] When you need a service mesh vs when it's overkill

### Istio Core
- [ ] Installation — `istioctl`, Helm, IstioOperator
- [ ] Sidecar injection — automatic (namespace label) vs manual
- [ ] VirtualService — traffic routing rules, fault injection, retries, timeouts
- [ ] DestinationRule — load balancing, circuit breaking, connection pool
- [ ] Gateway — ingress traffic management
- [ ] ServiceEntry — accessing external services
- [ ] PeerAuthentication — mTLS modes (STRICT, PERMISSIVE)
- [ ] AuthorizationPolicy — L7 access control (who can call what)

### Traffic Management
- [ ] Canary routing — weight-based traffic splitting
- [ ] Header-based routing — route by user, feature flag
- [ ] Fault injection — test resilience by injecting delays/errors
- [ ] Circuit breaking — prevent cascading failures
- [ ] Retries and timeouts — at the mesh level, not application level
- [ ] Rate limiting

### Observability
- [ ] Kiali — service mesh topology visualization
- [ ] Distributed tracing — Jaeger integration
- [ ] Metrics — Envoy metrics automatically collected by Prometheus
- [ ] Access logging

## Hands-On Project

1. Install Istio on your K8s cluster
2. Enable sidecar injection for your microservices namespace
3. mTLS everywhere — STRICT mode
4. Traffic splitting: route 90% to v1, 10% to v2 of a service
5. Authorization policies: service-a can call service-b but not service-c
6. Fault injection: add 500ms delay to 10% of requests to test resilience
7. Circuit breaking: trip after 5 consecutive errors
8. Set up Kiali for visualization
9. Correlate traces across services with Jaeger

## Validation
You're done when you can:
- Explain what a service mesh does and when you actually need one
- Configure traffic routing, mTLS, and authorization policies
- Use Istio for canary deployments
- Debug service-to-service communication issues using mesh tools
