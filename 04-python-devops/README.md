# 04 - Python Scripting for DevOps

## Why Python
Bash is great for glue. Python is great for everything else — API integrations, complex logic, data parsing, cloud SDKs. Every major cloud provider's SDK is Python-first.

## What to Learn

### Core Python for DevOps (Week 1)
- [ ] Data structures — lists, dicts, sets, tuples, defaultdict, Counter
- [ ] File I/O — reading/writing files, CSV, JSON, YAML (`pyyaml`)
- [ ] String formatting — f-strings, `format()`, template strings
- [ ] Error handling — try/except, custom exceptions, context managers (`with`)
- [ ] Regular expressions — `re` module
- [ ] `os` and `pathlib` — file system operations
- [ ] `subprocess` — running shell commands from Python (and when NOT to)
- [ ] `argparse` / `click` — building CLI tools
- [ ] `logging` module — proper logging instead of print statements

### DevOps-Specific Python (Week 2)
- [ ] `requests` / `httpx` — API calls (REST APIs, webhooks)
- [ ] `boto3` — AWS SDK (EC2, S3, Lambda, IAM operations)
- [ ] `paramiko` / `fabric` — SSH automation
- [ ] `jinja2` — templating (used by Ansible, K8s manifests, config generation)
- [ ] `docker` SDK — manage containers programmatically
- [ ] `kubernetes` client — interact with K8s API
- [ ] Working with INI, TOML, YAML, JSON config files

### Advanced Scripting (Week 3)
- [ ] Decorators — write retry decorators, timing decorators
- [ ] Generators — for processing large log files without loading into memory
- [ ] Async/await — `asyncio`, `aiohttp` for concurrent API calls
- [ ] Type hints — make scripts maintainable
- [ ] Packaging — `pyproject.toml`, making your scripts installable
- [ ] Testing — `pytest` basics, mocking external services

## Hands-On Project

**Build a multi-cloud resource auditor CLI tool:**
1. Connects to AWS (boto3) and reports: running EC2 instances, S3 buckets with public access, unused EBS volumes, IAM users without MFA
2. Outputs reports in JSON, CSV, and formatted table (use `rich` or `tabulate`)
3. Sends alerts to Slack/Discord webhook for critical findings
4. Has proper CLI interface with `click` (subcommands: `audit aws`, `audit security`, `report`)
5. Includes retry logic with exponential backoff for API calls
6. Has unit tests for core logic
7. Is packaged as an installable CLI tool
8. Includes a Dockerfile to run it

## Validation
You're done when you can:
- Write a 500+ line Python tool with proper structure (not a single script file)
- Interact with cloud APIs confidently
- Parse any config/log format thrown at you
- Build CLI tools that others on your team would actually use
