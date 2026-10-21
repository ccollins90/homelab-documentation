# Homelab Documentation

A living portfolio documenting my Raspberry Pi-based homelab, DNS filtering, Docker services, monitoring, and self-hosted applications.

> **Safety note:** This repository contains documentation and example configurations only. It does not contain live credentials or a complete copy of my production setup. Hostnames, addresses, ports, and values shown as examples should be reviewed before adapting them.

## Areas covered

- Raspberry Pi and Linux administration
- Pi-hole DNS filtering and Unbound recursive DNS
- Docker-based services and persistent storage
- Monitoring with Uptime Kuma, Prometheus, Grafana, and Node Exporter
- Self-hosted applications and troubleshooting notes

## Repository layout

- `docker/` — illustrative Compose examples and container notes
- `pihole/` — DNS architecture and operational notes
- `docs/` — sanitized network overview and troubleshooting workflow
- `.env.example` — placeholder environment variable names, never real values

## Important limitations

This is a portfolio and learning document, not a promise that every example is production-ready. Validate images, versions, permissions, network settings, and security controls before using examples on a live system.

## Security checklist before every commit

- [ ] No passwords, API keys, tokens, private keys, cookies, or recovery codes
- [ ] No real `.env` files, database dumps, backups, or private certificates
- [ ] No public IP address, public DNS records, tunnel tokens, or sensitive hostnames
- [ ] No unredacted screenshots or logs
- [ ] No private network topology beyond what I intend to disclose
- [ ] Review `git diff` before committing
