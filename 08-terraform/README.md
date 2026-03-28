# 08 - Terraform

## Why Terraform
Infrastructure as Code is non-negotiable. Terraform is the industry standard — multi-cloud, declarative, massive ecosystem. You'll use it daily.

## What to Learn

### Fundamentals (Week 1)
- [ ] HCL syntax — resources, data sources, variables, outputs, locals
- [ ] Provider configuration — AWS provider, versioning
- [ ] `terraform init`, `plan`, `apply`, `destroy` — the core workflow
- [ ] State — what it is, why it matters, `terraform.tfstate`
- [ ] Resource dependencies — implicit vs explicit (`depends_on`)
- [ ] Provisioners — why you should almost never use them (use Ansible instead)
- [ ] `terraform import` — bringing existing resources under management
- [ ] `terraform taint` / `terraform untaint` (replaced by `-replace` flag)

### State Management (Week 1)
- [ ] Remote state — S3 + DynamoDB backend
- [ ] State locking — why it matters for teams
- [ ] State file structure — understanding what's stored
- [ ] `terraform state` commands — `list`, `show`, `mv`, `rm`
- [ ] State environments — workspaces vs separate state files
- [ ] Sensitive data in state — why state must be encrypted

### Modules (Week 2)
- [ ] Writing modules — inputs, outputs, structure
- [ ] Module composition — calling modules from modules
- [ ] Module versioning — source from Git, Terraform Registry
- [ ] Public modules — when to use, when to write your own
- [ ] Module best practices — keep them small, single-purpose

### Advanced Patterns (Week 2)
- [ ] `for_each` vs `count` — when to use which
- [ ] Dynamic blocks
- [ ] `templatefile()` for generating configs
- [ ] Conditional resources with `count = var.enabled ? 1 : 0`
- [ ] `moved` blocks for refactoring without destroying resources
- [ ] Data sources — querying existing infrastructure
- [ ] `lifecycle` — `prevent_destroy`, `ignore_changes`, `create_before_destroy`

### Team & Production Patterns (Week 3)
- [ ] Directory structure for multi-environment setups
- [ ] Terragrunt — DRY Terraform for multiple environments (know it exists)
- [ ] CI/CD for Terraform — plan in PR, apply on merge
- [ ] Policy as code — Sentinel, OPA, `tflint`
- [ ] Cost estimation — `infracost` integration
- [ ] Drift detection
- [ ] Blast radius reduction — splitting state files by component

## Hands-On Project

**Rebuild your AWS project (section 07) entirely in Terraform:**

1. Module structure:
   ```
   modules/
     networking/    # VPC, subnets, IGW, NAT, route tables
     compute/       # ECS cluster, task definitions, services
     database/      # RDS, ElastiCache
     loadbalancer/  # ALB, target groups, listeners
     dns/           # Route 53, ACM
     monitoring/    # CloudWatch alarms, dashboards
   environments/
     dev/
     staging/
     prod/
   ```
2. Remote state in S3 with DynamoDB locking
3. Variables file per environment (different instance sizes, replica counts)
4. Outputs that give you all the URLs, endpoints, and connection strings
5. GHA pipeline: `terraform plan` on PR, `terraform apply` on merge to main
6. `infracost` comment on PRs showing cost impact
7. `tflint` and `terraform validate` in CI

## Validation
You're done when you can:
- Write Terraform for any AWS service from the docs alone
- Structure a multi-environment Terraform project for a team
- Debug state issues (state lock, drift, import) confidently
- Review someone else's Terraform PR and catch issues
- Tear down and rebuild entire infrastructure with one command
