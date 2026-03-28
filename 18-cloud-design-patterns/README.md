# 18 - Cloud Design Patterns

## Why Patterns
Patterns are the vocabulary of cloud architecture. Knowing them means you don't reinvent the wheel and you can communicate designs clearly.

## What to Learn

### Availability Patterns (Week 1)
- [ ] Health endpoint monitoring — liveness, readiness, deep health checks
- [ ] Queue-based load leveling — buffer spikes with SQS/RabbitMQ
- [ ] Throttling — rate limiting to protect services
- [ ] Circuit breaker — fail fast instead of cascading
- [ ] Retry with exponential backoff and jitter
- [ ] Bulkhead — isolate failures to prevent spread
- [ ] Deployment stamps — independent scale units per region/tenant
- [ ] Geode pattern — distribute data and processing globally

### Data Management Patterns (Week 1)
- [ ] Cache-aside — application manages cache population
- [ ] CQRS — separate read and write models
- [ ] Event sourcing — store events, derive state
- [ ] Sharding — horizontal data partitioning
- [ ] Saga — distributed transactions without 2PC
- [ ] Materialized view — pre-computed query results

### Design & Implementation Patterns (Week 2)
- [ ] Ambassador — proxy sidecar for external communication
- [ ] Sidecar — attach helper containers to main container
- [ ] Anti-corruption layer — protect new services from legacy interfaces
- [ ] Backends for Frontends (BFF) — dedicated backend per client type
- [ ] Strangler fig — gradually replace legacy systems
- [ ] Gateway aggregation — single entry point aggregates multiple services
- [ ] Gateway routing — route to different services based on request

### Management & Monitoring Patterns (Week 2)
- [ ] External configuration store — centralized config (Vault, Consul, Parameter Store)
- [ ] Leader election — one active node for coordination
- [ ] Scheduler agent supervisor — coordinate distributed actions
- [ ] Ambassador + sidecar for observability injection

## Study Method

For each pattern:
1. **What** — what problem does it solve?
2. **When** — when should you use it vs alternatives?
3. **How** — draw the architecture, identify the components
4. **Where** — which services on your current project would benefit?
5. **Implement** — build a small proof of concept

## Hands-On Project

**Enhance your microservices app with cloud patterns:**

1. Implement circuit breaker between services (Istio or application-level)
2. Add queue-based load leveling: API → SQS → Worker (handle traffic spikes)
3. Implement cache-aside pattern with Redis
4. Add retry with exponential backoff and jitter on all service-to-service calls
5. Implement health endpoint monitoring (deep health checks that verify dependencies)
6. Strangler fig: add a new service version behind a gateway, gradually migrate traffic
7. Document your architecture showing which patterns are used where

## Validation
You're done when you can:
- Look at a system architecture and identify which patterns are (or should be) in play
- Propose the right pattern for a given problem in an architecture review
- Implement any of these patterns in a real system
