# 05 - Web Infrastructure

## Why This Matters
Before you automate infrastructure, you need to understand what you're automating. Every production system involves proxies, load balancers, and caching — understand them deeply.

## What to Learn

### Nginx Deep Dive (Week 1)
- [ ] Nginx as a web server — serving static files, directory listing
- [ ] Virtual hosts / server blocks — multiple sites on one server
- [ ] Location blocks — routing rules, regex matching, priority order
- [ ] Nginx as a reverse proxy — `proxy_pass`, headers, timeouts
- [ ] Nginx as a load balancer — round-robin, least connections, IP hash, weighted
- [ ] SSL termination with Nginx — certs, HSTS, OCSP stapling
- [ ] Rate limiting and connection limiting
- [ ] Nginx logging — access logs, error logs, custom log formats
- [ ] Nginx performance tuning — worker processes, connections, buffers
- [ ] Health checks and upstream configuration

### Proxy Concepts (Week 1)
- [ ] Forward proxy — what it is, use cases (corporate networks, VPNs)
- [ ] Reverse proxy — what it is, why every production app uses one
- [ ] Difference between the two (know this cold for interviews)
- [ ] L4 vs L7 load balancing — when to use which
- [ ] Sticky sessions — when you need them, why you should avoid them

### Caching (Week 2)
- [ ] Browser caching — `Cache-Control`, `ETag`, `Last-Modified`
- [ ] CDN caching — how Cloudflare/CloudFront work, cache invalidation
- [ ] Nginx proxy cache — `proxy_cache`, cache zones, purging
- [ ] Application caching — Redis/Memcached basics
- [ ] Cache invalidation strategies (the hardest problem in CS)

### Firewalls & Security (Week 2)
- [ ] UFW — simple firewall management
- [ ] iptables — understanding chains and rules
- [ ] WAF concepts — what a Web Application Firewall does
- [ ] DDoS mitigation basics
- [ ] Security headers — CSP, CORS, X-Frame-Options, X-Content-Type-Options

## Hands-On Project

**Build a production-like web infrastructure on a single machine (Docker Compose):**

```
Client → Nginx (LB) → [App1, App2, App3] → Redis (cache) → Postgres (DB)
```

1. Nginx as reverse proxy + load balancer with health checks
2. Three instances of a simple Python/Node app
3. SSL termination at Nginx (self-signed or Let's Encrypt)
4. Nginx proxy caching for static assets
5. Redis as application-level cache
6. Rate limiting on the API endpoints
7. Custom access logging with request timing
8. Simulate failure: kill one app instance, verify LB routes around it
9. Add a second Nginx as a forward proxy for outbound traffic filtering

## Validation
You're done when you can:
- Write Nginx configs from scratch without looking anything up
- Explain the full request path from client to database and back
- Debug a 502 Bad Gateway and know exactly where to look
- Set up SSL termination and get an A+ on SSL Labs
