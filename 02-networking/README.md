# 02 - Networking Fundamentals

## Why This Matters
Most DevOps debugging boils down to networking. "The service is down" usually means a packet isn't getting where it should. This is the #1 gap for most DevOps engineers.

## What to Learn

### TCP/IP & OSI Basics (Week 1)
- [ ] OSI model — know layers 3 (Network), 4 (Transport), 7 (Application) cold
- [ ] IP addressing — IPv4, IPv6, private ranges (10.x, 172.16.x, 192.168.x)
- [ ] Subnets and CIDR notation — calculate subnet ranges by hand (`/24` = 256 IPs, `/16` = 65536)
- [ ] TCP vs UDP — three-way handshake, connection states, when to use which
- [ ] Ports — well-known ports (22, 53, 80, 443, 3306, 5432, 6379, 8080)
- [ ] NAT — how private IPs talk to the internet, SNAT vs DNAT
- [ ] DHCP — how machines get their IPs

### DNS (Week 1)
- [ ] How DNS resolution works end-to-end (recursive resolver → root → TLD → authoritative)
- [ ] Record types — A, AAAA, CNAME, MX, NS, TXT, SRV, PTR
- [ ] TTL and caching
- [ ] Debugging with `dig` and `nslookup`
- [ ] Split-horizon DNS, private DNS zones
- [ ] DNS in Kubernetes (CoreDNS, service discovery)

### HTTP/HTTPS/SSL/TLS (Week 2)
- [ ] HTTP methods, status codes (know 200, 201, 301, 302, 400, 401, 403, 404, 500, 502, 503)
- [ ] Headers — `Host`, `Content-Type`, `Authorization`, `Cache-Control`, `X-Forwarded-For`
- [ ] TLS handshake — how HTTPS actually works
- [ ] Certificates — CA, CSR, self-signed, Let's Encrypt, certificate chains
- [ ] mTLS — mutual TLS, why it matters for service mesh
- [ ] SSH — how key exchange works, port forwarding (local, remote, dynamic/SOCKS)

### Firewalls & Network Security (Week 2)
- [ ] iptables/nftables — chains (INPUT, OUTPUT, FORWARD), rules, NAT table
- [ ] Security groups (cloud context) vs NACLs
- [ ] VPN basics — WireGuard, OpenVPN
- [ ] Network segmentation — DMZ, VPCs, subnets

## Hands-On Project

**Debug and fix a broken multi-tier network setup:**

Set up with Docker Compose:
1. Frontend (Nginx) in a "public" network
2. Backend (Python API) in a "private" network
3. Database (Postgres) in a "data" network
4. Frontend can reach backend, backend can reach DB, frontend CANNOT reach DB directly

Then:
- Configure iptables rules on the host
- Set up SSL with self-signed certs (then Let's Encrypt if you have a domain)
- Use `tcpdump` to capture and analyze traffic between tiers
- Simulate DNS failures and debug them
- Set up SSH tunneling to access the DB from your local machine through the backend

## Validation
You're done when you can:
- Look at a CIDR block and know the IP range instantly
- Debug "connection refused" vs "connection timed out" vs "name resolution failed" and know exactly where to look
- Set up TLS certificates from scratch
- Explain to someone exactly what happens between typing a URL and seeing a page
- Read a `tcpdump` output and understand what's happening
