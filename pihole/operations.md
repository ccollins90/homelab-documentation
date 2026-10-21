# Pi-hole + Unbound: implementation notes

This page documents the design and operational lessons from the homelab. Sensitive host-specific values are intentionally omitted; verify current settings on the server before treating this as a complete runbook.

## Design

- **Pi-hole** provides DNS filtering for devices configured to use the homelab DNS service.
- **Unbound** runs as a local recursive resolver.
- Pi-hole forwards permitted queries to Unbound on a loopback listener using a local port.
- DNSSEC validation is enabled in the documented setup.
- Blocklists are combined to improve coverage. Larger lists can increase coverage but may also create false positives, so validate important services after list changes.

## Request flow

```text
Client device
    |
    v
Pi-hole filtering
    |
    v
Unbound recursive resolver
    |
    v
DNS response returns to client
```

This is a conceptual diagram. It intentionally excludes actual LAN addresses, hostnames, and client details.

## Operational checklist

### Verify service health

1. Check that Pi-hole FTL is running and listening for DNS requests on the intended interfaces.
2. Check that Unbound is running and listening on the local address and port configured for Pi-hole.
3. Test name resolution through Pi-hole.
4. Test Unbound separately when troubleshooting resolver failures.
5. Review relevant service logs, redacting client identifiers and query history before sharing excerpts.

### Diagnose a DNS failure

1. Determine whether the issue affects one client, one domain, or all clients.
2. Confirm the client is using the intended DNS server.
3. Check Pi-hole query results to see whether a request was blocked, forwarded, or failed.
4. Test the local Unbound resolver independently.
5. Check connectivity and DNSSEC-related errors before changing upstream settings.
6. Change one setting at a time, retest, and document the result.

### Manage blocklists safely

- Add or remove lists deliberately rather than changing many at once.
- Update gravity after list changes.
- Test frequently used websites and applications after changes.
- Use narrowly scoped allowlist entries only when evidence shows a legitimate false positive.
- Revisit allowlist entries periodically; avoid broad wildcards unless absolutely necessary.

## Security and privacy

- Do not commit raw query logs, client names, MAC addresses, or unredacted screenshots.
- Keep administrative credentials and environment files out of Git.
- Avoid publishing exact local addresses, interface details, or the full contents of live configuration files.
- Do not use a public DNS resolver as a permanent workaround without understanding the privacy, DNSSEC, and filtering implications.

## Evidence to add as the project evolves

For a useful portfolio case study, record a real issue with:
- Symptom and scope
- Diagnostic commands or dashboard observations (with sensitive output redacted)
- Confirmed root cause, if established
- The change made and why
- Validation steps and outcome
- Any rollback or follow-up action

Only describe a cause or fix as confirmed when it was actually verified.
