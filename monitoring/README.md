# Homelab monitoring architecture

This homelab uses a small self-hosted monitoring stack to improve visibility into service availability and host health. The notes below describe the roles of the tools; exact deployment settings are intentionally not reproduced.

## Components

- **Uptime Kuma** — checks whether selected services are reachable and tracks availability.
- **Prometheus** — scrapes configured metrics endpoints and stores time-series data.
- **Node Exporter** — exposes host-level metrics such as CPU, memory, filesystem, and network statistics.
- **Grafana** — visualizes metrics from Prometheus in dashboards.

## Conceptual data flow

```text
Linux host metrics ---> Node Exporter ----+
                                          |
Application / service metrics ------------+--> Prometheus --> Grafana dashboards
                                          |
Service reachability checks -----------------> Uptime Kuma
```

The diagram is conceptual. Not every application necessarily exposes Prometheus metrics, and Uptime Kuma availability checks are distinct from metrics scraping.

## Operational checks

1. Confirm each container or service is running.
2. Check Prometheus targets and confirm expected targets are healthy.
3. Open Grafana and verify dashboards have recent data rather than empty panels.
4. Check Uptime Kuma monitor history and verify each check matches the intended service endpoint.
5. When a target fails, test name resolution, network reachability, port mapping, and the target process separately.
6. After changing configuration, validate the result and note how to roll back.

## Security considerations

- Keep Grafana, Prometheus, and exporter endpoints on trusted networks unless access is intentionally secured.
- Avoid exposing metrics endpoints directly to the public internet.
- Protect Grafana accounts and do not commit passwords or API tokens.
- Metrics and dashboards can reveal hostnames, internal addresses, installed services, and usage patterns. Redact screenshots before publishing them.
- Use explicit, least-privilege access for monitoring integrations.

## Portfolio evidence to add

As the monitoring setup evolves, add a redacted dashboard screenshot and a short explanation of:
- What is being monitored
- Which thresholds or alerts are useful and why
- How a failed check is investigated
- What changed after a real incident
