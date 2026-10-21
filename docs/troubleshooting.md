# Troubleshooting notes

Use this repeatable workflow when a service or network feature stops working.

1. **Define the symptom.** Record what failed, when it began, and which clients are affected.
2. **Scope the issue.** Determine whether it affects one application, one device, or the whole network.
3. **Check service health.** Inspect container status, service status, and recent logs.
4. **Check connectivity.** Verify the host, port mapping, routing, and DNS resolution separately.
5. **Review recent changes.** Identify configuration or update changes that may explain the symptom.
6. **Make one change at a time.** Keep a note of the expected result and how to roll back.
7. **Verify and document.** Test the original symptom and note the actual outcome.

When publishing a case study, include the observed symptoms, investigation steps, the confirmed cause if known, the fix, and validation. Do not claim a root cause or resolution unless it was actually confirmed.

Before sharing logs, redact IP addresses where appropriate, hostnames, usernames, query history, tokens, and other sensitive data.
