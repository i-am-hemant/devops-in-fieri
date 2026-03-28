# 09 - Ansible

## Why Ansible
Terraform provisions infrastructure. Ansible configures it. Different tools for different jobs. Ansible is agentless (just SSH), uses YAML, and has a massive module library.

## What to Learn

### Fundamentals (Week 1)
- [ ] Architecture — control node, managed nodes, agentless via SSH
- [ ] Inventory — static, dynamic (AWS EC2 plugin), groups, group vars, host vars
- [ ] Ad-hoc commands — `ansible all -m ping`, `ansible web -m shell -a "uptime"`
- [ ] Playbooks — YAML structure, plays, tasks, handlers
- [ ] Modules — `apt`, `yum`, `copy`, `template`, `file`, `service`, `user`, `command`, `shell`, `lineinfile`
- [ ] Variables — precedence (22 levels!), facts, registered variables
- [ ] Conditionals — `when`, `changed_when`, `failed_when`
- [ ] Loops — `loop`, `with_items`, `with_dict`
- [ ] Handlers — notify and trigger on changes
- [ ] Tags — run specific parts of playbooks

### Intermediate (Week 1)
- [ ] Roles — directory structure, Galaxy, writing reusable roles
- [ ] Templates — Jinja2 templating for config files
- [ ] Vault — encrypting secrets in playbooks
- [ ] Error handling — `block/rescue/always`, `ignore_errors`
- [ ] Delegation — `delegate_to`, running tasks on specific hosts
- [ ] Serial execution — rolling updates with `serial`
- [ ] Check mode — `--check` for dry runs

### Advanced (Week 2)
- [ ] Dynamic inventory — AWS, GCP plugins
- [ ] Custom modules — writing Python modules for Ansible
- [ ] Callback plugins — custom output formatting
- [ ] Ansible + Terraform integration — using Terraform outputs as Ansible inventory
- [ ] Performance — `forks`, `pipelining`, `mitogen` strategy
- [ ] Molecule — testing Ansible roles with Docker

## Hands-On Project

**Build a complete configuration management setup:**

1. Ansible project structure:
   ```
   inventory/
     production/
     staging/
   roles/
     common/        # Users, SSH, NTP, basic security
     webserver/     # Nginx installation and config
     appserver/     # Python app deployment
     database/      # Postgres setup and config
     monitoring/    # Node exporter, Promtail
   playbooks/
     site.yml       # Full infrastructure
     deploy.yml     # Application deployment only
     security.yml   # Security hardening only
   ```
2. Provision 3 EC2 instances with Terraform, configure with Ansible
3. Dynamic inventory from AWS
4. Vault-encrypted database passwords and API keys
5. Rolling deployment playbook — update app servers one at a time with health checks
6. Idempotent — running playbooks twice changes nothing
7. Molecule tests for each role

## Validation
You're done when you can:
- Write a role from scratch that configures any common service
- Debug "why isn't my task running" by understanding variable precedence
- Set up a complete server fleet configuration from zero
- Explain when to use Ansible vs Terraform vs a shell script
