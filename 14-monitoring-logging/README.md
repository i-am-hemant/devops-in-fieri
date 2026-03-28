# 14 - Monitoring & Logging

## Why This Matters
If you can't observe your system, you can't operate it. Monitoring tells you something is wrong. Logging tells you why.

## What to Learn

### Prometheus (Week 1)
- [ ] Architecture — Prometheus server, scraping, TSDB, alertmanager
- [ ] Metric types — counter, gauge, histogram, summary
- [ ] PromQL — queries, aggregations, rate(), increase(), histogram_quantile()
- [ ] Scrape configs — static targets, service discovery (K8s, EC2)
- [ ] Recording rules — pre-compute expensive queries
- [ ] Alert rules — defining alerts, severity levels
- [ ] Alertmanager — routing, receivers (Slack, PagerDuty, email), silences, inhibitions
- [ ] Exporters — node_exporter, blackbox_exporter, custom exporters
- [ ] Instrumenting your own app — client libraries (Python, Go)

### Grafana (Week 1)
- [ ] Data sources — Prometheus, Loki, CloudWatch
- [ ] Dashboard design — panels, variables, annotations
- [ ] Essential dashboards — node exporter, K8s cluster, application RED metrics
- [ ] Alerting in Grafana — alert rules, notification policies
- [ ] Grafana as code — provisioning dashboards and datasources via YAML/JSON
- [ ] Grafana Alloy (formerly Agent) — lighter alternative to full Prometheus

### Loki (Week 2)
- [ ] Architecture — distributors, ingesters, queriers, storage
- [ ] LogQL — queries, filters, parsers, aggregations
- [ ] Labels — why label cardinality matters
- [ ] Promtail — log collection agent, scrape configs, pipelines
- [ ] Integration with Grafana — log correlation with metrics

### Practical Monitoring (Week 2)
- [ ] The RED method — Rate, Errors, Duration (for services)
- [ ] The USE method — Utilization, Saturation, Errors (for infrastructure)
- [ ] The Four Golden Signals (Google SRE) — Latency, Traffic, Errors, Saturation
- [ ] SLIs, SLOs, SLAs — defining and measuring reliability
- [ ] On-call best practices — alert fatigue, runbooks, escalation
- [ ] Distributed tracing basics — Jaeger/Tempo, trace context propagation

## Hands-On Project

**Build a complete observability stack for your K8s microservices:**

1. Deploy kube-prometheus-stack via Helm (Prometheus, Grafana, Alertmanager, node-exporter)
2. Deploy Loki + Promtail for log aggregation
3. Instrument your Python services with prometheus_client:
   - Request count, latency histogram, error rate
   - Custom business metrics (orders processed, queue depth)
4. Build Grafana dashboards:
   - Cluster overview (nodes, pods, resource usage)
   - Per-service RED metrics
   - Log viewer correlated with metrics
5. Alert rules:
   - High error rate (> 1% of requests)
   - Pod restarts
   - High latency (p99 > 500ms)
   - Disk space > 80%
   - Certificate expiry < 30 days
6. Alertmanager routing: critical → PagerDuty/Slack, warning → email
7. Silence alerts during planned maintenance
8. Write runbooks for each alert

## Validation
You're done when you can:
- Write PromQL queries for any metric
- Build a Grafana dashboard that tells a story about system health
- Set up alerting that's actually useful (not noisy)
- Debug a production issue using metrics and logs together
- Define SLOs for a service and measure compliance
