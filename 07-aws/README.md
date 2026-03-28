# 07 - AWS

## Why AWS First
AWS has ~32% market share. Learn it deeply, then other clouds map over easily. Don't spread thin across three providers.

## What to Learn

### IAM & Security (Week 1)
- [ ] IAM users, groups, roles, policies
- [ ] Policy documents — JSON structure, Effect/Action/Resource
- [ ] Principle of least privilege — how to actually do it
- [ ] IAM roles for services (EC2 instance profiles, Lambda execution roles)
- [ ] STS — AssumeRole, temporary credentials
- [ ] AWS Organizations and SCPs
- [ ] MFA enforcement

### Networking — VPC (Week 1)
- [ ] VPC — what it is, CIDR planning
- [ ] Subnets — public vs private
- [ ] Internet Gateway vs NAT Gateway
- [ ] Route tables — how traffic flows
- [ ] Security Groups vs NACLs — stateful vs stateless
- [ ] VPC Peering and Transit Gateway
- [ ] VPC Endpoints (Gateway and Interface) — access S3/DynamoDB without internet
- [ ] Flow Logs — debugging network issues

### Compute (Week 2)
- [ ] EC2 — instance types, AMIs, user data, metadata service
- [ ] Auto Scaling Groups — launch templates, scaling policies, health checks
- [ ] ECS — tasks, services, Fargate vs EC2 launch type
- [ ] Lambda — triggers, layers, concurrency, cold starts, timeouts
- [ ] Elastic Beanstalk — know it exists, when to use it (almost never)

### Storage & Databases (Week 2)
- [ ] S3 — buckets, policies, lifecycle rules, versioning, encryption, presigned URLs
- [ ] EBS — volume types (gp3, io2, st1), snapshots
- [ ] EFS — when to use it (shared filesystem across instances)
- [ ] RDS — MySQL/Postgres, Multi-AZ, read replicas, backups
- [ ] DynamoDB — basics, when to use NoSQL
- [ ] ElastiCache — Redis on AWS

### Load Balancing & DNS (Week 3)
- [ ] ALB — Application Load Balancer (L7), target groups, path-based routing
- [ ] NLB — Network Load Balancer (L4), when to use it
- [ ] Route 53 — hosted zones, record types, routing policies (weighted, latency, failover)
- [ ] CloudFront — CDN, origins, cache behaviors, invalidation
- [ ] ACM — free SSL certificates

### Other Essential Services (Week 3-4)
- [ ] SQS — message queues, dead letter queues
- [ ] SNS — notifications, pub/sub
- [ ] CloudWatch — metrics, alarms, logs, log insights
- [ ] Secrets Manager vs Parameter Store
- [ ] ECR — container registry
- [ ] EKS — managed Kubernetes (overview, deep dive in K8s section)
- [ ] CloudFormation — basics (you'll use Terraform, but know CF exists)

### Cost Management (Week 4)
- [ ] AWS pricing models — on-demand, reserved, spot, savings plans
- [ ] Cost Explorer, Budgets, Cost Allocation Tags
- [ ] Right-sizing recommendations
- [ ] Free tier limits — know them to avoid surprises

## Hands-On Project

**Build a production-ready three-tier architecture:**

1. VPC with public and private subnets across 2 AZs
2. ALB in public subnets
3. ECS Fargate services in private subnets (your Docker app from section 06)
4. RDS Postgres (Multi-AZ) in private subnets
5. ElastiCache Redis in private subnets
6. S3 for static assets, served via CloudFront
7. Route 53 for DNS (use a cheap domain or free subdomain)
8. ACM for SSL
9. CloudWatch alarms for CPU, memory, 5xx errors
10. IAM roles with least privilege for every service
11. All built manually first via Console, then tear it down and rebuild with Terraform (section 08)

## Validation
You're done when you can:
- Whiteboard a VPC architecture with subnets, route tables, and security groups
- Debug "I can't reach my EC2 instance" in 5 minutes
- Explain the difference between Security Groups and NACLs with examples
- Estimate monthly cost for a given architecture
- Set up a complete production environment from scratch
