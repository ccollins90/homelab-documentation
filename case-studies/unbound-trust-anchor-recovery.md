# Case study: restoring Unbound DNSSEC trust-anchor operation

> This is a sanitized summary of a real maintenance task. Host-specific addresses, logs, and other private details are omitted.

## Symptom

DNS resolution through the local Pi-hole and Unbound setup was not working as expected. Investigation identified a problem involving Unbound's root trust anchor.

## Investigation and resolution

The resolver's trust-anchor state was refreshed using the system helper:

```bash
sudo unbound-helper root_trust_anchor_update
```

After the update, Unbound was restarted or rechecked as appropriate, and DNS resolution was tested again through the local resolver and the Pi-hole path.

## Validation

A good validation sequence for this class of issue is:

1. Confirm the trust-anchor update completed without errors.
2. Confirm Unbound is running and listening on its configured local endpoint.
3. Query Unbound directly to separate resolver health from Pi-hole filtering.
4. Query through Pi-hole to validate the full request path.
5. Check service logs for renewed DNSSEC or trust-anchor errors.

Only record the incident as resolved after these tests succeed. The exact commands for service status and DNS testing depend on the host's distribution and local configuration.

## Lessons learned

- A DNS failure can originate in the recursive resolver even when Pi-hole itself is running.
- Test each layer independently to narrow the fault domain.
- Use the distribution-provided helper where available rather than editing trust-anchor files blindly.
- Validate the full client-to-Pi-hole-to-Unbound path after a repair.
- Keep the incident notes focused on symptoms, evidence, corrective action, and validation.

## Security note

Do not attach raw logs or query histories to a public case study. Redact local addresses, client identifiers, and any credentials before sharing diagnostic output.
