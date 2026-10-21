# Network overview (sanitized)

This document intentionally avoids publishing the exact home network layout.

## Components

- Router: provides local network connectivity and DHCP
- Raspberry Pi: Linux host for DNS filtering and self-hosted services
- Pi-hole: DNS filtering for configured clients
- Unbound: local recursive DNS resolver used in the DNS design
- Docker: runs selected applications in containers
- Cloudflare Tunnel: used in the website hosting design; tunnel credentials and routing tokens must remain private

## Addressing

Use placeholders in public documentation:
- Router: `<ROUTER_LAN_IP>`
- Homelab host: `<HOMELAB_HOST_LAN_IP>`
- DNS service: `<DNS_SERVER_LAN_IP>`

Private RFC1918 addresses are not generally routable on the public internet, but they can still disclose details about a personal network. Publish only what is useful for explaining the design.

## Remote access

Do not publish tunnel tokens, origin credentials, private hostnames, access policies, or screenshots exposing administrative URLs. Describe the architecture at a high level instead.
