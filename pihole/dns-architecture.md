# DNS architecture (sanitized)

## High-level flow

1. A configured client requests a domain lookup.
2. The client sends the DNS request to Pi-hole.
3. Pi-hole applies its filtering rules.
4. Permitted queries are forwarded to the configured upstream resolver.
5. The result is returned to the client and may be cached according to the resolver settings.

## Resolver notes

This homelab has used Unbound as a local recursive resolver, with Pi-hole configured to forward DNS queries to it. DNSSEC validation has also been enabled in the setup.

Exact resolver settings, interface bindings, and upstream behavior should be verified on the live host before publishing a more detailed diagram.

## Troubleshooting checklist

- Confirm the client is using the intended DNS server.
- Check that Pi-hole and the resolver services are running.
- Review relevant service logs and query results.
- Test local DNS resolution and upstream resolution separately.
- Change one setting at a time and record the outcome.

Do not include real client names, raw query logs, public IPs, or credentials in examples.
