# 01 - Linux & Bash Scripting

## Why This First
Everything in DevOps runs on Linux. Every server you'll SSH into, every container's base image, every CI runner — it's Linux. Bash is the glue that holds it all together.

## What to Learn

### Linux Fundamentals (Week 1)
- [ ] Filesystem hierarchy (`/etc`, `/var`, `/opt`, `/tmp`, `/proc`, `/sys`)
- [ ] Users, groups, permissions (`chmod`, `chown`, `umask`, sticky bit, SUID/SGID)
- [ ] Package management (`apt`, `yum`/`dnf`, `brew`)
- [ ] Systemd — services, units, journalctl, timers
- [ ] File descriptors, stdin/stdout/stderr, redirection (`>`, `>>`, `2>&1`, `|`)
- [ ] Cron jobs and scheduling
- [ ] Disk management — `df`, `du`, `lsblk`, `mount`, `fdisk`, LVM basics
- [ ] SSH — key generation, config file, agent forwarding, tunneling

### Bash Scripting (Week 2)
- [ ] Variables, arrays, associative arrays
- [ ] Conditionals (`if`, `case`, `[[ ]]` vs `[ ]`)
- [ ] Loops (`for`, `while`, `until`, `select`)
- [ ] Functions and return values
- [ ] String manipulation (parameter expansion: `${var%pattern}`, `${var#pattern}`, `${var/old/new}`)
- [ ] Exit codes and error handling (`set -euo pipefail`, `trap`)
- [ ] Here documents and here strings
- [ ] Process substitution (`<()`, `>()`)
- [ ] Signal handling

### Essential CLI Tools (Week 3)
- [ ] Text processing — `grep`, `sed`, `awk`, `cut`, `sort`, `uniq`, `tr`, `xargs`
- [ ] Process monitoring — `ps`, `top`/`htop`, `kill`, `nice`, `nohup`, `bg`, `fg`, `jobs`
- [ ] Performance — `vmstat`, `iostat`, `sar`, `free`, `uptime`, load averages
- [ ] Networking — `curl`, `wget`, `netstat`/`ss`, `dig`, `nslookup`, `traceroute`, `tcpdump`, `nc`
- [ ] File tools — `find`, `locate`, `tar`, `gzip`, `rsync`
- [ ] Vim — enough to edit configs on a remote server (`:w`, `:q`, `i`, `dd`, `/search`, `:%s/old/new/g`)

## Hands-On Project

**Build a server provisioning script** that:
1. Takes a fresh Ubuntu VM (use Multipass or a cloud free tier instance)
2. Creates a non-root user with SSH key auth (disables password login)
3. Installs and configures: Nginx, fail2ban, UFW firewall
4. Sets up log rotation
5. Configures unattended security updates
6. Hardens SSH config
7. Sets up a cron job for daily health checks (disk, memory, zombie processes)
8. Outputs a summary report
9. Is idempotent — running it twice doesn't break anything

The script should use proper error handling, logging, and be shellcheck-clean.

## How to Practice
- Spin up a VM with Multipass (`multipass launch --name devbox`) or Vagrant
- Do everything from the terminal — no GUI
- Break things intentionally and fix them
- Read man pages instead of Stack Overflow first

## Validation
You're done when you can:
- SSH into a fresh Linux box and confidently configure it for production use
- Write a 200+ line bash script that's clean, handles errors, and is idempotent
- Troubleshoot a process eating CPU/memory using only CLI tools
- Parse and transform log files with awk/sed one-liners
