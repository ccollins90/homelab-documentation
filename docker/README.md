# Docker examples

The Compose file in this folder is an **illustrative template**, not a copy of the live server configuration. It demonstrates the structure of a small monitoring stack.

Before adapting it:
1. Review each image and pin a version suitable for your environment.
2. Set up persistent storage and backups.
3. Confirm port availability on the host.
4. Use firewall rules and authentication appropriate to your network.
5. Do not expose management interfaces directly to the public internet.
6. Keep credentials out of Compose files and source control.
